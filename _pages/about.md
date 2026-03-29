---
layout: single
title: "Thèse de doctorat"
permalink: /
author_profile: true
toc: true
toc_label: "Sommaire"
toc_icon: "flask"
toc_sticky: true
---

# Étude expérimentale de la conductivité thermique de l'argent fritté poreux : effet du vieillissement thermique et de l'interface avec un substrat de cuivre

*Thèse de doctorat · Université de Poitiers · ENSMA · Institut P' (Pprime, UPR CNRS 3346)*

> Sujet de thèse centré sur l'évaluation des performances thermiques de matériaux d'assemblage innovants pour l'électronique de puissance. Travaux menés à l'interface entre expérimentation, modélisation et analyse de données, avec un enjeu fort de fiabilité et de compréhension du vieillissement des matériaux.

- **Directeurs :** X. Milhet (MCF HDR) & Y. Billaud (MCF)
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
      Conductivité maximale atteinte en ≈ 45 min de vieillissement · densité et taille de grains stables jusqu'à 500 h · mécanisme identifié : relaxation de contraintes résiduelles
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

| Matériau (99,95%) | Réf. conductivité (W·m⁻¹·K⁻¹) |
|:---|:---|
| Ag | 426 – 433 |
| Cu | 386 – 401 |
| Al | 237 – 239 |

### 3.3. Élaboration des échantillons

#### Procédé de frittage

Le protocole d'élaboration comprend :

1. **Dépôt de pâte d'Ag** (nanoparticules, diamètre moyen 20–40 nm, 17 % de solvant) sur substrat Kapton (Ag seul) ou Cu (bicouches).
2. **Dégazage sous vide primaire** (14 mbar) à température ambiante — plateau de masse résiduelle (~85 %) atteint après ~30 min, confirmant l'élimination des solvants.
3. **Répétition** du cycle dépôt + dégazage selon l'épaisseur finale désirée.
4. **Frittage** à **270 °C pendant 5 min** sous pression de **0 à 10 MPa** (machine jusqu'à 100 kN).

![Procédé de frittage](/images/frittage-process.png)
*Procédé d'élaboration : dépôt multicouche, dégazage sous vide et frittage 0–10 MPa @ 270 °C pendant 5 min.*

L'empilement des couches a été validé : la porosité est **homogène dans l'épaisseur**, comme confirmé par des analyses d'images MEB systématiques sur la tranche (taux de porosité surfacique constant ~10–12 % sur toute l'épaisseur pour un échantillon à 10 MPa).

#### Détermination de la température de frittage

La **température de frittage** a été déterminée par **DSC** couplée à l'**ATG** sur la plage **25–300 °C** à **10 °C/min** :

- **DSC** : premier pic vers **125 °C** (dégazage des solvants), second vers **257 °C** (frittage des particules).
- **ATG** : perte de masse de **~17 %** entre 100 et 210 °C, puis **~1 %** supplémentaire (décomposition du liant/dispersant).
- **MEB** : microstructure stable jusqu'à **250 °C**, puis coalescence des particules au-delà.

Ces résultats convergent vers le choix d'un frittage à **270 °C / 5 min** — compromis entre élimination du dispersant et compaction.

![ATG-DSC-MEB](/images/ATG-DSC-MEB.png)
*Analyses DSC/ATG et évolution microstructurale de la pâte d'argent en fonction de la température.*

### 3.4. Caractérisation microstructurale et thermophysique

#### Mesure de densité

La densité apparente a été déterminée par le rapport **masse/volume** :

- **Masse** : balance (précision ~10 mg)
- **Dimensions latérales** : profilomètre optique (~1 µm)
- **Épaisseur** : comparateur mécanique digital (~1 µm)
- **Erreur sur la densité : ~2 %**

Résultat : la pression de frittage contrôle directement la densité — de ~3 g·cm⁻³ (0 MPa) à ~8 g·cm⁻³ (10 MPa).

#### Porosité par imagerie MEB

La porosité primaire a été mesurée par **imagerie MEB** après préparation métallographique (polissages successifs : papiers 400, 800, 1200, 2000, 4000 → surface miroir). Les images acquises à **5000×** ont été traitées sous **ImageJ et Matlab** par binarisation et seuillage pour quantifier la fraction surfacique de porosité.

![Évaluation de la porosité par traitement d'images MEB](/images/porosite-MEB.png)
*Traitement d'image pour l'évaluation de la porosité : image MEB brute, seuillage, puis binarisation pour quantifier la fraction surfacique des pores.*

#### Taille des grains

La taille des grains a été évaluée par **MEB-FEG** à **30 000×**. Les contours des grains ont été tracés, les images binarisées, puis les aires mesurées sous **ImageJ** et converties en **diamètre équivalent** (assimilation à des disques).

**Résultat :** diamètre moyen **≈ 300 nm** (295–315 nm selon la pression), écart-type **≈ 100–124 nm**, stable jusqu'à 500 h @ 350 °C.

![Taille des grains](/images/taille-grains.png)
*Traitement d'image pour l'évaluation de la taille des grains : image brute, tracé des joints, identification individuelle sous ImageJ.*

#### Capacité calorifique

La capacité calorifique a été mesurée par **mDSC** (analyse calorimétrique différentielle à balayage en mode modulé) entre **−25 °C et 300 °C** à **10 °C/min**. Ce paramètre est essentiel pour convertir la diffusivité thermique en conductivité thermique (λ = α · ρ · c).

**Résultat clé :** la capacité thermique **diminue** à mesure que la densité **augmente** (de ~600 J·kg⁻¹·K⁻¹ à 0 MPa à ~286 J·kg⁻¹·K⁻¹ à 10 MPa). Ce résultat contredit l'hypothèse courante de la littérature qui suppose c = c_Ag massif. La relation empirique établie est :

> **c(ρ) = 13,9·ρ² − 203·ρ + 1027** &nbsp;&nbsp;(R² = 0,99)

**Erreur : ~5 %**

### 3.5. Échantillons étudiés et plan de vieillissement

**Deux familles d'échantillons :**

| | Ag fritté seul | Bicouches Ag/Cu |
|:---|:---|:---|
| Dimensions | 5 × 5 cm | 5 × 5 cm |
| Épaisseur Ag | 0,5 – 1,4 mm | 0,12 – 0,46 mm |
| Épaisseur Cu | — | 0,1 mm |
| Pressions | 0 / 2 / 5 / 10 MPa | 0 / 2 / 5 / 10 MPa |
| Lots | × 3 | × 1 |

**Vieillissement :** sous vide primaire (four Pyrox) pour limiter l'oxydation parasite.

| | Ag seul | Bicouches Ag/Cu |
|:---|:---|:---|
| Températures | 150 / 250 / 350 °C | 350 °C |
| Durées | 50 / 200 / 500 h | 50 / 200 / 500 h |

---

## 4. Résultats : Ag fritté seul

### 4.1. Corrélation densité → conductivité thermique

La pression de frittage est le levier principal : passer de 0 à 10 MPa augmente la densité de **62 %** et la conductivité thermique de **84 %**. Sur une porosité relative de **~25–75 % (±2 %)**, la conductivité varie d'un **facteur ~4** (de **222 à 66 W·m⁻¹·K⁻¹**).

Les mesures s'alignent sur les prédictions des modèles à pores sphériques et cylindriques d'Ordonez-Miranda et al. (2016), fondés sur la théorie du milieu effectif différentiel :

> **λ_eff = λ₀ · (1 − p)ⁿ**

avec *n* dépendant de la forme des pores (3/2 pour sphérique, 5/3 pour cylindrique, ∞ pour plat).

La relation empirique conductivité–densité (après vieillissement) est :

> **λ = 1,58·ρ² + 10,9·ρ + 20** &nbsp;&nbsp;(R² = 0,97)

![Conductivité vs porosité](/images/ag-non-vieilli.png)
*Conductivité thermique mesurée en fonction de la porosité relative, pour 4 pressions de frittage. Comparaison avec les modèles de pore sphérique, cylindrique et plat (Ordonez-Miranda et al., 2016).*

### 4.2. Effet du vieillissement thermique

Le vieillissement révèle une dynamique en deux temps :

**Étape 1 (ES1) — Saut initial rapide :** la conductivité thermique augmente significativement dans les **premières 45 minutes** de vieillissement. Ce saut est d'autant plus marqué que la pression de frittage est élevée. À 0 MPa, l'évolution est très limitée et plus lente.

**Étape 2 (ES2) — Stabilisation :** après ES1, la conductivité se stabilise. L'évolution résiduelle ne dépend ni de la procédure d'élaboration ni de la densité.

![Cinétique d'évolution](/images/ag-cinetique.png)
*Cinétique fine — λ atteint son maximum en ≈ 45 min (Ag 10 MPa @ 150 °C, mesures par intervalles de 15 min).*

![Barplot vieillissement](/images/ag-vieillissement.png)
*Évolution de λ pour 0–10 MPa, 150–350 °C, jusqu'à 500 h.*

**Trois observations majeures :**

1. **La densité reste parfaitement stable** jusqu'à 500 h à 350 °C, quelle que soit la pression de frittage. L'évolution de λ n'est donc pas liée à une densification globale.
2. **La taille des grains reste inchangée** (≈ 300 nm, confirmé par MEB-FEG colorisée à 2 et 10 MPa, vieilli à 350 °C). Ce résultat est corroboré par Zuo et al. (2022) et Agyakwa (2024).
3. **Après vieillissement**, les conductivités mesurées correspondent aux prédictions pour des pores **sphériques et cylindriques**, alors qu'avant vieillissement elles se situaient vers le modèle à pores plats.

> **Interprétation clé :** l'augmentation initiale de λ est attribuée à la **relaxation de contraintes résiduelles de compression** générées lors du frittage sous pression. Milhet et al. (2015) ont montré par résonance dynamique que ~10 % de la contrainte appliquée n'est pas relâchée après frittage, et que ces contraintes se relâchent lors du vieillissement. Lee et al. (2010) ont par ailleurs démontré que la conductivité thermique est fortement affectée par les contraintes/déformations mécaniques.

---

## 5. Résultats : bicouches Ag/Cu

### 5.1. L'interface change tout à long terme

Les bicouches Ag/Cu présentent d'abord le même comportement que l'Ag seul : une hausse de λ dans les 50 premières heures. Puis, **au-delà de 200 h**, une **dégradation progressive et significative** apparaît — absente dans les échantillons monocouches.

La densité globale des bicouches reste stable (confirmé jusqu'à 500 h @ 350 °C, pour toutes les pressions).

![Barplot λ Ag/Cu](/images/agcu-vieillissement.png)
*Évolution de la conductivité effective des bicouches Ag/Cu au cours du vieillissement @ 350 °C. La tendance en pointillés représente l'Ag fritté seul (pas de dégradation).*

### 5.2. Validation de la méthode Flash 3D sur bicouches

La compatibilité de la méthode Flash 3D avec un matériau bicouche a été vérifiée par des mesures dans **quatre configurations** (laser côté Ag/Cu, caméra côté Ag/Cu). Résultat : les erreurs relatives restent **inférieures à 4 %** et la conductivité mesurée est **indépendante de la configuration**, suggérant la réponse d'un matériau homogène effectif.

| Pression (MPa) | Config. (a) réf. | Config. (b) | Config. (c) | Config. (d) |
|:---|:---|:---|:---|:---|
| 0 | 116 | 116 | 117 | 119 |
| 2 | 218 | 226 | 213 | 214 |
| 5 | 268 | 261 | 262 | 258 |
| 10 | 296 | 292 | 288 | 292 |

*Conductivité thermique (W·m⁻¹·K⁻¹) mesurée selon 4 configurations laser/caméra. Erreur relative ≤ 4 %.*

### 5.3. Estimation sans effet d'interface

Un modèle de mélange (loi des mélanges en épaisseur) utilisant les propriétés de l'Ag fritté seul vieilli et du Cu permet d'estimer ce que devrait être la conductivité des bicouches **en l'absence d'effet d'interface** :

> **λ_Ag/Cu estimé = f_Ag · λ_Ag + f_Cu · λ_Cu + f_int · λ_int**

**Résultat :**

- **Adéquation** entre estimations et mesures jusqu'à **~200 h** de vieillissement @ 350 °C.
- **Divergence croissante** au-delà (jusqu'à **~36 %** à faible pression, **~17,9 %** à 10 MPa à 500 h).
- Cette divergence, supérieure à la marge d'erreur de mesure (~6 %), confirme un **effet d'interface réel**.

### 5.4. Évolution microstructurale de l'interface

L'analyse MEB de la tranche des bicouches vieillis révèle :

- **Pas de nouvelles phases** détectées (ni oxyde, ni alliage Ag_xCu_y par EDS).
- **Deux zones** à porosité distincte : une **zone dense (LPA, ~55 %)** et une **zone poreuse (HPA)**, probablement liée au dégazage du dispersant/liant lors du frittage.
- L'évolution de la **porosité apparente** en fonction du temps de vieillissement est qualitativement visible sur les images MEB.

L'épaisseur de la zone d'interface a été quantifiée par une **méthode originale de segmentation pixel par pixel** : binarisation des images MEB, calcul d'un profil cumulatif de porosité selon l'épaisseur, puis identification des limites inférieure (contact Ag/Cu) et supérieure (transition vers le comportement de l'Ag sain).

**Évolution du taux de porosité en surface (TPS) :**

| Temps (h) | TPS zone Ag (%) | TPS interface (%) |
|:---|:---|:---|
| 0 | ~11 | ~39 |
| 50 | ~12 | ~7 |
| 200 | ~15 | ~20 |
| 500 | ~46 | ~20 |

À l'interface : réduction significative du TPS après 50 h, puis stabilisation. En zone Ag : hausse marquée du TPS à long terme.

### 5.5. Estimation des propriétés locales

La chaîne d'estimation **TPS → densité → conductivité** repose sur deux corrélations établies sur l'Ag fritté seul :

> **ρ = 16·10⁻⁶·TPS² − 0,24·TPS + 10,5** &nbsp;&nbsp;(R² = 0,95)
>
> **λ = 2,3·ρ² + 8,9·ρ + 25,9** &nbsp;&nbsp;(R² = 0,97)

**Propriétés locales estimées (10 MPa, vieilli @ 350 °C) :**

| Temps (h) | λ zone Ag (W·m⁻¹·K⁻¹) | λ interface (W·m⁻¹·K⁻¹) |
|:---|:---|:---|
| 0 | 140 | 76 |
| 50 | 219 | 281 |
| 200 | 271 | 173 |
| 500 | 71 | 178 |

### 5.6. Quantification de la zone Ag affectée

Un modèle en couches (**Cu + interface + zone Ag affectée + Ag sain**) permet d'estimer l'épaisseur de la zone Ag dégradée.

| Temps (h) | λ_Ag exp | f_Zone Ag | f_Ag sain | l_Zone Ag (mm) | l_Ag sain (mm) | % Ag affecté |
|:---|:---|:---|:---|:---|:---|:---|
| 0 | 301 | 0 | 0,547 | 0,0 | 0,121 | 0 |
| 50 | 319 | 0 | 0,547 | 0,0 | 0,121 | 0 |
| 200 | 308 | 0 | 0,547 | 0,0 | 0,121 | 0 |
| **500** | **269** | **0,267** | **0,280** | **0,059** | **0,062** | **48,8** |

> **À 500 h @ 350 °C, environ 50 % de la couche d'Ag est affectée par le vieillissement.**

Le modèle prédit correctement λ jusqu'à ~200 h. Au-delà, la divergence croissante suggère des phénomènes non capturés : redistribution de porosité en 3D, défauts aux joints de grains, évolution de l'adhésion Ag/Cu.

---

## 6. Synthèse des contributions

Cette thèse apporte plusieurs résultats structurants, de la méthode de mesure à la compréhension des mécanismes :

| Contribution | Résultat clé |
|:---|:---|
| **Méthode Flash 3D calibrée** | Critères d'acquisition explicites (≥1200 trames, S/B ≥5), erreur <6 %, répétabilité validée |
| **Loi porosité ↔ λ** | Variation ×4 sur 25–75 % de porosité (222 → 66 W·m⁻¹·K⁻¹), R² = 0,97 |
| **Cinétique de vieillissement** | Maximum atteint en ~45 min ; densité et taille de grains stables |
| **Mécanisme identifié** | Relaxation de contraintes résiduelles de compression |
| **Interface Ag/Cu** | Effet critique à temps long : divergence à 200–500 h, ~50 % d'Ag affecté |
| **Modèles empiriques** | c(ρ) R²=0,99, λ(ρ) R²=0,97, TPS→ρ→λ R²=0,95 |
| **Capacité thermique mesurée** | Infirmation de l'hypothèse c = c_Ag massif couramment utilisée |

---

## 7. Publications & communications

- **Acta Materialia · 2023** — **A. Sghuri**, Y. Billaud, L. Signor, D. Saury, X. Milhet — [*Experimental investigation of thermal conductivity during aging of nanoporous sintered silver*](https://doi.org/10.1016/j.actamat.2023.119109)
- **IMAPS · 2023** — **A. Sghuri**, Y. Billaud, L. Signor, D. Saury, X. Milhet — *Evolution of the thermal conductivity of sintered Ag paste as a function of the density and aging* — 16th European Advanced Technology Workshop on Micropackaging and Thermal management, Poitiers.
- **SFT · 2021** — **A. Sghuri**, Y. Billaud, X. Milhet — Calibration de la méthode Flash 3D pour matériaux hautement conducteurs.

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
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Méthode inverse (ENH)</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Microscopie MEB / MEB-FEG</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Analyse d'images (ImageJ, Matlab)</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">mDSC / DSC / ATG</span>
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
