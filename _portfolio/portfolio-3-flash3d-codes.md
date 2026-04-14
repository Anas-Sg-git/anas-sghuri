---
title: "Caractérisation thermique Flash 3D — Pipeline d'estimation et codes MATLAB"
excerpt: "Développement d'un pipeline complet de mesure des propriétés thermiques : acquisition IR, traitement spectral, estimation paramétrique et diagnostic statistique.<br/><img src='/images/portfolio-flash3d-thumbnail.png' alt='Pipeline Flash 3D'>"
collection: portfolio
---

> Développement et calibration d'une méthode de mesure de la conductivité thermique adaptée aux matériaux frittés fortement diffusifs et potentiellement anisotropes.

**Mots-clés** : Flash 3D · Conductivité thermique · Problème inverse · Caméra IR · Laser CO₂ · Argent fritté

### Compétences transférables

| Compétence technique | Application industrielle |
|---------------------|--------------------------|
| Pipeline de traitement reproductible (config, cache, traçabilité) | Workflows data, industrialisation d'outils d'analyse |
| Estimation paramétrique et problème inverse | Modélisation procédés, identification de lois de comportement |
| Analyse statistique (χ², résidus, estimation robuste) | Validation de modèles, plans d'expérience, incertitudes |
| Calibration multi-paramètres et analyse de sensibilité | Optimisation procédés, réduction d'itérations d'essais |
| Lecture/écriture de formats binaires, architecture modulaire | Développement d'outils, interfaçage instrumentation |

---

## 01 — Contexte & Enjeu

La méthode Flash classique (Parker, 1961) repose sur une excitation thermique uniforme et une mesure 1D en face arrière. Elle ne permet pas d'accéder aux propriétés thermiques dans le plan — et ses hypothèses deviennent insuffisantes dès que le matériau est très conducteur ou potentiellement anisotrope.

C'est le cas des matériaux d'argent frittés : leur **structure poreuse complexe** et leur **anisotropie thermique** probable (liée au procédé de frittage) exigent une approche capable de caractériser les propriétés dans les trois directions. L'argent possède la conductivité thermique la plus élevée parmi les métaux purs (~426 W·m⁻¹·K⁻¹), générant des dynamiques thermiques extrêmement rapides et difficiles à capturer.

**Approche retenue** : la méthode Flash 3D, combinant une excitation laser localisée et une caméra infrarouge matricielle, permettant l'estimation simultanée des diffusivités planes (a_x, a_y) par analyse des harmoniques spatiales.

![Banc expérimental Flash 3D](/images/portfolio-flash3d-banc.png)
*Banc expérimental de la méthode Flash 3D : laser CO₂, caméra IR haute vitesse (FLIR-SC7000, 2000 fps), échantillon et cryothermostat.*

---

## 02 — Modèle analytique & méthodologie

### Le modèle direct 3D

L'équation de la chaleur 3D en géométrie cartésienne pour un matériau orthotrope :

```
ρ·C · ∂T/∂t = λₓ · ∂²T/∂x² + λᵧ · ∂²T/∂y² + λ_z · ∂²T/∂z²
```

Le modèle repose sur un ensemble d'hypothèses qui permettent une résolution analytique complète :
- L'échantillon est une **plaque plane orthotrope** : le tenseur de diffusivité est diagonal, avec trois composantes indépendantes (a_x, a_y, a_z) alignées sur les axes du repère.
- Les propriétés thermiques sont supposées **constantes et uniformes**, ce qui impose de travailler avec de faibles élévations de température.
- Les **faces latérales sont isolées** (flux nul), les faces avant et arrière échangent par convection.
- L'excitation laser est un **flux surfacique localisé** φ(x,y,t) sur la face avant.

Grâce à ces conditions aux limites, le champ de température se décompose naturellement sur une **base de cosinus spatiaux** — les harmoniques T̂(m,n,t). Cette décomposition transforme un problème 3D instationnaire en un ensemble de **problèmes 1D indépendants selon z**, chacun résolu analytiquement. C'est ce qui rend la méthode à la fois rigoureuse et calculable en temps raisonnable.

![Modèle mathématique 3D](/images/portfolio-flash3d-modele.png)
*Modèle analytique 3D : équation de la chaleur avec conditions aux limites (isolation latérale, convection avant/arrière, excitation laser). La solution se décompose en trois termes : signature fréquentielle de l'excitation, solution du problème 1D dans l'épaisseur, et évanescence de chaque harmonique spatiale.*

### Estimateur ENH (Normalisation des Harmoniques)

L'observable est le logarithme du rapport entre une harmonique (m,n) et une harmonique de référence (p,q) :

```
Y_m,n(t) = ln|θ_m,n(t) / θ_p,q(t)| = C_m,n + [τₓ·(p²−m²) + τᵧ·(q²−n²)]·π²·t
```

Cette normalisation élimine d'un coup tous les paramètres inaccessibles — énergie laser Q, coefficient de pertes h, épaisseur l_z et diffusivité transverse a_z. Le problème inverse devient **linéaire**, permettant une résolution directe par moindres carrés pondérés.

L'harmonique **(2,2)** est choisie comme référence plutôt que (0,0) car elle possède un écart-type deux fois plus faible et une meilleure robustesse au bruit environnemental.

![Principe d'identification ENH](/images/portfolio-flash3d-identification.png)
*Principe d'identification des propriétés thermiques par l'estimateur ENH : les données expérimentales et le modèle analytique sont projetés en Fourier (espace) et Laplace (temps), puis comparés via la normalisation harmonique. La chaîne d'estimation conduit des temps caractéristiques τ aux diffusivités α puis aux conductivités λ.*

### Comportement des harmoniques

La compréhension du comportement des harmoniques guide directement les choix expérimentaux :
- Chaque harmonique décroît exponentiellement, avec un taux proportionnel aux diffusivités planes.
- Plus l'ordre (m,n) est élevé, plus la décroissance est rapide — les harmoniques d'ordre élevé disparaissent dans le bruit après quelques trames.
- La taille de la fenêtre d'exploitation est un compromis : trop grande, le signal se dilue dans le bruit ; trop petite, les conditions aux limites du modèle ne sont plus respectées.

### Dispositif et pipeline

Le banc repose sur un **laser CO₂** (excitation localisée), une **caméra IR FLIR-SC7000** (acquisition du champ de température), et un post-traitement sous **MATLAB** :

```
Excitation          Acquisition         Projection           Normalisation       Estimation
laser CO₂    →     champ T(x,y,t)  →   harmoniques θₘₙ  →  rapport θₘₙ/θ₂₂  →  τₓ, τᵧ → aₓ, aᵧ
(impulsion)         caméra IR           Fourier-Cosinus      suppression Q,ρC    régression linéaire
```

Le pipeline est orchestré par un script principal (`sLinearModelEstimate.m`) qui gère la lecture des trames IR (format binaire PTW), la soustraction du fond thermique avec rejet robuste des trames aberrantes, la compensation des dérives de la caméra, la projection spectrale, l'estimation et le diagnostic statistique (χ² réduit, R², résidus). Un système de cache évite de recalculer les étapes intermédiaires lorsque les données n'ont pas changé.

---

## 03 — Validation numérique

Une étude paramétrique complète a été menée avec **FlexPDE** (éléments finis, maillage adaptatif) sur un échantillon virtuel d'argent (a = 173×10⁻⁶ m²·s⁻¹).

| Paramètre | Valeurs testées |
|---|---|
| Épaisseur l_z | 1, 5, 10 mm |
| Énergie laser Q | 1, 10, 100 J |
| Durée d'impulsion Δt | 0.01, 0.1, 1 s |
| Face observée | Avant, Arrière |

**Total : 54 configurations simulées** (3 × 3 × 3 × 2)

| Indicateur | Résultat |
|---|---|
| Meilleure erreur relative | **< 1 %** (face arrière, Δt = 0.01 s) |
| Face privilégiée | **Face arrière** (systématiquement meilleure) |
| Robustesse au bruit | Erreur < 13 % pour σ = 0.1 °C |

**Enseignements** : l'excitation doit être la plus brève et intense possible ; la face arrière fournit des estimations plus robustes ; un compromis énergétique est nécessaire pour éviter de violer l'hypothèse de propriétés constantes (T_max < 100 °C).

---

## 04 — Validation expérimentale

Trois campagnes de mesures sur des échantillons de **50 × 50 × 0.5 mm** ont permis d'optimiser les paramètres et de valider la méthode contre les valeurs de la littérature. Chaque échantillon a été mesuré **20 fois** pour quantifier la reproductibilité.

| Matériau | λ référence (W·m⁻¹·K⁻¹) | Paramètre étudié | Conclusion clé |
|---|---|---|---|
| **Aluminium** (Al) | 239 | Intensité du laser | Puissance max + durée minimale nécessaire |
| **Cuivre** (Cu) | 399 | Nombre de trames | Stabilisation à partir de ~1200 trames |
| **Argent** (Ag) | 426 | Rapport signal/bruit | Stabilisation à S/N ≥ 5 |

**Protocole final retenu** : P = 100 %, Δt = 1 ms, observation face arrière.

![Calibration Al, Cu, Ag](/images/portfolio-flash3d-calibration.png)
*Résultats de calibration sur trois métaux de référence. Al : la conductivité et la précision augmentent avec la puissance laser. Cu : convergence vers la valeur de référence à partir de ~1200 trames. Ag : stabilisation dès un rapport signal/bruit de 5. Conclusions : λx ≈ λy (isotropie vérifiée), erreur globale ~6 %.*

---

## 05 — Compétences mobilisées

- **Modélisation analytique** — Résolution de l'équation de la chaleur 3D par transformées intégrales (Laplace + Fourier-Cosinus), solution semi-analytique exploitable en temps réel.
- **Problème inverse & estimation** — Estimateur ENH, choix de l'harmonique de référence (2,2), analyse de sensibilité, propagation des incertitudes.
- **Simulation numérique** — Design d'expérience par éléments finis (FlexPDE), étude paramétrique (54 configurations), maillage adaptatif.
- **Instrumentation & expérimentation** — Banc laser CO₂ + caméra IR, calibration, optimisation des paramètres d'acquisition, post-traitement MATLAB.
- **Traitement du signal** — Projection en base cosinus, filtrage par sélection d'harmoniques, analyse du rapport signal/bruit, régularisation du problème inverse.

---

## Perspectives

Ce travail a permis l'élaboration d'un protocole expérimental calibré pour la méthode Flash 3D, appliqué ensuite à la caractérisation d'échantillons d'**argent fritté** : étude des relations densité–conductivité thermique, effet du vieillissement, et influence de l'interface Ag/Cu sur les propriétés du système.

---

**Outils** : `MATLAB` · `FlexPDE` · `Format PTW (binaire IR)` · `Transformée de Fourier-Cosinus` · `Moindres carrés pondérés` · `Estimation robuste` · `Export LaTeX/PNG`

*Ce travail constitue le **Chapitre 2** de mon manuscrit de thèse. Voir la [page dédiée à la thèse](/phd/) pour le contexte scientifique complet.*
