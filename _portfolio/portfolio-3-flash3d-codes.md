---
title: "Caractérisation thermique Flash 3D — Codes MATLAB & pipeline de données"
excerpt: "Développement d'un pipeline complet d'estimation des propriétés thermiques : acquisition IR, transformée de Fourier-Cosinus, inversion par modèle linéaire et diagnostic statistique.<br/><img src='/images/portfolio-flash3d-thumbnail.png' alt='Architecture du pipeline Flash 3D'>"
collection: portfolio
---

# Caractérisation thermique Flash 3D — Codes MATLAB & pipeline de données

> **Compétences mobilisées :** traitement du signal · problème inverse · estimation paramétrique · gestion de données expérimentales · analyse statistique · optimisation · MATLAB  
> **Mots-clés sectoriels :** R&D matériaux · instrumentation · méthode de mesure · modélisation · plan d'expérience · fiabilité · incertitudes

---

## Contexte

Dans le cadre de ma thèse, j'ai utilisé et adapté un ensemble de codes MATLAB pour estimer les propriétés thermiques (diffusivités, conductivités) de matériaux à partir de mesures par caméra infrarouge. La méthode Flash 3D repose sur une excitation laser impulsionnelle et l'analyse du champ de température transitoire en surface de l'échantillon.

Le défi principal : extraire des propriétés physiques fiables à partir de données bruitées, en maîtrisant chaque étape — de l'acquisition à l'estimation finale.

---

## Architecture du pipeline

Le pipeline de traitement se décompose en **6 modules fonctionnels** interconnectés :

| Étape | Module | Fonction |
|-------|--------|----------|
| **1. Configuration** | `infos.txt` + `LoadIniFile.m` | Paramétrage centralisé de l'expérience |
| **2. Lecture données** | `LoadDataFileSetPTW.m` | Chargement des trames IR (format PTW binaire) |
| **3. Fond thermique** | Bloc dans `sLinearModelEstimate.m` | Soustraction du fond + compensation des dérives |
| **4. Projection spectrale** | `transformTemperatureField.m` | Transformée de Fourier-Cosinus spatiale |
| **5. Estimation** | `LinearModelEstimate.m` | Inversion par moindres carrés pondérés |
| **6. Diagnostic** | `LinearModelDiagnostic.m` | Résidus, χ², R², distance de Cook |

**Flux de données :**
```
infos.txt → Lecture PTW → Soustraction fond → Transformée Fourier-Cosinus
   → Normalisation harmoniques → Estimation (τx, τy) → Diffusivités (ax, ay)
```

---

## 1. Lecture et gestion des données brutes

### Format PTW (propriétaire IR)

Les données thermographiques sont stockées au format binaire PTW (FLIR/Jenoptik). J'ai travaillé avec les fonctions de lecture bas niveau :

- **`LoadDataFileSetPTW.m`** — Chargement d'un ensemble de trames avec extraction d'une zone d'intérêt (ROI). Gère le mode `'full'` (image complète) et les sous-régions `[x1 y1 x2 y2]`.
- **`LoadDataFilePTW.m`** — Lecture unitaire d'un fichier PTW : parsing de l'en-tête binaire, positionnement par `fseek`, extraction par `fread` avec gestion des types (DL uint16 ou température float).

**Points techniques clés :**
- Lecture binaire optimisée avec `fread` en mode bloc (`width*format, skip`) pour extraire uniquement la ROI sans charger l'image complète
- Gestion transparente des deux formats de données (niveaux numériques DL et températures calibrées)
- Validation systématique de la cohérence des dimensions (assertions sur les ranges)

### Gestion du cache

Le script principal implémente un **système de cache intelligent** (`data.tmp`) qui vérifie si les fichiers d'entrée ont changé depuis le dernier calcul. Si les données sont inchangées, les résultats intermédiaires (harmoniques, moyennes du fond, etc.) sont rechargés directement — un gain de temps significatif lors des itérations de mise au point.

---

## 2. Traitement du fond thermique et compensation

### Soustraction du fond

Avant toute analyse, il faut isoler la réponse thermique de l'échantillon à l'excitation laser. Le traitement procède en **3 passes** :

1. **Moyenne temporelle du fond** — Calcul de la moyenne des trames de fond (`backgroundImages`) pour obtenir un fond thermique stable.
2. **Filtrage des trames aberrantes** — Analyse robuste (`robustfit`) de la moyenne temporelle. Les trames dont le résidu dépasse 2.576σ (seuil à 99 %) sont rejetées automatiquement.
3. **Soustraction spatiale** — Le fond moyen est soustrait de chaque trame pour obtenir les températures relatives.

### Compensation des dérives

La caméra IR présente des dérives temporelles qu'il faut corriger. Le script utilise une **zone de pixels de compensation** (`compensationPixels`) dont la température est supposée constante. Les variations observées sur cette zone sont retranchées des harmoniques — trame par trame et fréquence par fréquence.

### Calibration DL → Température

Lorsqu'un fichier de calibration est fourni, une loi d'étalonnage (interpolation) convertit les niveaux numériques (DL) en températures physiques.

---

## 3. Transformée de Fourier-Cosinus

### Principe

Le champ de température 2D est projeté sur une base d'harmoniques spatiales en cosinus :

$$\hat{T}(m,n,t) = \int_0^{l_x} \int_0^{l_y} T(x,y,t) \cdot \cos\left(\frac{m\pi x}{l_x}\right) \cdot \cos\left(\frac{n\pi y}{l_y}\right) \, dx \, dy$$

### Implémentation — `transformTemperatureField.m`

Cette fonction calcule la projection discrète du champ de température sur les harmoniques demandées. Elle supporte deux modes d'intégration numérique :

| Mode | Position des points | Pondération | Usage |
|------|---------------------|-------------|-------|
| `'pixel'` | Centre du pixel : `(i−0.5)/N` | Uniforme : `Δx = lx/N` | Données caméra IR |
| `'pt'` | Nœuds : `(i−1)/(N−1)` | Trapèzes : bords à `Δx/2` | Données simulées |

**Optimisation :** le calcul est vectorisé en séparant les composantes x et y (`baseX`, `baseY`), ce qui évite une double boucle sur les pixels et permet de traiter efficacement des matrices de grande taille.

### Normalisation par l'harmonique de référence

L'étape clé de la méthode : en divisant chaque harmonique par une harmonique de référence `(mref, nref)`, on élimine les paramètres inconnus du problème (énergie Q, pertes convectives h, épaisseur lz, diffusivité transverse az) :

$$R(m,n,t) = \frac{\hat{T}(m,n,t)}{\hat{T}(m_{\text{ref}}, n_{\text{ref}}, t)} \quad \xrightarrow{\text{modèle}} \quad f(\tau_x, \tau_y, C_{mn})$$

Le rapport normalisé ne dépend plus que des paramètres plans **τx** et **τy**, qui sont liés aux diffusivités par :

$$a_x = \tau_x \cdot \frac{l_x^2}{\pi^2}, \quad a_y = \tau_y \cdot \frac{l_y^2}{\pi^2}$$

---

## 4. Estimation par modèle linéaire

### Algorithme d'inversion — `LinearModelEstimate.m`

L'estimation des paramètres repose sur une **minimisation par moindres carrés pondérés**. Le modèle est linéaire en les coefficients `C_mn` (amplitudes des harmoniques) et non linéaire en `τx`, `τy` — mais la normalisation rend le problème globalement linéaire après reparamétrisation.

**Paramètres estimés :**
- `τx`, `τy` — taux de décroissance dans les directions x et y
- `C_mn` — amplitudes associées à chaque harmonique exploitée
- Incertitudes associées (écarts-types) via la matrice de covariance

**Options avancées :**
- Information a priori sur τ (régularisation bayésienne)
- Estimation robuste (pondération itérative des résidus, paramètre `robustH`)
- Diagnostic complet (χ², R², R² ajusté, corrélation, validRatio, distance de Cook)

### Structures de données

Le code s'organise autour de **4 structures MATLAB** qui encapsulent les différents aspects du problème :

| Structure | Contenu |
|-----------|---------|
| `unknownParams` | Paramètres à estimer (τ, C) et leurs a priori |
| `procParams` | Configuration du modèle (fréquences, temps, face excitée, σ) |
| `dataParams` | Données expérimentales (harmoniques, fond, compensation) |
| `optParams` | Options algorithmiques (robustesse, debug, affichage) |

---

## 5. Diagnostic et validation

### Métriques de qualité du fittage

| Métrique | Signification | Objectif |
|----------|---------------|----------|
| χ² réduit | Somme pondérée des résidus / (N − p) | ≈ 1 |
| R² | Coefficient de détermination | → 1 |
| R² ajusté | R² corrigé pour le nombre de paramètres | → 1 |
| Corrélation | Corrélation données/modèle (pondérée et non pondérée) | → 1 |
| validRatio | Fraction des résidus expliqués à 99 % | → 1 |
| Distance de Cook | Influence de chaque observation | Détection d'outliers |

### Diagnostic visuel — `LinearModelDiagnostic.m`

Génération automatique de graphiques :
- Résidus normalisés vs. prédictions
- Résidus vs. temps (par harmonique)
- Export PNG et/ou LaTeX

---

## 6. Visualisation des données brutes

Un script dédié permet de **visualiser rapidement les trames thermiques** : chargement via `LoadDataFileSet`, soustraction optionnelle du fond, affichage avec `imshow` en niveaux de gris. Des modules FFT2 et DCT2 sont disponibles pour l'analyse fréquentielle du champ.

---

## Calibration et optimisation expérimentale

La fiabilité des mesures a été établie par une **campagne systématique sur trois métaux de référence** (Al, Cu, Ag), en faisant varier les paramètres expérimentaux :

### Aluminium — Effet de la puissance laser

| Paramètre | Plage testée | Observation |
|-----------|-------------|-------------|
| Puissance laser | 30 % → 90 % | λ augmente avec P ; erreur relative < 1 % à P ≥ 80 % |
| Durée du pulse | 10⁻³ s (fixe) | Condition d'impulsionnalité respectée |

**Conclusion :** utiliser la puissance maximale pour maximiser le rapport signal/bruit.

### Cuivre — Effet du nombre de trames

| Paramètre | Plage testée | Observation |
|-----------|-------------|-------------|
| Nombre de trames | 200 → 1600 | Convergence à partir de ≈ 1200 trames |
| Référence Cu | 401 W·m⁻¹·K⁻¹ | Stabilisation autour de la valeur tabulée |

**Conclusion :** un nombre minimum de trames est nécessaire pour la convergence statistique.

### Argent — Rapport signal/bruit

| Paramètre | Plage testée | Observation |
|-----------|-------------|-------------|
| Rapport S/B | 1 → 30 | Stabilisation dès S/B ≈ 5 |
| Référence Ag | 429 W·m⁻¹·K⁻¹ | Mesures fiables à ± 6 % |

**Conclusion :** un rapport S/B ≥ 5 est suffisant pour des mesures précises.

### Validation numérique

54 simulations (3 énergies × 3 durées de pulse × 3 épaisseurs × 2 faces) ont confirmé que l'erreur d'estimation est inférieure à 2 % dans les conditions favorables (Δt_laser → 0).

---

## Compétences transférables

Ce travail illustre des compétences directement mobilisables en contexte industriel :

| Domaine | Compétence | Application industrielle |
|---------|------------|--------------------------|
| **Traitement du signal** | Transformée spectrale, filtrage, compensation de dérives | Instrumentation, capteurs, contrôle qualité |
| **Problème inverse** | Estimation paramétrique, moindres carrés pondérés, régularisation | Modélisation procédés, identification de paramètres |
| **Analyse statistique** | χ², R², résidus, distance de Cook, estimation robuste | Validation de modèles, plans d'expérience |
| **Gestion de données** | Pipeline reproductible, cache, traçabilité, fichier de configuration | Workflows data, reproductibilité, industrialisation |
| **Optimisation** | Calibration multi-paramètres, analyse de sensibilité | Optimisation procédés, réduction d'itérations |
| **Programmation** | MATLAB (600+ lignes), architecture modulaire, I/O binaire | Développement d'outils d'analyse, automatisation |

---

## Outils et technologies

`MATLAB` · `Traitement d'images IR` · `Format PTW (binaire)` · `Transformée de Fourier-Cosinus` · `Moindres carrés pondérés` · `Estimation robuste` · `Analyse de variance` · `Export LaTeX/PNG` · `Système de cache` · `Fichiers de configuration (INI)`

---

*Ce projet est détaillé dans le **Chapitre 2** de mon manuscrit de thèse. Pour une présentation complète de la méthode et des résultats, voir la [page dédiée à la thèse](/phd/).*
