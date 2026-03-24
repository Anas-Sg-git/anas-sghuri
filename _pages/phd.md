---
title: "PhD"
permalink: /phd/
layout: single
author_profile: true
---

<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=Source+Serif+4:ital,opsz,wght@0,8..60,300;0,8..60,400;1,8..60,300&display=swap" rel="stylesheet">

<style>
:root{--teal:#1D9E75;--teal-dark:#0F6E56;--teal-light:#E1F5EE;--charcoal:#1a1a1a;--mid:#444;--muted:#777;--border:#e8e8e8;--bg-subtle:#f8f8f6}
.phd-page{font-family:'Source Serif 4',Georgia,serif;color:var(--charcoal);max-width:860px;margin:0 auto}
.phd-hero{border-left:4px solid var(--teal);padding:2rem 0 2rem 1.75rem;margin-bottom:3rem}
.phd-hero .label{font-family:'Syne',sans-serif;font-size:.7rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase;color:var(--teal);display:block;margin-bottom:.75rem}
.phd-hero h1{font-family:'Syne',sans-serif;font-size:clamp(1.6rem,3vw,2.2rem);font-weight:800;line-height:1.15;margin:0 0 1rem;color:var(--charcoal);border:none;padding:0}
.phd-hero .subtitle{font-size:1.05rem;font-weight:300;font-style:italic;color:var(--mid);margin:0 0 1.5rem;max-width:600px}
.phd-hero .meta{font-family:'Syne',sans-serif;font-size:.8rem;color:var(--muted)}
.phd-hero .meta span{margin-right:1.5rem}
.stats-bar{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:1px;background:var(--border);border:1px solid var(--border);border-radius:6px;overflow:hidden;margin-bottom:3.5rem}
.stat-item{background:#fff;padding:1.2rem 1.5rem;text-align:center}
.stat-item .number{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;color:var(--teal);line-height:1;display:block}
.stat-item .unit{font-size:1rem;font-weight:400;color:var(--teal-dark)}
.stat-item .desc{font-size:.72rem;color:var(--muted);margin-top:.35rem;font-family:'Syne',sans-serif;line-height:1.3}
.phd-section{margin-bottom:3.5rem}
.section-tag{font-family:'Syne',sans-serif;font-size:.65rem;font-weight:700;letter-spacing:.18em;text-transform:uppercase;color:var(--teal);display:block;margin-bottom:.4rem}
.phd-section h2{font-family:'Syne',sans-serif;font-size:1.35rem;font-weight:700;color:var(--charcoal);margin:0 0 1.2rem;border:none;padding:0}
.phd-section p{font-size:1rem;line-height:1.75;color:var(--mid);margin-bottom:1rem}
.phd-section strong{color:var(--charcoal);font-weight:400}
.img-block{margin:1.5rem 0}
.img-block img{width:100%;border-radius:6px;border:1px solid var(--border);display:block}
.img-block figcaption{font-family:'Syne',sans-serif;font-size:.72rem;color:var(--muted);margin-top:.5rem;border-left:2px solid var(--teal-light);padding-left:.6rem}
.img-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin:1.5rem 0}
.img-grid .img-block{margin:0}
@media(max-width:600px){.img-grid{grid-template-columns:1fr}}
.callout{background:var(--teal-light);border-left:3px solid var(--teal);border-radius:0 6px 6px 0;padding:1rem 1.25rem;margin:1.5rem 0;font-size:.95rem;color:var(--teal-dark)}
.callout strong{color:var(--teal-dark);font-weight:700}
.challenge-list{list-style:none;padding:0;margin:1rem 0}
.challenge-list li{display:flex;gap:1rem;align-items:flex-start;padding:1rem 0;border-bottom:1px solid var(--border);font-size:.95rem;color:var(--mid);line-height:1.6}
.challenge-list li:last-child{border-bottom:none}
.challenge-num{font-family:'Syne',sans-serif;font-weight:800;font-size:1.5rem;color:var(--border);line-height:1;min-width:2rem}
.result-pair{display:grid;grid-template-columns:1fr 1fr;gap:1.5rem;margin:1.5rem 0}
@media(max-width:600px){.result-pair{grid-template-columns:1fr}}
.result-card{border:1px solid var(--border);border-radius:8px;padding:1.25rem;background:var(--bg-subtle)}
.result-card .rc-label{font-family:'Syne',sans-serif;font-size:.65rem;font-weight:700;letter-spacing:.15em;text-transform:uppercase;color:var(--teal);margin-bottom:.5rem;display:block}
.result-card h3{font-family:'Syne',sans-serif;font-size:.95rem;font-weight:700;color:var(--charcoal);margin:0 0 .6rem;border:none;padding:0}
.result-card p{font-size:.88rem;color:var(--mid);line-height:1.6;margin:0}
.result-card .finding{font-family:'Syne',sans-serif;font-size:.8rem;font-weight:700;color:var(--teal-dark);background:var(--teal-light);padding:.4rem .75rem;border-radius:4px;margin-top:.75rem;display:inline-block}
.pub-item{border-left:3px solid var(--charcoal);padding:.75rem 0 .75rem 1rem;margin-bottom:1.25rem;font-size:.9rem;color:var(--mid);line-height:1.65}
.pub-item .pub-journal{font-family:'Syne',sans-serif;font-size:.65rem;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--charcoal);display:block;margin-bottom:.3rem}
.skills-row{display:flex;flex-wrap:wrap;gap:.5rem;margin-top:.75rem}
.skill-chip{font-family:'Syne',sans-serif;font-size:.72rem;font-weight:700;padding:.3rem .75rem;border-radius:100px;border:1px solid var(--border);color:var(--mid);background:#fff}
.phd-divider{border:none;border-top:1px solid var(--border);margin:2.5rem 0}
.img-placeholder{width:100%;background:var(--bg-subtle);border:1.5px dashed var(--border);border-radius:6px;display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:220px;color:var(--muted);font-family:'Syne',sans-serif;font-size:.8rem;text-align:center;padding:1rem;box-sizing:border-box}
.img-placeholder .ph-slide{font-weight:700;color:var(--teal);margin-bottom:.25rem}
</style>

<div class="phd-page">

<div class="phd-hero">
  <span class="label">Thèse de doctorat · Institut P' · ENSMA · Université de Poitiers</span>
  <h1>Conductivité thermique de l'Argent fritté poreux :<br>vieillissement thermique &amp; interface Ag/Cu</h1>
  <p class="subtitle">Comprendre comment et pourquoi les propriétés thermiques évoluent dans les interconnexions pour l'électronique de puissance haute température.</p>
  <div class="meta">
    <span>Directeurs : Y. Billaud &amp; X. Milhet</span>
    <span>Financement : ACI++ Pprime Eprom · UE FEDER</span>
    <span>Publication : <em>Acta Materialia</em> (2023)</span>
  </div>
</div>

<div class="stats-bar">
  <div class="stat-item">
    <span class="number">+84<span class="unit">%</span></span>
    <div class="desc">Gain de conductivité par frittage sous 10 MPa</div>
  </div>
  <div class="stat-item">
    <span class="number">45<span class="unit"> min</span></span>
    <div class="desc">Cinétique de stabilisation de λ lors du vieillissement initial</div>
  </div>
  <div class="stat-item">
    <span class="number">500<span class="unit"> h</span></span>
    <div class="desc">Durée maximale de vieillissement thermique étudié</div>
  </div>
  <div class="stat-item">
    <span class="number">~50<span class="unit">%</span></span>
    <div class="desc">Zone Ag affectée par l'interface à 500 h @ 350 °C</div>
  </div>
  <div class="stat-item">
    <span class="number">&lt;6<span class="unit">%</span></span>
    <div class="desc">Incertitude de mesure Flash 3D après calibration</div>
  </div>
</div>

<div class="phd-section">
  <span class="section-tag">01 — Contexte &amp; enjeux</span>
  <h2>Pourquoi s'intéresser à l'Ag fritté en électronique de puissance ?</h2>
  <p>Les puces en <strong>SiC et GaN</strong> de nouvelle génération opèrent au-delà de 250 °C et dissipent des densités de puissance croissantes — en traction électrique, énergies renouvelables, aérospatiale. Les brasures classiques (SAC305 : 50 W·m⁻¹·K⁻¹) ne peuvent plus assurer l'évacuation thermique requise.</p>
  <p>L'<strong>argent fritté</strong> s'impose comme matériau d'interconnexion de nouvelle génération : conductivité théorique à 426 W·m⁻¹·K⁻¹, élaboration à basse température (200–300 °C), pas de fusion en service. Mais sa <strong>microstructure poreuse complexe</strong> génère une dispersion considérable dans les données publiées, et l'effet du vieillissement thermique sur ses propriétés restait très mal documenté.</p>
  <div class="img-block">
    <!-- Slide 2 → exporter en PNG → placer dans /assets/images/phd/module-puissance.png -->
    <!-- <img src="/assets/images/phd/module-puissance.png" alt="Architecture d'un module de puissance électronique"> -->
    <div class="img-placeholder">
      <div class="ph-slide">Slide 2 → /assets/images/phd/module-puissance.png</div>
      <div>Architecture Golf GTE + schéma assemblage module de puissance</div>
    </div>
    <figcaption>Architecture type d'un module de puissance — l'interconnexion entre la puce SiC/GaN et le substrat est le maillon thermique critique.</figcaption>
  </div>
</div>

<hr class="phd-divider">

<div class="phd-section">
  <span class="section-tag">02 — Verrou scientifique</span>
  <h2>Trois questions sans réponse robuste dans la littérature</h2>
  <p>La littérature recense plus d'une dizaine d'études sur la conductivité de l'Ag fritté, mais les résultats sont dispersés sur plus d'une décade pour un même taux de porosité. Trois problèmes fondamentaux se dégagent :</p>
  <ul class="challenge-list">
    <li>
      <span class="challenge-num">01</span>
      <div><strong style="color:var(--charcoal)">Mesurer sur un matériau hautement diffusif.</strong> L'Ag fritté est extrêmement conducteur, ce qui rend la méthode flash 1D inadaptée. Il fallait une méthode capable de gérer des effets 2D/3D et une anisotropie potentielle, sans hypothèse simplificatrice.</div>
    </li>
    <li>
      <span class="challenge-num">02</span>
      <div><strong style="color:var(--charcoal)">Relier conductivité, densité et vieillissement.</strong> La densité est le levier principal, mais personne n'avait encore établi de corrélation robuste λ = f(ρ, t, T) sur une large plage de conditions.</div>
    </li>
    <li>
      <span class="challenge-num">03</span>
      <div><strong style="color:var(--charcoal)">Quantifier l'effet de l'interface Ag/Cu.</strong> Dans un assemblage réel, l'argent repose sur un substrat cuivre. Les résistances d'interface sont systématiquement négligées dans la littérature — leur évolution à long terme était totalement inconnue.</div>
    </li>
  </ul>
</div>

<hr class="phd-divider">

<div class="phd-section">
  <span class="section-tag">03 — Approche expérimentale</span>
  <h2>La méthode Flash 3D : un choix décisif</h2>
  <p>La méthode retenue repose sur une <strong>excitation laser locale (CO₂, 130 W, 10 ms)</strong> et une caméra infrarouge haute vitesse (2000 fps) qui enregistre la diffusion thermique 2D en surface. Un estimateur analytique (ENH — Estimation par Normalisation Harmonique) extrait les diffusivités αₓ et αᵧ simultanément, sans hypothèse 1D.</p>
  <div class="img-grid">
    <div class="img-block">
      <!-- Slide 27 → /assets/images/phd/setup-flash3d.png -->
      <!-- <img src="/assets/images/phd/setup-flash3d.png" alt="Dispositif expérimental Flash 3D"> -->
      <div class="img-placeholder">
        <div class="ph-slide">Slide 27 → /assets/images/phd/setup-flash3d.png</div>
        <div>Photo du setup : laser, caméra IR, échantillon, cryothermostat</div>
      </div>
      <figcaption>Dispositif Flash 3D — laser CO₂, caméra IR haute vitesse, cryothermostat.</figcaption>
    </div>
    <div class="img-block">
      <!-- Slide 7 → /assets/images/phd/frittage-process.png -->
      <!-- <img src="/assets/images/phd/frittage-process.png" alt="Procédé de frittage de l'argent"> -->
      <div class="img-placeholder">
        <div class="ph-slide">Slide 7 → /assets/images/phd/frittage-process.png</div>
        <div>Procédé : pâte → dégazage → couches → frittage sous pression</div>
      </div>
      <figcaption>Élaboration — dépôt multicouche, dégazage sous vide, frittage 0–10 MPa @ 270 °C.</figcaption>
    </div>
  </div>
  <p>Une <strong>phase de calibration rigoureuse</strong> sur des matériaux de référence (Al, Cu, Ag massif) a permis d'établir trois paramètres critiques : puissance laser maximale, nombre de trames ≥ 1200, rapport signal/bruit ≥ 5. Résultat : une erreur de mesure inférieure à 6 %.</p>
  <div class="callout">
    <strong>Deux familles d'échantillons :</strong> plaques d'Ag fritté seul (5×5 cm, 0,5–1,4 mm) pour s'affranchir de l'interface, puis bicouches Ag/Cu (Ag 0,12–0,46 mm + Cu 0,1 mm) pour intégrer l'effet d'interface. Frittage de 0 à 10 MPa. Vieillissement sous vide primaire à 150, 250 et 350 °C pendant 50, 200 et 500 h.
  </div>
</div>

<hr class="phd-divider">

<div class="phd-section">
  <span class="section-tag">04 — Résultats : Ag fritté seul</span>
  <h2>Densité → conductivité : une corrélation robuste</h2>
  <p>La pression de frittage est le levier principal : passer de 0 à 10 MPa augmente la densité de <strong>62 %</strong> et la conductivité thermique de <strong>84 %</strong>. Les mesures s'alignent sur les prédictions des modèles à pores sphériques et cylindriques d'Ordonez-Miranda (2016).</p>
  <div class="img-block">
    <!-- Slide 39 → /assets/images/phd/ag-non-vieilli.png -->
    <!-- <img src="/assets/images/phd/ag-non-vieilli.png" alt="Conductivité thermique de l'Ag fritté vs porosité"> -->
    <div class="img-placeholder">
      <div class="ph-slide">Slide 39 → /assets/images/phd/ag-non-vieilli.png</div>
      <div>Graphe λ vs porosité relative — Ag non vieilli, 4 pressions, comparé aux modèles</div>
    </div>
    <figcaption>Conductivité thermique mesurée en fonction de la porosité relative, pour 4 pressions de frittage. Comparaison avec les modèles de pore sphérique, cylindrique et plat (Ordonez-Miranda, 2016).</figcaption>
  </div>

  <h2 style="margin-top:2rem;">Vieillissement : un saut initial rapide, puis stabilisation</h2>
  <p>Le vieillissement thermique révèle une dynamique en deux temps. Dans les <strong>premières 45 minutes</strong> — et non les premières 50 heures comme suggéré dans la littérature — la conductivité fait un saut significatif, particulièrement marqué pour les échantillons fortement densifiés (10 MPa). La <strong>densité, elle, reste parfaitement stable</strong> jusqu'à 500 h à 350 °C.</p>
  <div class="img-grid">
    <div class="img-block">
      <!-- Slide 42 → /assets/images/phd/ag-vieillissement.png -->
      <!-- <img src="/assets/images/phd/ag-vieillissement.png" alt="Évolution λ Ag fritté vieilli"> -->
      <div class="img-placeholder">
        <div class="ph-slide">Slide 42 → /assets/images/phd/ag-vieillissement.png</div>
        <div>Barplot λ (0h / 50h / 200h / 500h) pour 0–10 MPa, 150–350 °C</div>
      </div>
      <figcaption>Évolution de λ pour 0–10 MPa, 150–350 °C, jusqu'à 500 h.</figcaption>
    </div>
    <div class="img-block">
      <!-- Slide 43 → /assets/images/phd/ag-cinetique.png -->
      <!-- <img src="/assets/images/phd/ag-cinetique.png" alt="Cinétique fine vieillissement Ag"> -->
      <div class="img-placeholder">
        <div class="ph-slide">Slide 43 → /assets/images/phd/ag-cinetique.png</div>
        <div>Courbe λ vs temps (intervalles 15 min) — Ag 10 MPa @ 150 °C</div>
      </div>
      <figcaption>Cinétique fine — λ atteint son maximum en ≈ 45 min. La taille des grains (≈ 300 nm) reste inchangée.</figcaption>
    </div>
  </div>
  <div class="callout">
    <strong>Interprétation clé :</strong> l'augmentation initiale de λ n'est pas liée à une densification (ρ = constante) ni à une croissance de grains (stable à ≈ 300 nm). Elle est attribuée à la <strong>relaxation de contraintes résiduelles de compression</strong> générées lors du frittage sous pression — un mécanisme mis en évidence via des mesures de résonance dynamique et corroboré par des études indépendantes (Zuo et al., 2022 ; Agyakwa, 2024).
  </div>
</div>

<hr class="phd-divider">

<div class="phd-section">
  <span class="section-tag">05 — Résultats : bicouches Ag/Cu</span>
  <h2>L'interface change tout à long terme</h2>
  <p>Les bicouches Ag/Cu présentent d'abord le même comportement que l'Ag seul : une hausse de λ dans les 50 premières heures. Puis, <strong>au-delà de 200 h</strong>, une dégradation progressive et significative apparaît — absente dans les échantillons monocouches. La densité globale, elle, reste stable.</p>
  <div class="img-block">
    <!-- Slide 55 → /assets/images/phd/agcu-vieillissement.png -->
    <!-- <img src="/assets/images/phd/agcu-vieillissement.png" alt="Évolution λ bicouche Ag/Cu"> -->
    <div class="img-placeholder">
      <div class="ph-slide">Slide 55 → /assets/images/phd/agcu-vieillissement.png</div>
      <div>Barplot λ Ag/Cu — 0h / 50h / 200h / 500h pour 4 pressions, avec tendance Ag seul superposée</div>
    </div>
    <figcaption>Évolution de la conductivité effective des bicouches Ag/Cu au cours du vieillissement @ 350 °C. La tendance en pointillés représente l'Ag fritté seul (pas de dégradation).</figcaption>
  </div>
  <p>L'analyse microstructurale par MEB révèle une <strong>zone d'interface Ag/Cu à porosité inhomogène</strong> dont l'épaisseur et la microstructure évoluent avec le temps de vieillissement. Aucune nouvelle phase (oxyde, alliage AgₓCuᵧ) n'est détectée par EDS — la dégradation est exclusivement d'origine microstructurale locale.</p>
  <div class="result-pair">
    <div class="result-card">
      <span class="rc-label">Résultat clé — modèle en couches</span>
      <h3>Quantification de la zone affectée</h3>
      <p>Un modèle de contribution en couches (Cu + interface + zone Ag affectée + Ag sain) permet d'estimer l'épaisseur de la zone Ag dégradée. À 500 h @ 350 °C, environ <strong>50 % de la couche d'Ag</strong> est affectée par le vieillissement.</p>
      <span class="finding">~50 % de l'Ag affecté à 500 h</span>
    </div>
    <div class="result-card">
      <span class="rc-label">Résultat clé — limite du modèle</span>
      <h3>Divergence à temps long</h3>
      <p>Le modèle prédit correctement λ jusqu'à 200 h. Au-delà, une <strong>divergence croissante</strong> apparaît, indiquant des phénomènes non capturés : redistribution de porosité en 3D, défauts aux joints de grains, évolution de l'adhésion Ag/Cu.</p>
      <span class="finding">Modèle valide jusqu'à 200 h</span>
    </div>
  </div>
</div>

<hr class="phd-divider">

<div class="phd-section">
  <span class="section-tag">06 — Publications &amp; perspectives</span>
  <h2>Contributions et ouvertures</h2>
  <div class="pub-item">
    <span class="pub-journal">Acta Materialia · 2023</span>
    <strong>A. Sghuri</strong>, Y. Billaud, X. Milhet et al. — <em>Thermal conductivity of porous sintered silver: effect of density and thermal aging.</em>
  </div>
  <div class="pub-item">
    <span class="pub-journal">Conférence SFT · 2021</span>
    <strong>A. Sghuri</strong>, Y. Billaud, X. Milhet — Calibration de la méthode Flash 3D pour matériaux hautement conducteurs (Al, Cu, Ag).
  </div>
  <p style="margin-top:1.5rem;">Les perspectives ouvrent plusieurs directions à fort intérêt industriel : extension aux systèmes <strong>Cu/Ag/Cu et SiC/Ag</strong>, cyclage thermique en conditions représentatives, modélisation 3D de la microstructure incluant défauts aux joints de grains et évolution de l'adhésion interfaciale.</p>
  <h2 style="margin-top:2rem;">Compétences développées</h2>
  <div class="skills-row">
    <span class="skill-chip">Mesure thermique Flash 3D</span>
    <span class="skill-chip">Méthode inverse (ENH)</span>
    <span class="skill-chip">Microscopie MEB + analyse d'images</span>
    <span class="skill-chip">mDSC / calorimétrie modulée</span>
    <span class="skill-chip">Frittage Ag sous pression</span>
    <span class="skill-chip">Vieillissement thermique accéléré</span>
    <span class="skill-chip">Python / traitement données</span>
    <span class="skill-chip">MATLAB / modélisation thermique</span>
    <span class="skill-chip">Rédaction scientifique (EN/FR)</span>
  </div>
</div>

</div>
