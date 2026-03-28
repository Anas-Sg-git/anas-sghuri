---
title: ""
permalink: /phd/
layout: single
author_profile: true
---

# "Étude expérimentale de la conductivité thermique de l'argent fritté poreux : effet du vieillissement thermique et de l'interface avec un substrat de cuivre"

*Thèse de doctorat · Université de Poitiers · ENSMA · Institut P'*

> Sujet de thèse centré sur l’évaluation des performances thermiques de matériaux d’assemblage innovants pour l’électronique de puissance.
Travaux menés à l’interface entre expérimentation, modélisation et analyse de données, avec un enjeu fort de fiabilité et de compréhension du vieillissement des matériaux.

- Directeurs : Y. Billaud & X. Milhet
- Financement : ACI++ Pprime Eprom · UE FEDER
- Publication : Acta Materialia (2023)

<!--## Chiffres clés

| Valeur | Description |
|---|---|
| +84 % | Gain de conductivité thermique par frittage sous 10 MPa |
| 45 min | Cinétique de stabilisation de λ lors du vieillissement initial |
| 500 h | Durée maximale de vieillissement thermique étudié |
| ~50 % | Zone Ag affectée par l'interface à 500 h @ 350 °C |
| <6 % | Incertitude de mesure Flash 3D après calibration |-->

## 1. Contexte & enjeux

### Pourquoi s'intéresser à l'Ag fritté en électronique de puissance ?

Les composants en SiC et GaN de nouvelle génération, destinés à l’électronique de puissance, fonctionnent au-delà de 250 °C et doivent évacuer des densités de puissance croissantes. Dans ce contexte, les brasures classiques comme le SAC305 (50 W·m⁻¹·K⁻¹) ne permettent plus une dissipation thermique suffisante.

L'**Ag fritté** s'impose comme matériau d'interconnexion de nouvelle génération : conductivité théorique à 426 W·m⁻¹·K⁻¹, élaboration à basse température (200–300 °C), pas de fusion en service. Mais sa **microstructure poreuse complexe** génère une dispersion considérable dans les données publiées, et l'effet du vieillissement thermique sur ses propriétés demeurait insuffisamment documenté dans la littérature.

<img src="{{ '/images/module-puissance.png' | relative_url }}" alt="Module de puissance" style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">
>Architecture type d'un module de puissance et la microstructure de l'Ag fritté.
>L’interconnexion entre la puce en SiC/GaN et le substrat est un élément critique pour la dissipation thermique. Source : présentation de soutenance.

## 2. Verrou scientifique

Malgré l’intérêt croissant porté à l’Ag fritté comme matériau d’interconnexion, son comportement thermique reste difficile à décrire de manière robuste et prédictive. Cette difficulté tient à la fois à sa microstructure poreuse, à son évolution sous vieillissement thermique et au rôle des interfaces dans les assemblages réels. Trois verrous scientifiques principaux se dégagent :

 1. **Mesurer un matériau hautement diffusif.**
L’Ag fritté présente une conductivité thermique très élevée ; l’argent est en effet le métal le plus conducteur thermiquement à température ambiante. Cette forte diffusivité limite la validité des approches flash 1D. Une méthode capable de prendre en compte des effets 2D/3D ainsi qu’une anisotropie potentielle était donc nécessaire.
2. **Relier conductivité, densité et vieillissement.** La densité est un paramètre clé, mais on ne disposait pas encore d’une relation claire entre conductivité thermique, densité, temps et température de vieillissement.
3. **Quantifier l'effet de l'interface Ag/Cu.** Dans un assemblage réel, l'Ag repose sur un substrat Cu. Les résistances d'interface sont systématiquement négligées dans la littérature et leur évolution à long terme était totalement inconnue.

## 3. Approche expérimentale

### La méthode Flash 3D : un choix décisif

La méthode retenue repose sur une **excitation laser locale (CO₂, 130 W, 10 ms)** et une caméra infrarouge haute vitesse (2000 fps) qui enregistre la diffusion thermique 2D en surface. L’identification des conductivités thermiques repose sur la résolution d’un problème inverse fondé sur la solution analytique tridimensionnelle instationnaire de l’équation de la chaleur, projetée sur une base d’harmoniques spatiales.

Une **phase de calibration rigoureuse** sur des matériaux de référence (Al, Cu, Ag massif) a permis d'établir trois paramètres critiques : puissance laser maximale, nombre de trames ≥ 1200, rapport signal/bruit ≥ 5. Résultat : une erreur de mesure inférieure à 6 %.
 
<img src="{{ '/images/setup-flash3d.png' | relative_url }}" alt="Flash 3D: banc expérimental " style="display: block; width: 60%; max-width: 600px; height: auto; margin: 0 auto;">

*banc expérimental de la méthode Flash 3D : laser CO₂, caméra IR haute vitesse, cryothermostat.*

<img src="{{ '/images/principe-identification.png' | relative_url }}" alt="Flash 3D: principe identification " style="display: block; width: 90%; max-width: 600px; height: auto; margin: 0 auto;">

*Estimation des conductivités thermiques dans le plan à partir d’images infrarouges et de la résolution inverse de l’équation de la chaleur 3D instationnaire*

L’approche expérimentale repose également sur un **protocole complet d’élaboration des échantillons**. Celui-ci comprend un dépôt multicouche de pâte d’argent, un **dégazage sous vide primaire à température ambiante**, puis un **frittage sous pression à 270 °C pendant 5 min**, suivi d’un refroidissement libre. Ce protocole a été conçu pour obtenir des échantillons massifs et bicouches à densité contrôlée, en faisant varier la pression appliquée au frittage.

<img src="{{ '/images/frittage-process.png' | relative_url }}" alt="Procédé de frittage " style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">

*Procédé d'élaboration : dépôt multicouche, dégazage sous vide et frittage 0–10 MPa @ 270 °C pendant 5 min.*

La **température de frittage** a été déterminée par **analyse calorimétrique différentielle à balayage (DSC)** couplée à une **analyse thermogravimétrique (ATG)**. Les essais ont été réalisés sur la plage **25–300 °C** avec une vitesse de chauffe de **10 °C/min**. La DSC met en évidence un premier pic vers **125 °C**, attribué au dégazage des solvants, puis un second vers **257 °C**, associé au frittage des particules d’Ag. L’ATG montre en parallèle une perte de masse importante à partir de **100 °C** jusqu’à environ **210 °C**, puis une diminution plus lente attribuée à la décomposition du liant et du dispersant.

Les **observations MEB** ont servi à suivre l’évolution microstructurale de la pâte avec la température. Elles montrent que la microstructure initiale est globalement conservée jusqu’à **250 °C**, puis que les particules d’Ag commencent à coalescer au-delà. Ces observations ont conduit à retenir un **frittage à 270 °C pendant 5 min** comme compromis entre élimination du dispersant et compaction des particules.

<img src="{{ '/images/ATG-DSC-MEB.png' | relative_url }}" alt="ATG-DSC-MEB" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">

* **Analyses DSC/ATG et évolution microstructurale de la pâte d’argent en fonction de la température.**  
À gauche, les courbes DSC/ATG mettent en évidence le dégazage des solvants puis le frittage des particules d’Ag. À droite, les micrographies MEB montrent la conservation de la microstructure initiale jusqu’à **250 °C**, suivie de la coalescence des particules à plus haute température.*

Après élaboration, plusieurs techniques de **métrologie dimensionnelle** ont été utilisées pour déterminer la **densité apparente** des échantillons. La masse a été mesurée par balance, les dimensions latérales par **profilomètre optique**, et l’épaisseur par **comparateur mécanique digital**. La densité a ensuite été calculée par le rapport classique **masse/volume**.

La **porosité primaire** a été mesurée par **imagerie MEB** après une préparation métallographique minutieuse des échantillons. Cette préparation repose sur des **polissages successifs** avec papiers abrasifs de granulométrie **400, 800, 1200, 2000 et 4000** afin d’obtenir une surface miroir révélant clairement les pores et les grains. Les images MEB acquises à **5000×** ont ensuite été traitées sous **ImageJ et Matlab** par binarisation et seuillage pour quantifier la fraction surfacique de porosité.

<img src="{{ '/images/porosite-MEB.png' | relative_url }}" alt="Évaluation de la porosité par traitement d’images MEB" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">

*Traitement d’image pour l’évaluation de la porosité : image MEB brute, seuillage, puis binarisation pour quantifier la fraction surfacique des pores.*

La **taille des grains** d’Ag a été évaluée à partir d’images acquises par microscopie électronique à balayage à émission de champ **MEB-FEG** à un grossissement de **30 000×**. Les contours des grains ont d’abord été tracés, puis les images binarisées et traitées sous **ImageJ** à l’aide de l’outil de mesure de particules, en excluant les pores et les grains en bord d’image. L’aire de chaque grain a ensuite été mesurée et convertie en **diamètre équivalent**, en assimilant les grains à des disques. Il a ainsi été possible d’établir une distribution des tailles de grains, décrite par une moyenne et un écart-type.

<img src="{{ '/images/taille-grains.png' | relative_url }}" alt="Détermination de la taille des grains métallurgiques par traitement d’images MEB-FEG" style="display: block; width: 60%; max-width: 600px; height: auto; margin: 0 auto;">

***Traitement d’image mis en œuvre pour l’évaluation de la taille des grains :** image brute, tracé des joints, préparation de l’image pour l’analyse, puis identification individuelle des grains sous **ImageJ**.*

La **capacité calorifique** a été déterminée afin de compléter la caractérisation thermophysique des échantillons et de convertir les mesures de **diffusivité thermique** en **conductivité thermique**. Les essais ont été réalisés par **mDSC** entre **−25 °C et 300 °C** à **10 °C/min**. Grâce à la modulation du signal thermique, cette méthode permet d’accéder plus finement à la réponse réversible du matériau et donc à sa capacité calorifique.

**Deux familles d’échantillons :** plaques d’Ag fritté seul (**5 × 5 cm**, **0,5–1,4 mm**) pour isoler le comportement intrinsèque du matériau, puis bicouches **Ag/Cu** (**Ag : 0,12–0,46 mm** + **Cu : 0,1 mm**) pour intégrer l’effet d’interface. Le frittage a été réalisé sous des pressions comprises entre **0 et 10 MPa**. Les essais de vieillissement ont ensuite été conduits dans un **four horizontal Pyrox** sous **vide primaire**, afin de limiter les effets d’**oxydation parasite** tout en restant proches des **conditions rencontrées en service**. Trois températures ont été retenues **150, 250 et 350 °C** pour explorer des sollicitations thermiques croissantes, depuis des conditions modérées jusqu’aux températures visées pour les composants de nouvelle génération. Les durées de vieillissement (**50, 200 et 500 h**) permettent enfin de suivre l’évolution des assemblages à **court, moyen et long terme**.

## 4. Résultats : Ag fritté seul

### Densité → conductivité : une corrélation robuste

La pression de frittage est le levier principal : passer de 0 à 10 MPa augmente la densité de **62 %** et la conductivité thermique de **84 %**. Les mesures s'alignent sur les prédictions des modèles à pores sphériques et cylindriques d'Ordonez-Miranda (2016).

<img src="{{ '/images/ag-non-vieilli.png' | relative_url }}" alt="Conductivité thermique mesurée en fonction de la porosité relative" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">

*Conductivité thermique mesurée en fonction de la porosité relative, pour 4 pressions de frittage. Comparaison avec les modèles de pore sphérique, cylindrique et plat.*

### Vieillissement : un saut initial rapide, puis stabilisation

Le vieillissement thermique révèle une dynamique en deux temps. Dans les **premières 45 minutes** — et non les premières 50 heures comme suggéré dans la littérature — la conductivité fait un saut significatif, particulièrement marqué pour les échantillons fortement densifiés (10 MPa). La **densité, elle, reste parfaitement stable** jusqu'à 500 h à 350 °C.

<img src="{{ '/images/ag-cinetique.png' | relative_url }}" alt="saut initial rapide" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">

*Évolution de λ pour 0–10 MPa, 150–350 °C, jusqu'à 500 h.*

<img src="{{ '/images/ag-vieillissement.png' | relative_url }}" alt="Barplot λ vs temps de vieillissement" style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">

*Cinétique fine — λ atteint son maximum en ≈ 45 min. La taille des grains (≈300 nm) reste inchangée.*

> **Interprétation clé :** l'augmentation initiale de λ n'est pas liée à une densification (ρ =
> constante) ni à une croissance de grains (stable à ≈ 300 nm). Elle est attribuée à la **relaxation
> de contraintes résiduelles de compression** générées lors du frittage sous pression — un mécanisme
> mis en évidence via des mesures de résonance dynamique (X. Milhet et al., 2015) et corroboré par des
> études indépendantes (Zuo et al., 2022 ; Agyakwa, 2024).

## 5. Résultats : bicouches Ag/Cu

### L'interface change tout à long terme

Les bicouches Ag/Cu présentent d'abord le même comportement que l'Ag seul : une hausse de λ dans les 50 premières heures. Puis, **au-delà de 200 h**, une dégradation progressive et significative apparaît — absente dans les échantillons monocouches. La densité globale, elle, reste stable.

> **Placeholder image — Slide 55 ou 56**
> Barplot λ Ag/Cu — comparaison 0h / 50h / 200h / 500h pour les 4 pressions, avec tendance Ag seul superposée
> /assets/images/phd/agcu-vieillissement.png

*Évolution de la conductivité effective des bicouches Ag/Cu au cours du vieillissement @ 350 °C. La tendance en pointillés représente l'Ag fritté seul (pas de dégradation).*

L'analyse microstructurale par MEB révèle une **zone d'interface Ag/Cu à porosité inhomogène** dont l'épaisseur et la microstructure évoluent avec le temps de vieillissement. Aucune nouvelle phase (oxyde, alliage AgₓCuᵧ) n'est détectée par EDS — la dégradation est exclusivement d'origine microstructurale locale.

#### Quantification de la zone affectée

**Résultat clé — modèle en couches**

Un modèle de contribution en couches (Cu + interface + zone Ag affectée + Ag sain) permet d'estimer l'épaisseur de la zone Ag dégradée. À 500 h @ 350 °C, environ **50 % de la couche d'Ag** est affectée par le vieillissement.

**À retenir :** ~50 % de l'Ag affecté à 500 h

#### Divergence à temps long

**Résultat clé — limite du modèle**

Le modèle prédit correctement λ jusqu'à 200 h. Au-delà, une **divergence croissante** apparaît, indiquant des phénomènes non capturés : redistribution de porosité en 3D, défauts aux joints de grains, évolution de l'adhésion Ag/Cu.

**À retenir :** Modèle valide jusqu'à 200 h

## 6. Publications & perspectives

### Contributions et ouvertures

- **Acta Materialia · 2023** — **A. Sghuri**, Y. Billaud, X. Milhet et al. — *Thermal conductivity of porous sintered silver: effect of density and thermal aging.* — Article principal, résultats Ag monocouche.

- **Conférence SFT · 2021** — **A. Sghuri**, Y. Billaud, X. Milhet — Calibration de la méthode Flash 3D pour matériaux hautement conducteurs (Al, Cu, Ag).

Les perspectives identifiées ouvrent plusieurs directions à fort intérêt industriel : extension aux systèmes **Cu/Ag/Cu et SiC/Ag**, cyclage thermique en conditions représentatives, modélisation 3D de la microstructure incluant défauts aux joints de grains et évolution de l'adhésion interfaciale.

### Compétences développées

`Mesure thermique Flash 3D`, `Méthode inverse (ENH)`, `Microscopie MEB + analyse d'images`, `mDSC / calorimétrie modulée`, `Frittage Ag sous pression`, `Vieillissement thermique accéléré`, `Python / traitement données`, `MATLAB / modélisation thermique`, `Rédaction scientifique (EN/FR)`
