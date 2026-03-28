---
title: ""
permalink: /
layout: single
author_profile: true
classes: wide
---

<style>
.phd-hero {
  padding: 2rem 0 1rem;
}

.phd-badge {
  display: inline-block;
  margin-bottom: 1rem;
  padding: 0.35rem 0.8rem;
  border-radius: 999px;
  background: #e6f4f1;
  color: #0f766e;
  font-size: 0.9rem;
  font-weight: 600;
}

.phd-lead {
  font-size: 1.05rem;
  color: #4b5563;
  max-width: 900px;
}

.phd-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin: 1rem 0 1.5rem;
}

.phd-meta span {
  display: inline-block;
  padding: 0.55rem 0.85rem;
  border: 1px solid #e5e7eb;
  border-radius: 999px;
  background: #fff;
  font-size: 0.95rem;
}

.phd-highlight {
  margin: 1.5rem 0 2rem;
  padding: 1.1rem 1.2rem;
  border-left: 4px solid #0f766e;
  background: #f8fafc;
  border-radius: 0.75rem;
}

.phd-grid-2,
.phd-grid-3,
.phd-kpis {
  display: grid;
  gap: 1rem;
  margin: 1.25rem 0;
}

.phd-grid-2 {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}

.phd-grid-3 {
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.phd-kpis {
  grid-template-columns: repeat(4, minmax(0, 1fr));
}

.phd-card,
.phd-kpi {
  background: #fff;
  border: 1px solid #e5e7eb;
  border-radius: 1rem;
  padding: 1.1rem;
}

.phd-card h3 {
  margin-top: 0;
  margin-bottom: 0.6rem;
  font-size: 1.05rem;
}

.phd-kpi {
  text-align: center;
}

.phd-kpi-value {
  font-size: 1.7rem;
  font-weight: 700;
  color: #0f766e;
  line-height: 1.1;
}

.phd-kpi-label {
  margin-top: 0.4rem;
  font-size: 0.92rem;
  color: #6b7280;
}

.phd-figure {
  margin: 1.5rem 0;
  text-align: center;
}

.phd-figure img {
  border-radius: 1rem;
}

.phd-figure figcaption {
  margin-top: 0.6rem;
  font-size: 0.92rem;
  color: #6b7280;
}

.phd-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-top: 1rem;
}

.phd-tag {
  display: inline-block;
  padding: 0.45rem 0.75rem;
  border-radius: 999px;
  background: #f3f4f6;
  border: 1px solid #e5e7eb;
  font-size: 0.9rem;
}

@media (max-width: 900px) {
  .phd-grid-2,
  .phd-grid-3,
  .phd-kpis {
    grid-template-columns: 1fr;
  }
}
</style>

<div class="phd-hero">
  <span class="phd-badge">Thèse de doctorat · Université de Poitiers · ENSMA · Institut P’</span>

# Étude expérimentale de la conductivité thermique de l’argent fritté poreux : effet du vieillissement thermique et de l’interface avec un substrat de cuivre

<p class="phd-lead">
Travaux de thèse consacrés à la caractérisation thermique de matériaux d’assemblage innovants pour l’électronique de puissance, à l’interface entre expérimentation, modélisation et analyse microstructurale.
</p>

<div class="phd-meta">
  <span><strong>Encadrement :</strong> Y. Billaud &amp; X. Milhet</span>
  <span><strong>Financement :</strong> ACI++ Pprime Eprom · UE FEDER</span>
  <span><strong>Publication principale :</strong> Acta Materialia (2023)</span>
</div>
</div>

<div class="phd-highlight">
<strong>Problématique.</strong> Les composants SiC et GaN de nouvelle génération fonctionnent à des températures élevées et imposent des contraintes croissantes de dissipation thermique. Dans ce contexte, l’argent fritté constitue une alternative prometteuse aux brasures classiques, mais sa microstructure poreuse, son évolution sous vieillissement et le rôle de l’interface Ag/Cu rendent son comportement thermique difficile à décrire de manière robuste.
</div>

<div class="phd-kpis">
  <div class="phd-kpi">
    <div class="phd-kpi-value">+84 %</div>
    <div class="phd-kpi-label">gain de conductivité thermique entre 0 et 10 MPa</div>
  </div>
  <div class="phd-kpi">
    <div class="phd-kpi-value">+62 %</div>
    <div class="phd-kpi-label">augmentation de densité par pression de frittage</div>
  </div>
  <div class="phd-kpi">
    <div class="phd-kpi-value">≈ 45 min</div>
    <div class="phd-kpi-label">temps caractéristique du saut initial de λ</div>
  </div>
  <div class="phd-kpi">
    <div class="phd-kpi-value">≈ 50 %</div>
    <div class="phd-kpi-label">de la couche d’Ag affectée à 500 h @ 350 °C</div>
  </div>
</div>

## 1. Contexte et enjeu scientifique

Les modules d’électronique de puissance reposent sur une chaîne de dissipation thermique dans laquelle l’interconnexion entre la puce et le substrat joue un rôle critique. Avec l’essor des composants SiC et GaN, capables de fonctionner au-delà de **250 °C**, les solutions d’assemblage conventionnelles deviennent limitantes.

L’**argent fritté** apparaît alors comme un matériau d’interconnexion particulièrement attractif : il combine une **conductivité thermique théorique très élevée** (**426 W·m⁻¹·K⁻¹**), une **température d’élaboration modérée** (**200–300 °C**) et l’absence de fusion en service. En revanche, sa **porosité**, la dispersion de sa **microstructure** et l’évolution de ses propriétés sous **vieillissement thermique** compliquent fortement sa caractérisation.

<figure class="phd-figure">
  <img src="{{ '/images/module-puissance.png' | relative_url }}" alt="Architecture type d’un module de puissance" style="width:100%; max-width:720px;">
  <figcaption>
    Architecture type d’un module de puissance et position critique de l’interconnexion dans la chaîne de dissipation thermique.
  </figcaption>
</figure>

## 2. Verrous scientifiques

Cette thèse s’est structurée autour de trois verrous principaux :

<div class="phd-grid-3">
  <div class="phd-card">
    <h3>Mesurer un matériau hautement diffusif</h3>
    <p>
      La très forte diffusivité thermique de l’Ag limite la validité des approches flash 1D classiques. Une méthode tenant compte d’effets 2D/3D était nécessaire.
    </p>
  </div>

  <div class="phd-card">
    <h3>Relier conductivité, densité et vieillissement</h3>
    <p>
      La densité contrôle une part importante du comportement thermique, mais la relation entre porosité, conductivité et vieillissement restait encore mal établie.
    </p>
  </div>

  <div class="phd-card">
    <h3>Quantifier l’effet de l’interface Ag/Cu</h3>
    <p>
      Dans les assemblages réels, l’interface entre l’argent fritté et le cuivre influence la performance thermique globale, en particulier à long terme.
    </p>
  </div>
</div>

## 3. Démarche adoptée

### Une contribution méthodologique : la Flash 3D adaptée aux matériaux très conducteurs

Le cœur de la démarche repose sur l’utilisation de la **méthode Flash 3D**, adaptée à l’étude de matériaux hautement diffusifs comme l’argent. Le dispositif expérimental combine :

- une **excitation laser locale CO₂** (**130 W, 10 ms**) ;
- une **caméra infrarouge haute vitesse** (**2000 fps**) ;
- une identification des propriétés thermiques par **résolution inverse** d’un modèle 3D instationnaire.

Une **phase de calibration** sur des matériaux de référence (**Al, Cu, Ag massif**) a permis de définir les paramètres expérimentaux pertinents et d’atteindre une **erreur de mesure inférieure à 6 %**.

<div class="phd-grid-2">
  <figure class="phd-figure">
    <img src="{{ '/images/setup-flash3d.png' | relative_url }}" alt="Banc expérimental Flash 3D" style="width:100%; max-width:520px;">
    <figcaption>Banc expérimental de la méthode Flash 3D.</figcaption>
  </figure>

  <figure class="phd-figure">
    <img src="{{ '/images/principe-identification.png' | relative_url }}" alt="Principe d’identification thermique" style="width:100%; max-width:620px;">
    <figcaption>Identification inverse des conductivités thermiques à partir des images infrarouges.</figcaption>
  </figure>
</div>

### Élaboration et caractérisation des échantillons

L’étude repose sur deux familles d’échantillons :

- des **plaques d’Ag fritté seul**, pour isoler le comportement intrinsèque du matériau ;
- des **bicouches Ag/Cu**, pour intégrer le rôle de l’interface.

Le protocole d’élaboration comprend un dépôt multicouche de pâte d’argent, un dégazage sous vide primaire, puis un **frittage sous pression à 270 °C pendant 5 min**, avec une pression variant de **0 à 10 MPa**.

Le vieillissement thermique a ensuite été conduit sous vide primaire à **150, 250 et 350 °C**, pour des durées allant jusqu’à **500 h**.

## 4. Résultats — Ag fritté seul

### Corrélation densité / conductivité

La pression de frittage s’est révélée être le levier majeur de contrôle des propriétés thermiques. Entre **0 et 10 MPa**, la densité augmente de **62 %** et la conductivité thermique de **84 %**.

Les mesures obtenues s’alignent avec les modèles de la littérature basés sur des pores sphériques et cylindriques, ce qui confirme la robustesse de la relation établie entre microstructure poreuse et transport thermique.

<figure class="phd-figure">
  <img src="{{ '/images/ag-non-vieilli.png' | relative_url }}" alt="Conductivité thermique en fonction de la porosité" style="width:100%; max-width:760px;">
  <figcaption>
    Évolution de la conductivité thermique en fonction de la porosité relative pour différentes pressions de frittage.
  </figcaption>
</figure>

### Effet du vieillissement thermique

Le vieillissement met en évidence une cinétique en deux temps :

1. une **augmentation initiale rapide** de la conductivité thermique ;
2. puis une **stabilisation** à plus long terme.

Le point important est que cette hausse initiale intervient dans les **premières 45 minutes**, alors que la **densité reste stable** jusqu’à **500 h à 350 °C**. L’évolution observée n’est donc pas attribuée à une densification supplémentaire, mais à une **relaxation de contraintes résiduelles** générées au cours du frittage.

<div class="phd-grid-2">
  <figure class="phd-figure">
    <img src="{{ '/images/ag-cinetique.png' | relative_url }}" alt="Cinétique d’évolution de la conductivité" style="width:100%; max-width:760px;">
    <figcaption>Cinétique d’évolution de la conductivité thermique sous vieillissement.</figcaption>
  </figure>

  <figure class="phd-figure">
    <img src="{{ '/images/ag-vieillissement.png' | relative_url }}" alt="Évolution de lambda au vieillissement" style="width:100%; max-width:760px;">
    <figcaption>Hausse initiale de λ puis stabilisation à plus long terme.</figcaption>
  </figure>
</div>

## 5. Résultats — bicouches Ag/Cu

L’étude des bicouches Ag/Cu montre que le comportement à long terme ne peut plus être expliqué par les seules propriétés de l’Ag fritté.

Au début du vieillissement, la conductivité suit une tendance proche de celle observée pour l’Ag seul. En revanche, **au-delà de 200 h**, une **dégradation progressive puis marquée** apparaît. Cette baisse est absente des monocouches et met donc en évidence le rôle déterminant de l’**interface Ag/Cu**.

<figure class="phd-figure">
  <img src="{{ '/images/agcu-vieillissement.png' | relative_url }}" alt="Vieillissement des bicouches Ag Cu" style="width:100%; max-width:760px;">
  <figcaption>
    Évolution de la conductivité thermique effective des bicouches Ag/Cu au cours du vieillissement.
  </figcaption>
</figure>

L’analyse microstructurale met en évidence une **zone interfaciale à porosité inhomogène**, dont l’épaisseur évolue avec le temps. Aucune nouvelle phase chimique significative n’a été détectée, ce qui conduit à attribuer la dégradation observée à une évolution **microstructurale locale** plutôt qu’à une transformation chimique.

Un modèle en couches a permis d’estimer qu’à **500 h @ 350 °C**, environ **50 % de l’épaisseur de la couche d’Ag** est affectée par le vieillissement. Le modèle reste pertinent jusqu’à environ **200 h**, puis montre une divergence croissante, suggérant l’existence de mécanismes additionnels non capturés à ce niveau de description.

## 6. Apport scientifique

Cette thèse apporte plusieurs résultats structurants :

- l’**adaptation et la calibration** de la méthode Flash 3D pour des matériaux hautement diffusifs ;
- l’établissement d’une relation robuste entre **densité, porosité et conductivité thermique** de l’Ag fritté ;
- l’identification d’une **cinétique initiale rapide** de vieillissement thermique ;
- la mise en évidence du rôle critique de l’**interface Ag/Cu** dans la dégradation thermique à temps long.

## 7. Limites et perspectives

Les résultats obtenus ouvrent plusieurs perspectives à fort intérêt scientifique et industriel :

- extension aux systèmes **Cu/Ag/Cu** et **SiC/Ag** ;
- essais en **cyclage thermique** plus représentatifs des conditions de service ;
- modélisation 3D plus fine de la microstructure ;
- prise en compte de l’évolution de l’**adhésion interfaciale** et des défauts aux joints de grains.

## 8. Publications

- **Acta Materialia · 2023** — **A. Sghuri**, Y. Billaud, X. Milhet et al.  
  *Thermal conductivity of porous sintered silver: effect of density and thermal aging.*

- **SFT · 2021** — **A. Sghuri**, Y. Billaud, X. Milhet  
  Calibration de la méthode Flash 3D pour matériaux hautement conducteurs.

## 9. Compétences développées

<div class="phd-tags">
  <span class="phd-tag">Flash 3D</span>
  <span class="phd-tag">Méthode inverse (ENH)</span>
  <span class="phd-tag">Microscopie MEB</span>
  <span class="phd-tag">Analyse d’images</span>
  <span class="phd-tag">mDSC / calorimétrie</span>
  <span class="phd-tag">Frittage Ag sous pression</span>
  <span class="phd-tag">Vieillissement thermique</span>
  <span class="phd-tag">Python</span>
  <span class="phd-tag">MATLAB</span>
  <span class="phd-tag">Rédaction scientifique FR/EN</span>
</div>
