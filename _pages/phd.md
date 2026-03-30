---
layout: single
title: "Thèse de doctorat"
permalink: /phd/
author_profile: true
toc: true
toc_label: "Sommaire"
toc_icon: "flask"
toc_sticky: true
---

# Étude expérimentale de la conductivité thermique de l'argent fritté poreux : effet du vieillissement thermique et de l'interface avec un substrat de cuivre

*Université de Poitiers · ENSMA · Institut P' (Pprime, UPR CNRS 3346)*

> Sujet de thèse centré sur l'évaluation des performances thermiques de matériaux d'assemblage innovants pour l'électronique de puissance. Travaux menés à l'interface entre expérimentation, modélisation et analyse de données, avec un enjeu fort de fiabilité et de compréhension du vieillissement des matériaux.

- **Directeurs :** X. Milhet & Y. Billaud
- **Financement :** ACI++ Pprime Eprom · UE FEDER
- **Soutenance :** 11 mars 2024
- **Publication :** [Voir la partie publication](https://anas-sg-git.github.io/anas-sghuri/publications/)

---

**Contributions clés de cette thèse — de l'élaboration à la fiabilité :**

<div style="display: flex; flex-wrap: wrap; gap: 0.8em; margin: 1.5em 0; justify-content: center;">

  <div style="flex: 1; min-width: 150px; max-width: 180px; text-align: center; padding: 0.8em; border: 2px solid #1a5276; border-radius: 10px; background: #fafafa;">
    <div style="font-size: 1.1em; font-weight: bold; color: #1a5276; margin-bottom: 0.4em;">Élaboration</div>
    <div style="font-size: 0.82em; line-height: 1.4;">
      Procédé de frittage multicouche à paramètres variables · dégazage sous vide · 2 familles d'échantillons élaborées (Ag seul & Ag/Cu)
    </div>
  </div>

  <div style="flex: 1; min-width: 150px; max-width: 180px; text-align: center; padding: 0.8em; border: 2px solid #1a5276; border-radius: 10px; background: #fafafa;">
    <div style="font-size: 1.1em; font-weight: bold; color: #1a5276; margin-bottom: 0.4em;">Méthode & Caractérisation</div>
    <div style="font-size: 0.82em; line-height: 1.4;">
      Flash 3D + méthode inverse · MEB / MEB-FEG · DSC / ATG / mDSC · caractérisation thermique, microstructurale et dimensionnelle
    </div>
  </div>

  <div style="flex: 1; min-width: 150px; max-width: 180px; text-align: center; padding: 0.8em; border: 2px solid #1a5276; border-radius: 10px; background: #fafafa;">
    <div style="font-size: 1.1em; font-weight: bold; color: #1a5276; margin-bottom: 0.4em;">Relations structure–propriété</div>
    <div style="font-size: 0.82em; line-height: 1.4;">
      Conductivité variant d'un facteur 4 selon la porosité · lois reliant porosité, densité et conductivité établies
    </div>
  </div>

  <div style="flex: 1; min-width: 150px; max-width: 180px; text-align: center; padding: 0.8em; border: 2px solid #1a5276; border-radius: 10px; background: #fafafa;">
    <div style="font-size: 1.1em; font-weight: bold; color: #1a5276; margin-bottom: 0.4em;">Vieillissement</div>
    <div style="font-size: 0.82em; line-height: 1.4;">
      Première mise en évidence d'un saut initial de conductivité suivi d'une stabilisation · densité et taille de grains stables jusqu'à 500 h · mécanisme identifié : relaxation de contraintes résiduelles
    </div>
  </div>

  <div style="flex: 1; min-width: 150px; max-width: 180px; text-align: center; padding: 0.8em; border: 2px solid #1a5276; border-radius: 10px; background: #fafafa;">
    <div style="font-size: 1.1em; font-weight: bold; color: #1a5276; margin-bottom: 0.4em;">Interface & Fiabilité</div>
    <div style="font-size: 0.82em; line-height: 1.4;">
      ~50 % d'Ag affecté · divergence à 200 h · propriétés locales quantifiées par analyse microstructurale
    </div>
  </div>

</div>

---

## 1. Contexte & enjeux

### Pourquoi s'intéresser à l'Ag fritté en électronique de puissance ?

Les modules d'électronique de puissance reposent sur une chaîne de 
dissipation thermique dans laquelle l'interconnexion entre la puce et 
le substrat joue un rôle critique. Les composants SiC et GaN de nouvelle 
génération fonctionnent au-delà de **250 °C** et imposent des densités de 
puissance croissantes. Or les brasures classiques comme le SAC305 
(50 W·m⁻¹·K⁻¹, T° fusion 217 °C) ou l'Au-20Sn (57 W·m⁻¹·K⁻¹, 
T° fusion 278 °C) ne sont plus adaptées : leur température de fusion 
est trop proche des conditions de service, et leur conductivité thermique 
reste insuffisante.

L'**Ag fritté** s'impose comme matériau d'interconnexion de nouvelle génération : conductivité théorique à **426 W·m⁻¹·K⁻¹** (le métal le plus conducteur thermiquement), élaboration à basse température (**200–300 °C**), pas de fusion en service (T° fusion Ag : 961 °C). Mais sa **microstructure poreuse complexe** génère une dispersion considérable dans les données publiées (conductivité variant de **3 à 433 W·m⁻¹·K⁻¹** selon la littérature), et l'effet du vieillissement thermique sur ses propriétés demeurait insuffisamment documenté.

<img src="{{ '/images/module-puissance.png' | relative_url }}" alt="Module de puissance" style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">
*Architecture type d'un module de puissance et position critique de l'interconnexion dans la chaîne de dissipation thermique. Source : présentation de soutenance.*

---

## 2. Verrous scientifiques

Malgré l'intérêt croissant porté à l'Ag fritté, son comportement thermique reste difficile à décrire de manière robuste et prédictive. Trois verrous principaux structurent cette thèse :

### Mesurer un matériau hautement diffusif

L'Ag fritté présente une conductivité thermique très élevée ; l'argent est le métal le plus conducteur thermiquement à température ambiante. Cette forte diffusivité limite la validité des approches flash 1D classiques. Une méthode capable de prendre en compte des effets 2D/3D ainsi qu'une anisotropie potentielle était donc nécessaire.

### Relier conductivité, densité et vieillissement

La densité est un paramètre clé, mais on ne disposait pas d'une relation claire et robuste entre conductivité thermique, densité, temps et température de vieillissement. La mesure de la densité elle-même pose problème : l'analyse d'images MEB 2D peut biaiser les résultats, et la capacité thermique de l'Ag fritté est souvent supposée égale à celle de l'Ag massif (une hypothèse non vérifiée).

### Quantifier l'effet de l'interface Ag/Cu

Dans un assemblage réel, l'Ag repose sur un substrat Cu. Les résistances d'interface (R_Ag/Cu, R_Ag/SiC) sont systématiquement négligées dans la littérature et leur évolution à long terme était totalement inconnue. Pourtant, cette interface est susceptible de contrôler la fiabilité thermique du système complet.

---

## 3. Approche expérimentale

### 3.1. La méthode Flash 3D : un choix décisif

Le cœur de la démarche repose sur la **méthode Flash 3D**, adaptée à l'étude de matériaux hautement diffusifs comme l'argent. Le dispositif expérimental combine :

- une **excitation laser locale CO₂** (**130 W, 10 ms**) créant un point chaud sur la face avant de l'échantillon ;
- une **caméra infrarouge haute vitesse** (**jusqu'à 2000 fps**) enregistrant la diffusion thermique 2D en surface de l'échantillon ;

L'identification des conductivités thermiques repose sur la résolution d'un **problème inverse** fondé sur la solution analytique tridimensionnelle instationnaire de l'équation de la chaleur, projetée sur une base d'harmoniques spatiales (transformée de Fourier) et temporelles (transformée de Laplace). L'estimateur utilisé, dit **ENH** (Estimation par Normalisation Harmonique), permet d'extraire les temps de diffusion caractéristiques τ_x et τ_y, puis les diffusivités α_x et α_y, et enfin les conductivités λ_x et λ_y.

<img src="{{ '/images/setup-flash3d.png' | relative_url }}" alt="Flash 3D: banc expérimental " style="display: block; width: 60%; max-width: 600px; height: auto; margin: 0 auto;">
*Banc expérimental de la méthode Flash 3D : laser CO₂, caméra IR haute vitesse, cryothermostat.*

<img src="{{ '/images/principe-identification.png' | relative_url }}" alt="Flash 3D: principe identification " style="display: block; width: 90%; max-width: 600px; height: auto; margin: 0 auto;">
*Estimation des conductivités thermiques dans le plan à partir d'images infrarouges et de la résolution inverse de l'équation de la chaleur 3D instationnaire.*

### 3.2. Calibration et validation

Une **phase de calibration rigoureuse** sur des matériaux de référence (Al, Cu, Ag massif, pureté 99,95 %) a permis d'établir trois paramètres critiques d'acquisition :

| Paramètre | Critère retenu | Matériau de calibration |
|:---|:---|:---|
| Puissance laser | Maximale (100 %) | Al |
| Nombre de trames | ≥ 1200 | Cu |
| Rapport signal/bruit | ≥ 5 | Ag |

**Résultat :** une **erreur de mesure inférieure à 6 %**, avec confirmation de l'isotropie dans le plan (λ_x ≈ λ_y). La répétabilité a été validée par **20 mesures par échantillon**.

### 3.3. Élaboration des échantillons

#### Procédé de frittage

Le protocole d'élaboration comprend :

1. **Dépôt de pâte d'Ag** (nanoparticules, diamètre moyen 20–40 nm, 17 % de solvant) sur substrat Kapton (Ag seul) ou Cu (bicouches).
2. **Dégazage sous vide primaire** (14 mbar) à température ambiante — plateau de masse résiduelle (~85 %) atteint après ~30 min, confirmant l'élimination des solvants.
3. **Répétition** du cycle dépôt + dégazage selon l'épaisseur finale désirée.
4. **Frittage** à **270 °C pendant 5 min** sous pression de **0 à 10 MPa** (machine jusqu'à 100 kN).

<img src="{{ '/images/frittage-process.png' | relative_url }}" alt="Procédé de frittage " style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">
*Procédé d'élaboration : dépôt multicouche, dégazage sous vide et frittage 0–10 MPa @ 270 °C pendant 5 min.*

L'empilement des couches a été validé : la porosité est **homogène dans l'épaisseur**, comme confirmé par des analyses d'images MEB systématiques sur la tranche (taux de porosité surfacique constant ~10–12 % sur toute l'épaisseur pour un échantillon à 10 MPa).

#### Détermination de la température de frittage

La **température de frittage** a été déterminée par **DSC** couplée à l'**ATG** sur la plage **25–300 °C** à **10 °C/min** :

- **DSC** : premier pic vers **125 °C** (dégazage des solvants), second vers **257 °C** (frittage des particules).
- **ATG** : perte de masse de **~17 %** entre 100 et 210 °C, puis **~1 %** supplémentaire (décomposition du liant/dispersant).
- **MEB** : microstructure stable jusqu'à **250 °C**, puis coalescence des particules au-delà.

Ces résultats convergent vers le choix d'un frittage à **270 °C / 5 min** — compromis entre élimination du dispersant et compaction.

<img src="{{ '/images/ATG-DSC-MEB.png' | relative_url }}" alt="ATG-DSC-MEB" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">
*Analyses DSC/ATG et évolution microstructurale de la pâte d'Ag en fonction de la température.*

### 3.4. Caractérisation microstructurale et thermophysique

#### Mesure de densité

La densité apparente a été déterminée par le rapport **masse/volume** :

- Masse : **balance** (précision ~10 mg)
- Dimensions latérales : **profilomètre optique** (~1 µm)
- Épaisseur : **comparateur mécanique digital** (~1 µm)
- **Erreur sur la densité : ~2 %**

**Résultat** : la pression de frittage contrôle directement la densité — de ~3 g·cm⁻³ (0 MPa) à ~8 g·cm⁻³ (10 MPa).

#### Porosité par imagerie MEB

La porosité primaire a été mesurée par **imagerie MEB** après préparation métallographique (polissages successifs : papiers 400, 800, 1200, 2000, 4000 → surface miroir). Les images acquises à **5000×** ont été traitées sous **ImageJ et Matlab** par binarisation et seuillage pour quantifier la fraction surfacique de porosité.

<img src="{{ '/images/porosite-MEB.png' | relative_url }}" alt="Évaluation de la porosité par traitement d’images MEB" style="display: block; width: 80%; max-width: 600px; height: auto; margin: 0 auto;">
*Traitement d'image pour l'évaluation de la porosité : image MEB brute, seuillage, puis binarisation pour quantifier la fraction surfacique des pores.*

#### Taille des grains

La taille des grains a été évaluée par **MEB-FEG** à **30 000×**. Les contours des grains ont été tracés, les images binarisées, puis les aires mesurées sous **ImageJ** et converties en **diamètre équivalent** (assimilation à des disques).

**Résultat :** diamètre moyen **≈ 300 nm** (295–315 nm selon la pression), écart-type **≈ 100–124 nm**, stable jusqu'à 500 h @ 350 °C.

<img src="{{ '/images/taille-grains.png' | relative_url }}" alt="Détermination de la taille des grains métallurgiques par traitement d’images MEB-FEG" style="display: block; width: 60%; max-width: 600px; height: auto; margin: 0 auto;">
*Traitement d'image pour l'évaluation de la taille des grains : image brute, tracé des joints, identification individuelle sous ImageJ.*

#### Capacité calorifique

La capacité calorifique a été mesurée par **mDSC** (analyse calorimétrique différentielle à balayage en mode modulé) entre **−25 °C et 300 °C** à **10 °C/min**. Ce paramètre est essentiel pour convertir la diffusivité thermique en conductivité thermique (λ = α · ρ · c).

**Résultat clé :** la capacité thermique **diminue** à mesure que la densité **augmente** (de ~600 J·kg⁻¹·K⁻¹ à 0 MPa à ~286 J·kg⁻¹·K⁻¹ à 10 MPa ,**erreur : ~5 %**). Ce résultat contredit l'hypothèse courante de la littérature qui suppose c = c_Ag massif. La relation empirique établie est :

> **c(ρ) = 13,9·ρ² − 203·ρ + 1027** &nbsp;&nbsp;(R² = 0,99)

### 3.5. Échantillons étudiés et plan de vieillissement

**Deux familles d'échantillons :**

<table>
  <tr>
    <th></th>
    <th>Ag fritté seul</th>
    <th>Bicouches Ag/Cu</th>
  </tr>
  <tr>
    <td>Dimensions cm</td>
    <td colspan="2" style="text-align:center;">5 × 5</td>
  </tr>
  <tr>
    <td>Épaisseur Ag mm</td>
    <td>0,5 – 1,4</td>
    <td>0,12 – 0,46</td>
  </tr>
  <tr>
    <td>Épaisseur Cu mm</td>
    <td>—</td>
    <td>0,1</td>
  </tr>
  <tr>
    <td>Pressions de frittage MPa</td>
    <td colspan="2" style="text-align:center;">0 / 2 / 5 / 10</td>
  </tr>
  <tr>
    <td>Lots</td>
    <td>× 3</td>
    <td>× 1</td>
  </tr>
  <tr>
    <td>T° de vieillissement °C</td>
    <td>150 / 250 / 350</td>
    <td>350</td>
  </tr>
  <tr>
    <td>Durées de vieillissement h</td>
    <td colspan="2" style="text-align:center;">50 / 200 / 500</td>
  </tr>
</table>

**Vieillissement :** sous vide primaire (four Pyrox) pour limiter l'oxydation tout en restant proche des conditions de fonctionnement réelles.

---

## 4. Résultats : Ag fritté seul

### 4.1. Corrélation densité → conductivité thermique

La pression de frittage est le levier principal : passer de 0 à 10 MPa augmente la densité de **62 %** et la conductivité thermique de **84 %**. Sur une porosité relative de **~25–75 % (±2 %)**, la conductivité varie d'un **facteur ~4** (de **222 à 66 W·m⁻¹·K⁻¹**).

Les mesures s'alignent sur les prédictions des modèles à pores sphériques et cylindriques d'Ordonez-Miranda et al. (2016), fondés sur la théorie du milieu effectif différentiel :

> **λ_eff = λ₀ · (1 − p)ⁿ**

avec *n* dépendant de la forme des pores (3/2 pour sphérique, 5/3 pour cylindrique, ∞ pour plat).

La relation empirique conductivité–densité (avant vieillissement) est :

> **λ = 1,58·ρ² + 10,9·ρ + 20** &nbsp;&nbsp;(R² = 0,97)

<img src="{{ '/images/ag-non-vieilli.png' | relative_url }}" alt="Conductivité thermique mesurée en fonction de la porosité relative" style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">
*Conductivité thermique mesurée en fonction de la porosité relative, pour 4 pressions de frittage. Comparaison avec les modèles de pore sphérique, cylindrique et plat (Ordonez-Miranda et al., 2016).*

### 4.2. Effet du vieillissement thermique

Après avoir établi la relation entre porosité et conductivité à l'état 
initial, la question suivante est : comment ces propriétés évoluent-elles 
en service ? Pour y répondre, les échantillons d'Ag fritté ont été vieillis 
sous vide primaire à 150, 250 et 350 °C pendant des durées allant 
jusqu'à 500 h.

#### Vue d'ensemble : un saut initial suivi d'une stabilisation

La figure ci-dessous présente la conductivité thermique de l'ensemble 
des échantillons (0–10 MPa) aux trois températures de vieillissement. 
On observe une tendance commune : la majeure partie de l'augmentation 
de λ se produit entre 0 et 50 h de vieillissement. Au-delà, 
l'évolution devient faible et ne dépend ni de la pression de frittage 
ni de la densité initiale. Deux cas particuliers ressortent : le saut 
est d'autant plus marqué que la pression de frittage est élevée, et 
à 0 MPa l'évolution reste très limitée.

<img src="{{ '/images/ag-vieillissement.png' | relative_url }}" 
     alt="Évolution de la conductivité au vieillissement" 
     style="display: block; width: 100%; max-width: 700px; height: auto; margin: 0 auto;">

*Conductivité thermique de l'Ag fritté au cours du vieillissement 
(0, 50, 200 et 500 h) pour les quatre pressions de frittage, 
à 150, 250 et 350 °C.*

#### Zoom sur la cinétique : le saut se joue en quelques dizaines de minutes

Pour résoudre plus finement la cinétique de ce saut initial, un 
vieillissement par intervalles de 15 min a été réalisé sur un 
échantillon fritté à 10 MPa à 150 °C. Le résultat est remarquable : 
la conductivité atteint sa valeur maximale en **≈ 45 min**. 
Au-delà (ES2), elle se stabilise. Ce résultat montre que le saut 
observé entre 0 et 50 h sur la figure précédente ne dure en réalité 
que quelques dizaines de minutes.

<img src="{{ '/images/ag-cinetique.png' | relative_url }}" 
     alt="Cinétique à temps court du vieillissement" 
     style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">

*Cinétique à temps court : conductivité thermique de l'Ag fritté 
à 10 MPa, vieilli à 150 °C par intervalles de 15 min. La transition 
entre ES1 (saut rapide) et ES2 (stabilisation) intervient vers 45 min.*

#### Quels paramètres microstructuraux évoluent pendant le vieillissement ?

Pour comprendre l'origine de ce saut, trois paramètres ont été 
suivis au cours du vieillissement :

1. **La densité reste stable** jusqu'à 500 h à 350 °C, quelle que 
   soit la pression de frittage. L'évolution de λ n'est donc pas 
   liée à une densification globale.
2. **La taille des grains reste inchangée** (≈ 300 nm, mesurée par 
   MEB-FEG à 2 et 10 MPa, vieilli à 350 °C). Ce résultat est 
   corroboré par Zuo et al. (2022) et Agyakwa (2024).
3. **Après vieillissement**, les conductivités mesurées correspondent 
   aux prédictions pour des pores **sphériques et cylindriques**, 
   alors qu'avant vieillissement elles se situaient vers le modèle 
   à pores plats.

Ni la densification, ni la croissance de grains, ni l'évolution 
de la connectivité des pores ne peuvent expliquer un saut aussi 
rapide et aussi dépendant de la pression de frittage.

#### Interprétation : relaxation de contraintes résiduelles

Le seul paramètre qui distingue les échantillons entre eux est 
la **pression appliquée lors du frittage**. Milhet et al. (2015) 
ont montré par résonance dynamique que le frittage sous pression 
génère des contraintes résiduelles de compression dans le matériau, 
dont environ 10 % ne sont pas relâchées après frittage. Ces 
contraintes se relâchent lors du vieillissement, entraînant une 
augmentation du module d'Young vers sa valeur théorique. 
Par ailleurs, Lee et al. (2010) ont démontré que la conductivité 
thermique est fortement affectée par les contraintes et 
déformations mécaniques.

Ce mécanisme est cohérent avec l'ensemble des observations : 
pas de saut à 0 MPa (pas de contrainte résiduelle attendue), 
saut maximal à 10 MPa (contrainte résiduelle maximale), 
cinétique rapide indépendante de la température de vieillissement 
(une fois les contraintes relâchées, la valeur stabilisée ne 
dépend que de la porosité).

---

## 5. Résultats : bicouches Ag/Cu

### 5.1. L'interface change tout à long terme
La figure ci-dessous compare l'évolution de la conductivité 
thermique des bicouches Ag/Cu à celle de l'Ag fritté seul 
(représentée en pointillés), pour les quatre pressions de frittage, 
au cours du vieillissement à 350 °C.

<img src="{{ '/images/agcu-vieillissement.png' | relative_url }}" 
     alt="Évolution de la conductivité des bicouches Ag/Cu" 
     style="display: block; width: 100%; max-width: 700px; height: auto; margin: 0 auto;">

*Conductivité thermique des bicouches Ag/Cu au cours du 
vieillissement à 350 °C (0, 50, 200 et 500 h), pour les quatre 
pressions de frittage. La tendance en pointillés correspond au 
comportement attendu d'après les résultats de l'Ag fritté seul.*

Dans les 50 premières heures, les bicouches suivent la même 
tendance que l'Ag seul : une augmentation de la conductivité 
thermique. Mais **au-delà de 200 h**, un comportement différent 
apparaît : la conductivité diminue progressivement, alors qu'elle 
reste stable pour l'Ag seul. Cette dégradation est d'autant plus 
marquée que la pression de frittage est faible.

#### La densité globale ne change pas

Comme pour l'Ag seul, la densité des échantillons bicouches 
reste stable tout au long du vieillissement, jusqu'à 500 h à 
350 °C et pour toutes les pressions. La dégradation observée 
n'est donc pas liée à une évolution de la densité globale du 
système, mais à un phénomène qui n'existait pas dans les 
échantillons monocouches : **l'interface Ag/Cu**.

### 5.2. Mise en évidence de l'effet d'interface

Pour isoler le rôle de l'interface, la conductivité thermique des 
bicouches a été estimée à partir des propriétés de l'Ag fritté seul 
et du Cu, en utilisant une loi des mélanges en épaisseur — autrement 
dit, en supposant que l'interface n'a pas d'effet propre.

Jusqu'à 50 h de vieillissement, les estimations et les mesures 
concordent, avec des erreurs relatives inférieures à 6 %. Mais 
**au-delà de 200 h**, un écart croissant apparaît entre le modèle 
et l'expérience : jusqu'à **~36 %** à faible pression et **~18 %** 
à 10 MPa après 500 h. Ces écarts, bien supérieurs à l'incertitude 
de mesure, confirment qu'un **phénomène lié à l'interface** 
contribue à la dégradation de la conductivité thermique.

Pour comprendre ce phénomène, la microstructure de l'interface a 
été analysée par MEB sur des échantillons frittés à 10 MPa, 
découpés et vieillis à 0, 50, 200 et 500 h. L'observation révèle 
une alternance de **zones denses (LPA, ~55 %)** et **poreuses (HPA)**, 
ainsi qu'une **zone d'interface** dont la porosité évolue au cours 
du vieillissement. L'épaisseur de cette zone a été quantifiée par 
segmentation des images MEB binarisées, ligne par ligne.

Le suivi du taux de porosité en surface (TPS) montre deux 
dynamiques distinctes. À l'interface, le TPS chute de ~39 % 
à ~7 % après 50 h, traduisant une densification locale, puis 
se stabilise autour de ~20 %. En zone Ag, le TPS augmente 
progressivement de ~11 % à ~46 % après 500 h. Ces évolutions 
opposées expliquent pourquoi la densité globale reste constante 
alors que les propriétés locales se dégradent.

### 5.3. Quantification : quelle part de l'Ag est affectée ?

Pour traduire ces observations microstructurales en propriétés 
thermiques, une chaîne d'estimation a été construite à partir 
des corrélations établies sur l'Ag fritté seul : le TPS est 
d'abord converti en densité locale, puis la densité en 
conductivité thermique. Ce pipeline permet d'estimer séparément 
la conductivité de la zone Ag et celle de la zone d'interface 
à chaque étape de vieillissement.

Un modèle en couches — **Cu / interface / zone Ag affectée / 
Ag sain** — a ensuite été utilisé pour estimer l'épaisseur de 
la zone d'Ag effectivement dégradée. Jusqu'à 200 h, la totalité de la couche d'Ag conserve des 
propriétés proches de celles de l'Ag fritté seul. À 500 h, 
**environ 50 % de l'épaisseur de la couche d'Ag** présente des 
propriétés dégradées, avec une conductivité de la zone Ag 
passant de 271 à 71 W·m⁻¹·K⁻¹ entre 200 et 500 h.

Ce modèle reproduit correctement les mesures jusqu'à ~200 h. 
Au-delà, une divergence subsiste, suggérant des phénomènes 
non capturés par une description en couches 2D : redistribution 
de porosité en 3D, défauts aux joints de grains, évolution de 
l'adhésion Ag/Cu. Ces limites ouvrent directement sur les 
perspectives de la thèse.

---

## 6. Synthèse des contributions

Cette thèse couvre l'ensemble de la chaîne — de l'élaboration 
des échantillons à l'identification des mécanismes de dégradation 
— et apporte des contributions à chaque étape.

**Méthodologie**
- Adaptation et calibration de la méthode Flash 3D pour des matériaux hautement diffusifs, avec des critères d'acquisition explicites et une répétabilité validée sur trois matériaux de référence.
- Mise au point d'un procédé d'élaboration multicouche pour produire des échantillons d'Ag fritté seul et des bicouches Ag/Cu à densité variable.

**Relations structure–propriété**
- Loi reliant porosité et conductivité thermique établie sur toute la gamme étudiée, mettant en évidence une variation d'un facteur 4.
- Capacité thermique de l'Ag fritté mesurée par mDSC, révélant un écart significatif avec la valeur de l'Ag massif couramment utilisée dans la littérature.
- Corrélations empiriques construites pour relier densité, porosité et conductivité, permettant l'estimation des propriétés dans des configurations multicouches.

**Vieillissement thermique**
- Première mise en évidence, pour ce matériau, d'une cinétique en deux temps : saut initial de conductivité en quelques dizaines de minutes, suivi d'une stabilisation.
- Densité et taille des grains restant stables, le saut a été attribué à la relaxation de contraintes résiduelles de compression issues du frittage sous pression.

**Fiabilité des assemblages**
- Effet d'interface critique identifié à temps long dans les bicouches Ag/Cu, absent des échantillons monocouches.
- Quantification microstructurale montrant qu'à 500 h environ 50 % de la couche d'Ag est affectée, soulignant l'importance de l'interface dans la conception et la qualification des assemblages de puissance.

---

## 7. Publications & communications

**Experimental investigation of thermal conductivity during aging of nanoporous sintered silver**  
A. Sghuri, Y. Billaud, L. Signor, D. Saury, X. Milhet  
*[Acta Materialia](https://www.sciencedirect.com/journal/acta-materialia)*, 2023 — Impact Factor : 9.3 — [28](https://scholar.google.com/citations?user=qvDI3ZYAAAAJ&hl=fr) citations à ce jour 
 DOI : [10.1016/j.actamat.2023.119109](https://doi.org/10.1016/j.actamat.2023.119109)

[Voir la partie publication](https://anas-sg-git.github.io/anas-sghuri/publications/)

---

## 8. Perspectives

Les résultats ouvrent plusieurs directions à fort intérêt scientifique et industriel :

- Extension aux systèmes **Cu/Ag/Cu** et **SiC/Ag** (assemblages plus représentatifs).
- Essais en **cyclage thermique** en conditions de service.
- **Modélisation 3D** de la microstructure incluant la connectivité des pores, les défauts aux joints de grains et l'évolution de l'adhésion interfaciale.
- Prise en compte de la redistribution de porosité observée par Carr et al. (2015) : passage d'une distribution homogène à hétérogène après vieillissement.

---

## 9. Compétences développées

<div style="display: flex; flex-wrap: wrap; gap: 0.5em; margin-top: 0.5em;">
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Mesure thermique Flash 3D</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Méthode inverse</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Microscopie MEB / MEB-FEG</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Analyse d'images (ImageJ, Matlab)</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">mDSC / DSC / ATG</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Protocole d'élaboration</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Frittage Ag sous pression</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Vieillissement thermique accéléré</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Métrologie dimensionnelle</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Python / traitement de données</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">MATLAB / modélisation thermique</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Préparation métallographique</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Rédaction scientifique (EN/FR)</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Plan d'expériences</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Modélisation empirique (lois de comportement)</span>
</div>
