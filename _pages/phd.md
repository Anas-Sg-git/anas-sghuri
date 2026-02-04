---
title: "PhD"
permalink: /phd/
layout: single
author_profile: true
---

## Présentation générale

Le manuscrit s’inscrit dans le champ de l’électronique de puissance, où la gestion thermique conditionne directement la fiabilité et les performances des modules. L’étude prend pour objet une famille de matériaux d’interconnexion à fort potentiel — les pâtes d’argent frittées — dont l’intérêt est évident du point de vue de la dissipation thermique, mais dont la réalité microstructurale (porosité, hétérogénéités, anisotropie possible) rend la caractérisation complexe et explique la dispersion des données disponibles. Dans ce contexte, le travail vise à établir une compréhension expérimentale solide de l’évolution de la conductivité thermique au cours d’un vieillissement thermique, en s’attachant à relier rigoureusement propriétés effectives et paramètres microstructuraux.

Le mémoire est structuré autour d’une introduction générale suivie de cinq chapitres constituant le cœur de l’étude, complétés par des annexes et une bibliographie conséquente. L’écriture est volontairement synthétique et lisible, avec un fil directeur clair : choisir une méthode de mesure adaptée à des matériaux fortement diffusifs, construire une méthodologie robuste, puis l’appliquer à des systèmes de complexité croissante — d’abord l’Ag fritté seul, ensuite des bicouches Ag/Cu afin d’intégrer l’effet d’interface.

---

## Introduction : positionnement du sujet et verrou scientifique

L’introduction replace la problématique dans le cadre des technologies de puissance et des contraintes associées à l’utilisation de matériaux tels que le SiC et le GaN. Elle justifie l’intérêt des interconnexions à base d’argent pour évacuer la chaleur, tout en soulignant que la question essentielle n’est pas seulement “quelle conductivité au départ ?”, mais “comment et pourquoi cette conductivité évolue ?”. Le vieillissement thermique est ainsi posé comme un enjeu de fiabilité, et la nécessité d’une caractérisation fiable des matériaux poreux très conducteurs apparaît comme le prérequis indispensable à toute discussion sérieuse des performances en conditions de service.

---

## Chapitre 1 — Contexte scientifique et bibliographique

Le premier chapitre propose une revue bibliographique structurée autour des technologies d’interconnexion, des matériaux et des compromis associés, avec un accent particulier sur l’argent fritté. Le procédé de frittage est discuté non seulement comme un moyen d’obtenir une liaison, mais comme un générateur de microstructures (porosité, connectivité, hétérogénéités) dont découlent les propriétés mécaniques et thermiques. Une place importante est donnée aux méthodes d’évaluation de la densité et de la porosité, en distinguant approches directes et indirectes, et en rappelant que la densité apparaît comme un levier majeur à la fois pour la tenue mécanique et pour la conduction thermique. Ce chapitre installe le décor : la littérature existe, mais les résultats sont dispersés, et l’effet du vieillissement sur la conduction thermique manque encore de bases expérimentales suffisamment robustes.

---

## Chapitre 2 — Mesure de la conductivité : justification et calibration d’une méthode Flash 3D

Le deuxième chapitre traite un point décisif : mesurer correctement la conductivité thermique de matériaux frittés qui peuvent présenter une anisotropie liée au procédé. Cette anisotropie potentielle impose une méthode capable de gérer des effets 2D/3D, au-delà des hypothèses 1D trop simplificatrices. La démarche retenue repose sur une méthode Flash 3D, choisie pour accéder à des propriétés macroscopiques à l’échelle millimétrique ou centimétrique, tout en conservant une capacité d’analyse compatible avec des transferts extrêmement rapides — situation typique de l’argent.

Le chapitre ne se contente pas de présenter l’outil : il en discute les origines, les avantages et les limitations, puis détaille une phase de calibration indispensable. L’approche est examinée théoriquement, puis éprouvée via un exercice numérique et une validation expérimentale sur des matériaux de référence proches, en termes de propriétés, des échantillons visés. Un point ressort nettement : la fiabilité des estimations dépend d’un réglage fin des paramètres expérimentaux, et l’étude débouche sur une méthodologie opérationnelle et reproductible pour estimer les paramètres thermiques des échantillons d’Ag fritté.

---

## Chapitre 3 — Échantillons, protocoles et construction d’une relation conductivité–densité–vieillissement

Le troisième chapitre a pour objectif d’établir une relation claire entre conductivité thermique, densité et vieillissement pour l’argent fritté, matériau clé pour le report de puces en électronique de puissance. La stratégie expérimentale est construite avec lucidité : l’étude commence par l’Ag seul, afin de s’affranchir de l’interface et des multiples couplages d’un assemblage réel, puis se prolonge vers des systèmes bicouches Ag/Cu, plus représentatifs et plus complexes. Deux familles d’échantillons sont donc préparées — Ag massif/Ag fritté d’un côté, bicouches Ag/Cu de l’autre — à partir d’un protocole établi puis adapté aux contraintes spécifiques de la pâte d’argent et aux dimensions retenues.

Le chapitre décrit également, avec un souci de rigueur métrologique, les méthodes employées pour quantifier densités et porosités, et les techniques retenues pour caractériser la taille de grains d’Ag et l’épaisseur des interfaces Ag/Cu. La microscopie électronique (MEB) et le traitement d’images sont mobilisés pour garantir l’intégrité des données ; une mesure calorimétrique (mDSC) est introduite afin de disposer d’éléments complémentaires utiles aux analyses ultérieures. Enfin, les essais de vieillissement thermique sont présentés comme un socle expérimental commun permettant d’évaluer l’effet du temps et de la température sur le matériau et sur l’assemblage.

---

## Chapitre 4 — Vieillissement de l’Ag fritté : évolution thermique et lecture microstructurale

Le quatrième chapitre se concentre sur l’évolution de la conductivité thermique des matériaux d’Ag frittés au cours du vieillissement, et sur sa mise en perspective avec les évolutions microstructurales, notamment porosité et taille de grains. L’analyse met en évidence un résultat fondamental : après frittage, la conductivité thermique de l’argent est étroitement corrélée à la densité. La densification, qu’elle soit obtenue par les conditions de mise en forme ou par la contrainte appliquée lors du frittage, se traduit par une augmentation significative de la conductivité.

Le vieillissement thermique révèle ensuite une dynamique marquée : une augmentation notable de la conductivité, particulièrement visible dans les étapes initiales, alors que les échantillons très poreux montrent une progression plus limitée. Cette observation conduit à une interprétation cohérente où la contrainte de frittage joue un rôle déterminant dans l’évolution initiale. La discussion ne s’arrête pas au constat : elle met en évidence que certains paramètres microstructuraux peuvent rester remarquablement stables sur la durée considérée, ce qui impose de discuter des mécanismes effectifs responsables des changements observés, au-delà d’une simple densification globale.

---

## Chapitre 5 — Bicouches Ag/Cu : interface, zones affectées et limites de la modélisation

Le dernier chapitre traite le cas des bicouches Ag/Cu et introduit naturellement la question d’interface, souvent centrale dans la tenue à long terme des interconnexions. Les premières tendances observées au début du vieillissement peuvent ressembler à celles de l’Ag seul ; toutefois, un comportement distinct apparaît ensuite : au-delà d’environ 200 heures, une détérioration de la conductivité thermique du système est constatée, alors même que la densité ne montre pas d’évolution notable. Ce résultat constitue un point important du manuscrit : il indique que des phénomènes localisés — et non une densification globale — pilotent l’évolution à temps long.

L’étude microstructurale met en évidence que le vieillissement affecte la zone d’interface Ag/Cu ainsi qu’une zone adjacente située au-dessus, et que cette évolution se traduit par une dégradation des performances thermiques effectives. Pour interpréter et quantifier cette influence, un modèle est proposé afin d’estimer l’épaisseur des zones et d’en déduire leurs conductivités thermiques, dans une logique de contribution en couches. Cette approche permet d’extraire des tendances et d’ordonner les phénomènes ; néanmoins, elle montre ses limites pour des temps de vieillissement longs, et appelle explicitement une modélisation plus complète. Les perspectives identifiées incluent notamment la prise en compte d’une microstructure réellement 3D, de l’adhésion Ag/Cu, de l’évolution des grains et des défauts aux joints de grains, afin d’expliquer durablement l’écart entre valeurs mesurées et valeurs estimées.

---

## Conclusion (message principal)

Au total, le manuscrit propose une démarche rigoureuse et progressive : sélectionner une méthode de mesure adaptée à des matériaux fortement diffusifs, l’adapter et la calibrer de manière convaincante, puis établir des corrélations expérimentales robustes entre conductivité thermique, densité et vieillissement pour l’Ag fritté, avant de démontrer, sur des bicouches Ag/Cu, l’importance déterminante de l’interface à temps long. La cohérence entre développements expérimentaux et éléments numériques, ainsi que la quantité de résultats mobilisés, rendent l’étude solide et utile pour la compréhension des performances thermiques des interconnexions en conditions de vieillissement.

---

## Documents

- Manuscrit de thèse (PDF) : `{{ site.baseurl }}/files/these.pdf`
- Rapport de lecture (PDF) : `{{ site.baseurl }}/files/rapport-richard.pdf`
