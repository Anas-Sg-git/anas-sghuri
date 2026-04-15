---
title: "Simulation numérique de la conduction thermique 3D — Python & FlexPDE"
excerpt: "Implémentation d'un solveur pour l'équation de la chaleur 3D instationnaire dans un milieu anisotrope, excité par impulsion laser gaussienne — différences finies, schéma implicite, scipy sparse.<br/>
<img src='/anas-sghuri/images/portfolio-simu-excerpt.png' 
     alt='portfolio-simu-excerpt' style='width:70%; margin-top:0.5em;'>"
collection: portfolio
---

> Simulation de l'équation de la chaleur 3D instationnaire dans un échantillon d'argent soumis à un pulse laser gaussien — différences finies 3D, schéma implicite (Euler arrière), solveur creux scipy.

**Mots-clés** : Différences finies · Python · FlexPDE · Equation de la chaleur · Laser pulse · Schéma implicite · Scipy sparse · Argent

### Compétences transférables

| Compétence technique | Application industrielle |
|---|---|
| Discrétisation d'EDP par différences finies 3D | Simulation thermique, mécanique, diffusion |
| Schéma implicite (Euler arrière) + factorisation LU sparse | Solveurs robustes pour systèmes raides |
| Modélisation de conditions aux limites mixtes | Convection, flux imposé, couplage multi-physiques |
| Portage de codes de simulation vers Python | Reproductibilité, open-source, déploiement |
| Post-traitement et visualisation (champs 2D/3D, historiques) | Analyse de résultats, rapports automatisés |

---

## 01 — Contexte & Enjeu

La méthode Flash 3D repose sur la résolution numérique et analytique de l'équation de la chaleur 3D dans un milieu soumis à une excitation laser localisée. Avant d'appliquer l'estimateur ENH à des mesures expérimentales, il est indispensable de **valider le modèle direct** par simulation numérique : on génère des données synthétiques dont on connaît les propriétés exactes, puis on vérifie que la méthode d'estimation les retrouve.

L'outil de référence utilisé au laboratoire est **FlexPDE®**, un solveur éléments finis multiphysiques. Ses points forts sont son maillage adaptatif spatial et temporel — indispensable pour capturer les forts gradients générés par le pulse laser — et sa robustesse pour les phénomènes à dynamiques multiples.

Ce projet documente le code de simulation utilisé pour les simulations de référence de la thèse, et son **implémentation Python** (numpy / scipy / matplotlib) pour les études paramétriques.

---

## 02 — Le problème physique

### Equation de la chaleur 3D anisotrope

L'échantillon est un parallélépipède d'argent (50 × 50 × 10 mm). Le problème physique s'écrit :

```
ρ·C · ∂T/∂t + div(Q) = 0

avec  Q = (-kₓ·∂T/∂x, -kᵧ·∂T/∂y, -k_z·∂T/∂z)
```

**Conditions aux limites :**
- Faces latérales : isolées (flux nul)
- Face inférieure (z = 0) : convection — `-k_z·∂T/∂z = h·(T - T∞)`
- Face supérieure (z = L_z) : convection + flux laser — `-k_z·∂T/∂z = -φ(x,y,t) + h·(T - T∞)`

**Condition initiale :** T(x,y,z,0) = Tᵢ = 25 °C

![Schéma 3D de l'échantillon d'argent avec conditions aux limites](https://anas-sg-git.github.io/anas-sghuri/images/portfolio-simu-geometrie.png)
*Géométrie du problème : parallélépipède 50×50×10 mm. Face supérieure (orange) soumise à la convection et au flux laser localisé. Face inférieure (bleu) soumise à la convection seule. Faces latérales isolées (flux nul).*

### Excitation laser gaussienne

L'excitation est le produit d'une gaussienne spatiale et d'une gaussienne temporelle, centrées au milieu de l'échantillon :

```
φ(x, y, t) = P_laser · f_x(x) · f_y(y) · g(t)

avec  f_x(x) = 1/(σₓ√2π) · exp(-(x - μₓ)²/2σₓ²)
      g(t)   = 1/(σₜ√2π) · exp(-(t - μₜ)²/2σₜ²)
```

Le choix d'une gaussienne temporelle plutôt qu'un créneau permet d'éviter les discontinuités qui feraient diverger le schéma numérique.

![Distribution spatiale et profil temporel de l'excitation laser gaussienne](https://anas-sg-git.github.io/anas-sghuri/images/portfolio-simu-laser.png)
*Excitation laser φ(x,y,t) = P_laser · f_x(x) · f_y(y) · g(t). Gauche : distribution spatiale gaussienne centrée sur la face supérieure (σ_x = σ_y = l/6). Droite : profil temporel gaussien du pulse (durée 10 ms, μ_t = 5 ms).*

### Propriétés de l'argent (Ag)

| Paramètre | Valeur |
|---|---|
| Masse volumique ρ | 10 500 kg·m⁻³ |
| Capacité thermique Cp | 236 J·kg⁻¹·K⁻¹ |
| Diffusivité thermique α | 1,73 × 10⁻⁴ m²·s⁻¹ |
| Conductivité thermique k | 429 W·m⁻¹·K⁻¹ |

L'argent est le métal pur ayant la conductivité thermique la plus élevée. Cette propriété génère une dynamique thermique **extrêmement rapide**, qui impose des contraintes sévères sur le schéma numérique.

---

## 03 — Le code FlexPDE original

FlexPDE permet d'exprimer le problème directement en notation mathématique. La syntaxe est déclarative : on décrit l'équation, les variables, la géométrie et les conditions aux limites — le solveur gère automatiquement la discrétisation et le maillage adaptatif.

```
VARIABLES
    Temp    { Température }

EQUATIONS
    Temp: rho*Cp*dt(Temp) + Div(Q) = 0

BOUNDARIES
    SURFACE 'Top'    NATURAL(Temp) = -Heat_Flux + h*(Temp - Tinf)
    SURFACE 'Bottom' NATURAL(Temp) =              h*(Temp - Tinf)

TIME 0 to sim_time by d_time
```

**Points forts de FlexPDE dans ce contexte :**
- Maillage adaptatif en espace ET en temps — s'affine automatiquement là où les gradients sont forts (impact laser, front thermique).
- Gestion native des géométries 3D par extrusion.
- Export des champs de température vers MATLAB ou Tecplot.



---

## 04 — Implémentation Python : méthode et architecture

### Choix de la méthode numérique

Le schéma explicite est écarté d'emblée : avec α = 1,73 × 10⁻⁴ m²·s⁻¹, le critère de stabilité impose :

```
dt_max ≤ 1 / [2α · (1/dx² + 1/dy² + 1/dz²)] ≈ 4 ms
```

Le pas de temps expérimental est de 10 ms — soit 2,5 fois plus grand que la limite de stabilité. Le **schéma implicite (Euler arrière)** est donc adopté : inconditionnellement stable, il supporte n'importe quel pas de temps.

### Architecture du solveur

```
Grille de discrétisation (25×25×6 noeuds = 3 750 inconnues)
            │
            ▼
Construction de la matrice creuse A (scipy.sparse.csr_matrix)
│  → terme temporel : ρCp/dt sur la diagonale
│  → laplacien : différences finies décentrées
│  → conditions aux limites : termes de convection intégrés
            │
            ▼
Factorisation LU unique (scipy.sparse.linalg.splu)
            │
            ▼
Boucle temporelle :  pour chaque pas de temps t_n
│   b = (ρCp/dt)·T_old  +  termes source (convection Tinf, flux laser)
│   T_new = LU.solve(b)      ← substitution avant/arrière seulement
            │
            ▼
Post-traitement : historiques, cartes 2D, profils, export CSV
```

La factorisation LU est calculée **une seule fois** (A ne change pas). À chaque pas de temps, seule une substitution est effectuée — ce qui rend la boucle temporelle très rapide malgré 3 750 inconnues.

![Structure creuse (spy plot) de la matrice de rigidité thermique A](https://anas-sg-git.github.io/anas-sghuri/images/portfolio-simu-matrice.png)
*Structure de la matrice creuse A (schéma implicite, grille 10×10×4). Chaque point représente un coefficient non nul. Les trois bandes diagonales correspondent aux couplages selon z (bande fine), y et x. La diagonale principale regroupe les termes temporels et les conditions aux limites.*

### Extrait du code — construction de la matrice creuse

```python
for i in range(NX):
    for j in range(NY):
        for k in range(NZ):
            n = idx(i, j, k)
            diag = rho * Cp / dt   # terme temporel

            if i == 0:             # face x=0 : convection
                diag += 2*kx/dx**2 + 2*h/dx
                add(n, idx(i+1,j,k), -2*kx/dx**2)
            else:                  # nœud intérieur
                diag += 2*kx/dx**2
                add(n, idx(i-1,j,k), -kx/dx**2)
                add(n, idx(i+1,j,k), -kx/dx**2)
            # ...idem Y et Z...

            if k == NZ-1:          # face z=LZ : convection + laser dans le RHS
                diag += 2*kz/dz**2 + 2*h/dz
                add(n, idx(i,j,k-1), -2*kz/dz**2)

A = sp.csr_matrix((vals, (rows, cols)), shape=(N, N))
solver = spla.splu(A)   # factorisation unique
```

### Flux laser — handle de fonction

Le flux laser est implémenté comme une **fonction appelée à chaque pas de temps** dans la construction du second membre, ce qui permet de gérer facilement des formes d'excitation complexes :

```python
def heat_flux(xi, yi, t):
    fx = 1/(sigma_x*sqrt(2*pi)) * exp(-(xi - mu_x)**2 / (2*sigma_x**2))
    fy = 1/(sigma_y*sqrt(2*pi)) * exp(-(yi - mu_y)**2 / (2*sigma_y**2))
    g  = 1/(sigma_t*sqrt(2*pi)) * exp(-(t  - mu_t )**2 / (2*sigma_t**2))
    return P_laser * fx * fy * g
```

---

## 05 — Résultats et validation

### Performances du solveur

| Paramètre | Valeur |
|---|---|
| Grille | 25 × 25 × 6 = 3 750 nœuds |
| Pas de temps | 10 ms |
| Nombre de pas | 51 (simulation 0 → 0,5 s) |
| Temps de résolution total | **0,2 s** (CPU standard) |
| Librairies requises | numpy, scipy, matplotlib uniquement |

### Résultats physiques

Le pulse laser (Q = 1 J, durée = 10 ms) chauffe le centre de la face supérieure jusqu'à **~37 °C** (température initiale 25 °C), puis l'échantillon se refroidit par convection pour revenir vers 25,6 °C à t = 0,5 s.

Les deux faces (supérieure et inférieure) atteignent quasi-instantanément la même température en régime établi, ce qui est physiquement cohérent avec la très haute conductivité de l'argent (k ≈ 429 W·m⁻¹·K⁻¹) — le matériau homogénéise la température dans son épaisseur beaucoup plus vite que la convection ne peut la dissiper en surface.

![Historiques de température au centre des faces supérieure et inférieure, et profil temporel du pulse laser](https://anas-sg-git.github.io/anas-sghuri/images/portfolio-simu-historiques.png)
*Gauche : évolution temporelle de la température au centre des faces supérieure (rouge) et inférieure (bleu). Le pulse laser (Q = 1 J, Δt = 10 ms) élève la face supérieure à ~37 °C, puis le refroidissement convectif ramène l'échantillon vers l'ambiante. La quasi-superposition des deux courbes traduit la très haute diffusivité de l'argent. Droite : profil temporel gaussien g(t) de l'excitation.*

**Livrables générés par le code :**

- Historique T(t) au centre des faces supérieure et inférieure
- Carte de température T(x,y) sur la face supérieure à t_final
- Coupe T(y,z) à x = LX/2
- Profil T(y) le long de la face supérieure
- Snapshots à 6 instants réguliers
- Export CSV des historiques

![Évolution du champ de température sur la face supérieure à 6 instants](https://anas-sg-git.github.io/anas-sghuri/images/portfolio-simu-snapshots.png)
*Cartes de température T(x,y) sur la face supérieure (z = L_z) à six instants régulièrement espacés entre t = 0 et t = 0,5 s. La tache chaude gaussienne centrée disparaît rapidement par diffusion latérale et refroidissement convectif — comportement cohérent avec α = 1,73×10⁻⁴ m²·s⁻¹.*

---

## 06 — Compétences mobilisées

- **Modélisation des EDP** — Formulation forte et faible de l'équation de la chaleur 3D, discrétisation par différences finies, gestion des conditions aux limites de type Neumann/Robin.
- **Algèbre linéaire creuse** — Construction de matrices sparses (format CSR), factorisation LU (splu), substitution forward/backward — gain de performance décisif pour les simulations répétées.
- **Analyse numérique** — Critère de stabilité CFL, choix du schéma implicite pour les problèmes raides, vérification de la convergence en maillage.
- **FlexPDE** — Formulation d'un problème EDP 3D instationnaire, maillage adaptatif, extrusion géométrique, export des données.
- **Python scientifique** — numpy, scipy.sparse, scipy.sparse.linalg, matplotlib (contourf, pdeplot-like), export CSV.
- **Validation numérique** — Comparaison des résultats avec les valeurs analytiques connues, étude paramétrique, documentation de la chaîne de calcul.

---

## Perspectives

Le solveur Python développé ici constitue la **brique de base** pour l'étude paramétrique numérique de la méthode Flash 3D. Il est directement interfaçable avec l'estimateur ENH pour générer des données synthétiques à la volée.

Les extensions envisagées sont : couplage avec l'estimateur ENH pour valider automatiquement la chaîne simulation → estimation, extension aux géométries bicouches (interface Ag/Cu), et intégration d'un maillage non uniforme pour raffiner localement au voisinage du pulse laser.

---

**Outils** : `Python` · `numpy` · `scipy.sparse` · `scipy.sparse.linalg (splu)` · `matplotlib` · `FlexPDE®` · `Différences finies 3D` · `Schéma implicite (Euler arrière)` · `Factorisation LU creuse`

*Ce travail s'inscrit dans le cadre de la **validation numérique du Chapitre 2** de mon manuscrit de thèse (méthode Flash 3D).*
