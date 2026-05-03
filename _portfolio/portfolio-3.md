---
title: "Microtraction de systèmes Ag nanoporeux / Cu : influence du vieillissement thermique et du frittage"
excerpt: "Ce projet de portfolio présente mon travail sur l'élaboration d'échantillons et la caractérisation mécanique de l'Ag nanoporeux et de bicouches Ag/Cu, en combinant des essais de traction, la corrélation d'images numériques et l'analyse de la rupture interfaciale afin d'étudier le rôle du vieillissement thermique et de la pression de frittage sur la fiabilité de l'assemblage.
Ce projet porte sur l'élaboration d'échantillons et la caractérisation mécanique de l'Ag nanoporeux et de bicouche Ag/Cu, afin d'évaluer l'effet du temps de vieillissement thermique et de la pression de frittage sur le comportement en micro-traction.<br/>
<img src='/anas-sghuri/images/SyntheseArgentNanoporeuxAgetAgCuTestsdeMicrotraction.png' 
     alt='Microtraction Ag/Cu' style='width:100%; margin-top:0.5em;'>"
collection: portfolio
---

<img src="{{ '/images/SyntheseArgentNanoporeuxAgetAgCuTestsdeMicrotraction.png' | relative_url }}" 
     alt="Résumé graphique — Microtraction Ag/Cu"
     style="display: block; width: 100%; max-width: 800px; height: auto; margin: 1.5em auto;">

- **Contexte :** travaux de thèse · Institut Pprime · Université de Poitiers
- **Outils :** MATLAB, Digital Image Correlation (DIC), machine de microtraction
- **Domaine :** caractérisation mécanique, science des matériaux, assemblage électronique

---

## 01. Contexte

Ce projet porte sur l'étude du comportement mécanique de systèmes à base d'argent nanoporeux, considérés soit seuls, soit en architecture bicouche Ag nanoporeux / Cu, à partir d'essais de microtraction couplés à la corrélation d'images numériques (DIC). L'objectif est d'établir les relations entre les paramètres de procédé, l'état microstructural et la réponse mécanique du matériau.

## 02. Problématique

L'enjeu est particulièrement important pour les systèmes bicouches, car le comportement observé résulte de l'interaction entre deux matériaux de nature très différente : une couche d'Ag nanoporeux, à comportement fragile, qui rompt précocement, et une couche de Cu, plus ductile, capable de poursuivre la déformation après la rupture de l'argent. La question scientifique centrale consiste donc à déterminer comment les conditions de mise en œuvre influencent la transmission de charge entre les couches, la stabilité de l'interface et la transition entre une rupture précoce de l'Ag et la poursuite de la déformation par le Cu.

## 03. Dispositif expérimental

L'étude a été menée sur deux types d'échantillons : de l'Ag seul (matériau poreux et très fragile) et des bicouches Ag/Cu. Les variables testées sont la pression de frittage (5 MPa et 10 MPa) ainsi que le vieillissement thermique à 350 °C pour différentes durées (0 h, 24 h, 50 h et 150 h).

Les essais de microtraction ont été couplés à une mesure de champs par Digital Image Correlation : la surface peinte des éprouvettes est suivie image par image afin de reconstruire les champs de déplacements puis de déformations en surface. Ces données cinématiques, synchronisées avec l'effort appliqué et traitées sous MATLAB, permettent d'interpréter la localisation de la déformation, la séquence de rupture et l'évolution de l'intégrité interfaciale dans le système Ag/Cu.

## 04. Résultats

Les résultats mettent en évidence un comportement mécanique en deux temps dans les bicouches. La couche d'Ag nanoporeux présente d'abord une réponse quasi élastique et rompt rapidement, tandis que la couche de Cu prend ensuite le relais par déformation plastique. Après la rupture initiale de l'Ag, la courbe contrainte–déformation présente souvent des *stress drops*, interprétés ici comme un indicateur qualitatif de désolidarisation ou de glissement interfacial entre la couche d'Ag déjà rompue et la couche de Cu encore en déformation.

Lorsque le temps de vieillissement augmente, les *stress drops* deviennent globalement moins fréquents et moins marqués, ce qui suggère une amélioration progressive des joints Ag/Cu. Au début du vieillissement, la rupture de l'Ag est souvent suivie d'un délaminage rapide. À l'inverse, pour les temps les plus longs (notamment à 150 h), la rupture du Cu tend plus souvent à se produire au même endroit que celle de l'Ag, indiquant que les deux couches restent solidaires jusqu'à la fin de l'essai.

L'augmentation de la pression de frittage de 5 MPa à 10 MPa semble également conduire à des échantillons plus résistants, cohérent avec un matériau mieux consolidé et une interface plus robuste. Cette tendance reste toutefois qualitative, car l'interprétation est limitée par la dispersion des résultats et la variabilité intrinsèque de la structure nanoporeuse. Enfin, le module de Young mesuré reste très dispersé (5 à 40 GPa), traduisant la forte sensibilité du comportement mécanique à la microstructure locale du réseau nanoporeux.

## 05. Bilan

Ce travail montre que le comportement mécanique des systèmes à base d'argent nanoporeux dépend fortement des conditions de procédé. Le vieillissement thermique renforce progressivement l'adhérence entre l'Ag et le Cu, limite les phénomènes de glissement interfacial et favorise une rupture plus coordonnée des deux couches. Une pression de frittage plus élevée semble améliorer la résistance globale. L'ensemble met en évidence le rôle central du couplage entre procédé, microstructure et interface dans la réponse en microtraction de ces architectures Ag nanoporeux / Cu.

### Compétences mobilisées

- Essais de microtraction sur matériaux fragiles (Ag nanoporeux)
- Corrélation d'images numériques (DIC) — champs de déformation
- Traitement et analyse de données sous MATLAB
- Caractérisation de la rupture interfaciale (délaminage, stress drops)
- Élaboration d'échantillons par frittage (SPS)
- Microscopie électronique à balayage (MEB)
- Analyse statistique de résultats expérimentaux dispersés

### Perspectives

L'étude ouvre des pistes vers une modélisation multi-couches du système Ag/Cu permettant de prédire l'évolution de la rigidité en fonction de l'état d'endommagement de l'interface. Une caractérisation à l'échelle locale (nano-indentation, tomographie X) permettrait de lever les ambiguïtés liées à la dispersion expérimentale et d'affiner la compréhension des mécanismes d'adhérence interfaciale au cours du vieillissement.
