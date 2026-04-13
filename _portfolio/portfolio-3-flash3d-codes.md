---
title: "Caractérisation thermique Flash 3D — Pipeline d'estimation et codes MATLAB"
excerpt: "Développement d'un pipeline complet de mesure des propriétés thermiques : acquisition IR, traitement spectral, estimation paramétrique et diagnostic statistique.<br/><img src='/images/portfolio-flash3d-thumbnail.png' alt='Pipeline Flash 3D'>"
collection: portfolio
---

# Caractérisation thermique Flash 3D — Pipeline d'estimation et codes MATLAB

> **Compétences :** traitement du signal · problème inverse · estimation paramétrique · analyse statistique · gestion de données expérimentales · MATLAB  
> **Domaines d'application :** R&D matériaux · instrumentation · modélisation · plan d'expérience · incertitudes

---

## Contexte

La méthode Flash 3D permet de mesurer les diffusivités thermiques planes d'un matériau à partir d'un flash laser et d'une caméra infrarouge. Le principe : exciter thermiquement la surface, filmer la diffusion 2D en temps réel, puis résoudre un problème inverse pour remonter aux propriétés du matériau.

Dans le cadre de ma thèse, j'ai utilisé et adapté un ensemble de codes MATLAB couvrant l'intégralité de la chaîne — de la lecture des données brutes jusqu'à l'estimation des conductivités thermiques et le diagnostic de la qualité du résultat.

---

## Vue d'ensemble du pipeline

```
Fichier de configuration (infos.txt)
        │
        ▼
Lecture des trames IR (format PTW binaire)
        │
        ▼
Soustraction du fond thermique + compensation des dérives
        │
        ▼
Projection sur les harmoniques spatiales (Fourier-Cosinus)
        │
        ▼
Normalisation par l'harmonique de référence
        │
        ▼
Estimation des paramètres (τx, τy) par modèle linéaire
        │
        ▼
Calcul des diffusivités (ax, ay) et conductivités (λx, λy)
        │
        ▼
Diagnostic statistique et validation
```

Le pipeline est orchestré par un script principal (`sLinearModelEstimate.m`, ~600 lignes) qui s'appuie sur plusieurs modules spécialisés. Un système de cache (`data.tmp`) évite de recalculer les étapes intermédiaires lorsque les données n'ont pas changé.

---

## Lecture et prétraitement des données

Les données thermographiques sont stockées au format binaire PTW (propriétaire FLIR). La lecture repose sur deux fonctions complémentaires :

- **`LoadDataFileSetPTW`** charge un ensemble de trames en extrayant uniquement la zone d'intérêt demandée, ce qui limite la consommation mémoire.
- **`LoadDataFilePTW`** lit un fichier unitaire par accès direct (`fseek` + `fread`) en gérant les deux types de données (niveaux numériques uint16 ou températures float).

Le prétraitement comprend ensuite trois opérations :

1. **Fond thermique** — Moyenne temporelle des trames acquises avant le flash. Les trames aberrantes sont détectées par régression robuste (`robustfit`, seuil à 99 %) et exclues automatiquement.
2. **Compensation des dérives** — Une zone de pixels hors excitation sert de référence pour corriger les fluctuations temporelles de la caméra, harmonique par harmonique.
3. **Calibration** — Conversion optionnelle des niveaux numériques en températures via un fichier d'étalonnage.

---

## Projection spectrale et normalisation

Le champ de température est projeté sur une base de cosinus spatiaux (transformée de Fourier-Cosinus), ce qui réduit chaque image 2D à un jeu de coefficients scalaires — les harmoniques T̂(m,n,t).

La fonction `transformTemperatureField` implémente cette projection en mode vectorisé (séparation des composantes x et y) et supporte deux schémas d'intégration : `'pixel'` pour les données expérimentales (point au centre du pixel) et `'pt'` pour les données simulées (nœuds aux bords, pondération trapézoïdale).

L'étape clé est la **normalisation** : en divisant chaque harmonique par une harmonique de référence, on élimine les paramètres inaccessibles (énergie laser, pertes convectives, épaisseur, diffusivité transverse). Le rapport normalisé ne dépend plus que des deux paramètres plans recherchés, τx et τy.

---

## Estimation et diagnostic

L'estimation est réalisée par `LinearModelEstimate` via une minimisation par moindres carrés pondérés. Le modèle est structuré autour de quatre structures MATLAB (`unknownParams`, `procParams`, `dataParams`, `optParams`) qui séparent clairement les paramètres à estimer, la configuration physique, les données et les options algorithmiques.

**Sorties principales :**
- Diffusivités thermiques ax, ay (avec incertitudes)
- Conductivités thermiques λx, λy (à partir de la capacité calorifique et de la densité)
- Métriques de qualité : χ² réduit, R², R² ajusté, corrélation, fraction des résidus expliqués

Le module de diagnostic (`LinearModelDiagnostic`) génère les graphiques de résidus et permet l'export en PNG ou LaTeX. Une option d'estimation robuste avec pondération itérative des résidus est disponible pour traiter les données contenant des points aberrants.

---

## Calibration expérimentale

La fiabilité de la méthode a été établie sur trois métaux de référence, en identifiant les paramètres expérimentaux optimaux :

| Étude | Paramètre varié | Résultat clé |
|-------|-----------------|--------------|
| **Aluminium** | Puissance laser (30 → 90 %) | Erreur < 1 % à puissance maximale |
| **Cuivre** | Nombre de trames (200 → 1600) | Convergence à partir de ~1200 trames |
| **Argent** | Rapport signal/bruit (1 → 30) | Stabilisation dès S/B ≈ 5 |

Ces études ont conduit à retenir les conditions suivantes : puissance maximale, durée de pulse 10⁻³ s, épaisseur 0.5 mm, ≥ 1200 trames. Une campagne de 54 simulations numériques a confirmé des erreurs d'estimation inférieures à 2 % dans ces conditions.

---

## Compétences transférables

| Compétence technique | Application industrielle |
|---------------------|--------------------------|
| Pipeline de traitement reproductible (config, cache, traçabilité) | Workflows data, industrialisation d'outils d'analyse |
| Estimation paramétrique et problème inverse | Modélisation procédés, identification de lois de comportement |
| Analyse statistique (χ², résidus, estimation robuste) | Validation de modèles, plans d'expérience, incertitudes |
| Calibration multi-paramètres et analyse de sensibilité | Optimisation procédés, réduction d'itérations d'essais |
| Lecture/écriture de formats binaires, architecture modulaire | Développement d'outils, interfaçage instrumentation |

---

## Outils

`MATLAB` · `Format PTW (binaire IR)` · `Transformée de Fourier-Cosinus` · `Moindres carrés pondérés` · `Estimation robuste` · `Export LaTeX/PNG` · `Système de cache`

---

*Ce travail est détaillé dans le **Chapitre 2** de mon manuscrit de thèse. Voir aussi la [page dédiée à la thèse](/phd/) pour le contexte scientifique complet.*
