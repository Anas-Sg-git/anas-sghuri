---
permalink: /
title: "Anas Sghuri"
author_profile: true
---

<style>
/* ── Hero ─────────────────────────────────────────── */
.hero-subtitle {
  font-size: 1.15em;
  color: #555;
  margin-top: -0.5em;
  margin-bottom: 0.6em;
  font-weight: 400;
}
.hero-accroche {
  font-size: 0.97em;
  color: #444;
  margin-bottom: 1.4em;
  font-style: italic;
  max-width: 620px;
}
/* ── KPI cards ───────────────────────────────────── */
.kpi-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 0.6em;
  margin: 1.2em 0 1.5em;
}
@media (max-width: 1024px) {
  .kpi-grid { grid-template-columns: repeat(3, 1fr); }
}
@media (max-width: 768px) {
  .kpi-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 480px) {
  .kpi-grid { grid-template-columns: 1fr; }
}
.kpi-card {
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 0.75em 0.85em;
  background: #fafafa;
  text-align: left;
}
.kpi-card .kpi-value {
  font-size: 0.92em;
  font-weight: 700;
  color: #1a1a1a;
  line-height: 1.3;
}
.kpi-card .kpi-label {
  font-size: 0.74em;
  color: #666;
  margin-top: 0.3em;
  line-height: 1.3;
}
.kpi-card .kpi-impact {
  font-size: 0.7em;
  color: #888;
  margin-top: 0.6em;
  font-style: italic;
  line-height: 1.4;
}
/* ── CTA buttons ─────────────────────────────────── */
.cta-row {
  display: flex;
  gap: 0.75em;
  flex-wrap: wrap;
  margin-bottom: 2em;
}
.btn-primary {
  display: inline-block;
  padding: 0.5em 1.2em;
  background: #1a7abf;
  color: #fff !important;
  border-radius: 4px;
  font-size: 0.9em;
  text-decoration: none;
  font-weight: 600;
}
.btn-primary:hover { background: #145f96; }
.btn-secondary {
  display: inline-block;
  padding: 0.5em 1.2em;
  border: 1.5px solid #1a7abf;
  color: #1a7abf !important;
  border-radius: 4px;
  font-size: 0.9em;
  text-decoration: none;
  font-weight: 600;
  background: transparent;
}
.btn-secondary:hover { background: #eaf3fb; }
/* ── Section headings ────────────────────────────── */
.section-divider {
  border: none;
  border-top: 1px solid #e0e0e0;
  margin: 2.2em 0 1.6em;
}
/* ── Competence chain ────────────────────────────── */
.chain-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.7em;
  margin: 1em 0 1.2em;
}
@media (max-width: 768px) {
  .chain-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 480px) {
  .chain-grid { grid-template-columns: 1fr; }
}
.chain-item {
  border-left: 3px solid #1a7abf;
  padding: 0.5em 0.75em;
  background: #f7f9fc;
  border-radius: 0 4px 4px 0;
}
.chain-item .chain-num {
  font-size: 0.7em;
  color: #1a7abf;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
.chain-item .chain-title {
  font-size: 0.88em;
  font-weight: 600;
  color: #1a1a1a;
  line-height: 1.3;
}
.chain-item .chain-desc {
  font-size: 0.76em;
  color: #666;
  margin-top: 0.1em;
}
/* ── Portfolio cards ─────────────────────────────── */
.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1em;
  margin: 1em 0 1.2em;
}
@media (max-width: 768px) {
  .portfolio-grid { grid-template-columns: 1fr; }
}
.portfolio-card {
  border: 1px solid #ddd;
  border-radius: 5px;
  overflow: hidden;
  background: #fff;
}
.portfolio-card img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  background: #eaeff4;
  display: block;
}
.portfolio-card .portfolio-placeholder {
  width: 100%;
  height: 140px;
  background: #dce6f0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75em;
  color: #666;
}
.portfolio-card .portfolio-body {
  padding: 0.7em 0.85em 0.85em;
}
.portfolio-card .portfolio-title {
  font-size: 0.88em;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 0.3em;
  line-height: 1.3;
}
.portfolio-card .portfolio-desc {
  font-size: 0.78em;
  color: #555;
}
.portfolio-card a { text-decoration: none; color: inherit; }
.portfolio-card:hover { box-shadow: 0 2px 8px rgba(0,0,0,0.10); }
/* ── Publications list ───────────────────────────── */
.pub-block p { margin: 0.4em 0; font-size: 0.92em; }
/* ── Contact block ───────────────────────────────── */
.contact-block {
  background: #f7f9fc;
  border-radius: 5px;
  padding: 1em 1.2em;
  font-size: 0.92em;
}
</style>
 
<!-- ═══════════════════════════════════════════════════
     HERO
═══════════════════════════════════════════════════ -->
 
<p class="hero-subtitle">Docteur-ingénieur — R&D matériaux &amp; caractérisation</p>
<!--
  CHOIX D'ACCROCHE — décommenter celle retenue, supprimer les deux autres.
  Option A — Angle « résultat phare » (recommandé) :
-->
<p class="hero-accroche">Élaboration, caractérisation, mécanisme, publication.</p>
<!--
  Option B — Angle « positionnement poste » :
  <p class="hero-accroche">Je recherche un poste d'ingénieur R&D matériaux ou caractérisation en environnement industriel — France, mobilité nationale.</p>
  Option C — Zéro narration (supprimer la balise .hero-accroche entière) :
-->
 
<div class="kpi-grid">
  <div class="kpi-card">
    <div class="kpi-value">Frittage Ag · 0–10 MPa</div>
    <div class="kpi-label">Procédé qualifié bout-en-bout · 270 °C</div>
    <div class="kpi-impact">Autonomie sur un procédé d'assemblage stratégique</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">Flash 3D · 1ère extension aux métaux</div>
    <div class="kpi-label">Ag, Cu, Al — diffusivité 10× à 100×</div>
    <div class="kpi-impact">Nouvelle capacité de mesure pour métaux</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">λ × 4 sur 25–75 % de porosité</div>
    <div class="kpi-label">222 → 66 W·m⁻¹·K⁻¹</div>
    <div class="kpi-impact">Levier procédé pour la dissipation thermique</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">Mécanisme du vieillissement élucidé</div>
    <div class="kpi-label">Relaxation des contraintes, pas la densification</div>
    <div class="kpi-impact">Identifie le vrai levier d'optimisation</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">Acta Materialia · IF 9.3</div>
    <div class="kpi-label">28 citations · 2023</div>
    <div class="kpi-impact">Validé par un filtre éditorial international</div>
  </div>
</div>
<div class="cta-row">
  <a class="btn-primary" href="{{ '/cv/' | relative_url }}">Voir le CV complet</a>
  <a class="btn-secondary" href="mailto:anas.sghuri@gmail.com">Me contacter</a>
</div>
---

## À propos

Docteur-ingénieur en sciences des matériaux, j'ai développé au cours de ma thèse un ensemble de compétences en caractérisation expérimentale, analyse de données et méthodologie de mesure, appliquées à des problématiques de fiabilité dans un contexte industriel exigeant.

Mon travail doctoral m'a conduit à concevoir des protocoles d'essais, exploiter des techniques de caractérisation avancées (MEB, MEB-FEG, DSC, ATG, méthode Flash 3D, micro-traction), traiter et interpréter des données complexes (MATLAB, Python, ImageJ), et établir des lois de comportement reliant microstructure et propriétés fonctionnelles.

Ces compétences sont directement transposables à tout environnement R&D ou industriel où la compréhension des matériaux, la rigueur expérimentale et la résolution de problèmes sont au cœur de l'activité — que ce soit en caractérisation, en essais, en qualité ou en recherche appliquée. Ce site présente en détail mes travaux de thèse, mes publications, mon expérience d'enseignement et les compétences que j'ai acquises.

<hr class="section-divider">

## Chaîne de compétences R&D matériaux

<div class="chain-grid">

  <div class="chain-item">
    <div class="chain-num">① </div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#dev-materiaux">Développement matériaux &amp; procédés</a></div>
    <div class="chain-desc">Frittage Ag, bicouches, optimisation process</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">②</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#preparation">Préparation &amp; métallographie</a></div>
    <div class="chain-desc">Enrobage, polissage miroir, préparation MEB</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">③</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#caracterisation">Caractérisation thermique / mécanique / micro</a></div>
    <div class="chain-desc">Flash 3D, DSC, ATG, MEB-FEG, microtraction</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">④</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#metrologie">Métrologie &amp; mesures physiques</a></div>
    <div class="chain-desc">Densité, porosité, incertitudes, calibration</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">⑤</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#modelisation">Modélisation numérique &amp; méthodes inverses</a></div>
    <div class="chain-desc">Équation chaleur 3D, estimateurs ENH, corrélations</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">⑥</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#programmation">Programmation scientifique &amp; traitement de données</a></div>
    <div class="chain-desc">MATLAB expert, Python, ImageJ, segmentation</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">⑦</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#analyse">Analyse &amp; résolution de problèmes</a></div>
    <div class="chain-desc">Diagnostic microstructural, hypothèses, confirmation</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">⑧</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#qualite">Qualité, sécurité &amp; réglementation</a></div>
    <div class="chain-desc">Traçabilité, SOPs, HSE laser et chimie</div>
  </div>

  <div class="chain-item">
    <div class="chain-num">⑨</div>
    <div class="chain-title"><a href="{{ '/cv/' | relative_url }}#veille">Veille &amp; recherche bibliographique</a></div>
    <div class="chain-desc">État de l'art, benchmark, RoHS/DEEE</div>
  </div>

</div>

[Voir le détail dans le CV →]({{ '/cv/' | relative_url }})

<hr class="section-divider">

## Portfolio

<div class="portfolio-grid">

  <div class="portfolio-card">
    <a href="{{ '/portfolio/portfolio-1-flash3d-codes/' | relative_url }}">
      <div class="portfolio-placeholder">Image Flash 3D (à ajouter)</div>
      <div class="portfolio-body">
        <div class="portfolio-title">Caractérisation thermique Flash 3D — Pipeline d'estimation et codes MATLAB</div>
        <div class="portfolio-desc">Méthode inverse ENH, critères d'acquisition, validation sur Al/Cu/Ag.</div>
      </div>
    </a>
  </div>

  <div class="portfolio-card">
    <a href="{{ '/portfolio/portfolio-2/' | relative_url }}">
      <div class="portfolio-placeholder">Image MEB interface (à ajouter)</div>
      <div class="portfolio-body">
        <div class="portfolio-title">Quantification d'interface par traitement d'images MEB</div>
        <div class="portfolio-desc">Segmentation MATLAB, épaisseur de zone Ag/Cu, évolution en vieillissement.</div>
      </div>
    </a>
  </div>

  <div class="portfolio-card">
    <a href="{{ '/portfolio/portfolio-3/' | relative_url }}">
      <img src="{{ '/images/SyntheseArgentNanoporeuxAgetAgCuTestsdeMicrotraction.png' | relative_url }}"
           alt="Microtraction Ag/Cu">
      <div class="portfolio-body">
        <div class="portfolio-title">Microtraction de systèmes Ag nanoporeux / Cu</div>
        <div class="portfolio-desc">Influence du vieillissement thermique et de la pression de frittage sur la fiabilité mécanique.</div>
      </div>
    </a>
  </div>

</div>

[Voir tous les projets →]({{ '/portfolio/' | relative_url }})

<hr class="section-divider">

## Thèse &amp; Publications

**Thèse de doctorat** — *Étude expérimentale de la conductivité thermique de l'argent fritté poreux : effet du vieillissement thermique et de l'interface avec un substrat de cuivre* — Université de Poitiers, Institut Pprime, soutenue le 11 mars 2024. Directeurs : X. Milhet &amp; Y. Billaud. [Manuscrit HAL (tel-05045482)](https://hal.science/tel-05045482)

**Article** — A. Sghuri et al., *Experimental investigation of thermal conductivity during aging of nanoporous sintered silver*, **Acta Materialia**, 2023 (IF 9.3 · 28 citations). [DOI 10.1016/j.actamat.2023.119109](https://doi.org/10.1016/j.actamat.2023.119109)

**Conférences (4 présentations orales)** — IMAPS · European ATW, Poitiers 2023 (international) · TMS Annual Meeting, Anaheim 2022 (international) · Congrès Français de Mécanique, Nantes 2022 · Congrès Français de Thermique, Belfort 2021.

[Voir toutes les publications →]({{ '/publications/' | relative_url }}) &ensp;·&ensp; [Voir la page thèse →]({{ '/phd/' | relative_url }})

<hr class="section-divider">

## Enseignement

ATER à l'ISAE-ENSMA (2022–2023) : 190+ heures d'enseignement (TP/TD/projets) auprès d'élèves ingénieurs — sciences des matériaux, choix des matériaux, ondes de choc laser, calcul scientifique, probabilités — et encadrement de 2 stages de recherche sur l'adhésion Ag/Cu par choc laser.

[Voir le détail →]({{ '/teaching/' | relative_url }})

<hr class="section-divider">

## Contact
 
<div class="contact-block" id="contact">
Ouvert à des opportunités en <strong>R&amp;D matériaux</strong>, <strong>caractérisation</strong>, <strong>essais</strong> ou <strong>qualité</strong>, dans tout secteur industriel. France — mobilité nationale.<br><br>
📧 <a href="mailto:anas.sghuri@gmail.com">anas.sghuri@gmail.com</a>
</div>
