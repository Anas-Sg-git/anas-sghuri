---
title: "Quantification de l'épaisseur d'interface par traitement d'images MEB"
excerpt: "Développement d'une méthode de segmentation d'images de microscopie pour quantifier l'évolution locale de la porosité et estimer l'épaisseur d'une zone d'interface dans un matériau bicouche."
collection: portfolio
---


Développement d'une méthode de segmentation d'images de microscopie 
pour quantifier l'évolution locale de la porosité et estimer 
l'épaisseur d'une zone d'interface dans un matériau bicouche.

- **Contexte :** travaux de thèse · Institut Pprime · Université de Poitiers
- **Outils :** MATLAB, ImageJ, MEB / MEB-FEG
- **Domaine :** analyse d'images, microstructure, quantification

---

## Le problème

Dans les échantillons bicouches Ag/Cu étudiés au cours de la 
thèse, les mesures de conductivité thermique montrent une 
dégradation progressive au-delà de 200 h de vieillissement, 
alors que la densité globale de l'échantillon reste constante. 
Ce paradoxe suggère que les propriétés changent **localement**, 
à une échelle que les mesures macroscopiques ne capturent pas.

L'observation des sections transversales par MEB confirme 
cette hypothèse : au voisinage du contact entre l'Ag et le Cu, 
une zone d'interface à porosité variable est visible. Mais 
cette observation reste qualitative. Pour aller plus loin, il 
fallait répondre à deux questions concrètes :

- **Quelle est l'épaisseur de cette zone d'interface ?**
- **Comment la porosité de cette zone évolue-t-elle au cours 
  du vieillissement ?**

Aucune méthode standard ne permet de répondre à ces questions 
sur ce type d'images. Il a donc fallu en développer une.

## Observation préalable : une microstructure hétérogène

Avant de quantifier l'interface, une première analyse des 
images MEB a révélé que la microstructure de la couche d'Ag 
n'est pas homogène latéralement. On observe une alternance 
de **zones denses** (LPA — Less Porous Area, ~55 % de la 
surface) et de **zones poreuses** (HPA — Highly Porous Area), 
probablement liée au dégazage du dispersant et du liant 
lors du frittage.

<!-- IMAGE SLIDE 2 : vue d'ensemble LPA/HPA -->
<img src="{{ '/images/portfolio-interface-zones-lpa-hpa.png' | relative_url }}" 
     alt="Zones LPA et HPA dans un échantillon Ag/Cu" 
     style="display: block; width: 100%; max-width: 700px; height: auto; margin: 0 auto;">

*Section transversale d'un échantillon Ag/Cu fritté à 10 MPa. 
On distingue une zone dense (LPA) et une zone poreuse (HPA) 
au sein de la couche d'Ag.*

Cette hétérogénéité implique qu'une seule image n'est pas 
représentative de l'ensemble de l'échantillon. Pour chaque 
condition de vieillissement, plusieurs images ont donc été 
acquises dans chaque type de zone (LPA et HPA), afin 
d'obtenir des mesures statistiquement significatives.

Le suivi visuel des images à 0, 50, 200 et 500 h de 
vieillissement montre qualitativement une évolution de la 
porosité apparente, à la fois dans la zone Ag et au 
voisinage de l'interface avec le Cu.

<!-- IMAGE SLIDE 3 : comparaison 4 temps -->
<img src="{{ '/images/portfolio-interface-evolution-vieillissement.png' | relative_url }}" 
     alt="Évolution microstructurale au cours du vieillissement" 
     style="display: block; width: 100%; max-width: 700px; height: auto; margin: 0 auto;">

*Évolution de la microstructure à l'interface Ag/Cu au cours du 
vieillissement (0, 50, 200 et 500 h à 350 °C), dans les zones 
denses (LPA, en haut) et poreuses (HPA, en bas). Échantillon 
fritté à 10 MPa.*

## La méthode développée

Pour passer de l'observation qualitative à une mesure 
quantitative, une méthode de segmentation a été développée 
sous MATLAB. Le principe repose sur trois étapes successives 
appliquées à chaque image MEB de section transversale.

### Étape 1 — Binarisation

L'image MEB brute (niveaux de gris) est convertie en image 
binaire par seuillage : les pixels correspondant aux pores 
deviennent noirs, le reste devient blanc. Cette étape, 
réalisée après calibration du seuil sur des images de 
référence, permet de quantifier la fraction de pores 
pour chaque pixel de l'image.

### Étape 2 — Construction de l'image cumulative

Pour chaque ligne horizontale de l'image binarisée, le 
nombre de pixels noirs (pores) est compté. Une nouvelle 
image est alors construite : pour chaque ligne, les pixels 
noirs sont alignés à droite, proportionnellement au nombre 
de pores détectés. Cette représentation cumulative traduit 
la **distribution de porosité en fonction de la profondeur** 
dans l'échantillon.

Le profil obtenu fait apparaître une frontière irrégulière 
entre la zone blanche (Ag dense) et la zone noire (pores 
accumulés). La forme de cette frontière encode l'information 
sur la répartition spatiale de la porosité à travers 
l'épaisseur de l'échantillon.

### Étape 3 — Détermination de l'épaisseur d'interface

L'épaisseur de la zone d'interface est estimée à partir 
de l'image cumulative en identifiant deux limites :

- La **limite inférieure** correspond au point de contact 
  Ag/Cu : c'est le dernier pixel noir en partant du bas 
  de l'image cumulative, là où la porosité de l'Ag 
  rencontre le Cu dense.
- La **limite supérieure** est estimée à partir de la 
  valeur moyenne de la distribution de porosité : elle 
  marque la transition entre la zone d'interface (où la 
  porosité s'écarte du comportement moyen de l'Ag) et 
  la zone d'Ag à porosité homogène.

La distance en pixels entre ces deux limites, convertie 
en micromètres via le facteur d'échelle de l'image MEB, 
donne l'épaisseur de la zone d'interface.

<!-- IMAGE SLIDE 10 : triptyque final -->
<img src="{{ '/images/portfolio-interface-methode-complete.png' | relative_url }}" 
     alt="Méthode complète de segmentation" 
     style="display: block; width: 100%; max-width: 700px; height: auto; margin: 0 auto;">

*Pipeline complet : image MEB brute (gauche), image binarisée 
(centre), image cumulative avec profil de porosité et 
épaisseur d'interface identifiée (droite). La zone entre 
les deux lignes rouges correspond à l'interface Ag/Cu.*

## Implémentation

La méthode a été implémentée en MATLAB. Le traitement 
d'une image se déroule de manière séquentielle :

1. Chargement de l'image MEB binarisée.
2. Comptage des pixels noirs (pores) pour chaque ligne 
   horizontale.
3. Construction de l'image cumulative par redistribution 
   des pixels noirs.
4. Calcul de la distance moyenne de porosité (ligne 
   moyenne).
5. Identification du dernier point de contact avec le Cu 
   (limite inférieure).
6. Estimation de la limite supérieure par comparaison 
   avec la moyenne.
7. Calcul de l'épaisseur en pixels, puis conversion 
   en micromètres.

Ce traitement est appliqué de manière identique à toutes 
les images, pour chaque condition de vieillissement et 
chaque zone (LPA, HPA), ce qui garantit la comparabilité 
des résultats.
```matlab
% Charger l'image binarisée
brut_2 = imread(selectedfile);
[ligne, colonne] = size(brut_2);

% Compter les pores ligne par ligne
cumul_pores_ligne = zeros(ligne, 1);
for l = 1:ligne
    cumul_pores_ligne(l) = sum(brut_2(l, :) == 0);
end

% Construire l'image cumulative
image_cumul = ones(ligne, colonne) * 255;
for lig = 1:ligne
    for pore = 1:cumul_pores_ligne(lig)
        image_cumul(lig, pore) = 0;
    end
end

% Calculer la distance moyenne de porosité par ligne
distance_ligne = zeros(ligne, 1);
for l = 1:ligne
    distance_ligne(l) = sum(image_cumul(l, :) == 0);
end

% Déterminer l'épaisseur de l'interface
mean_distance = round(mean(distance_ligne));
dernier_point = find(image_cumul(:, colonne) == 0, 1);
epaisseur = dernier_point - mean_distance;
```

## Résultats

La méthode a été appliquée systématiquement aux échantillons 
frittés à 10 MPa, vieillis à 350 °C pour des durées de 0, 
50, 200 et 500 h. Pour chaque condition, le taux de porosité 
en surface (TPS) a été mesuré séparément dans la zone Ag 
(au-dessus de l'interface) et dans la zone d'interface 
(entre la limite supérieure et le contact Ag/Cu).

Les résultats mettent en évidence deux dynamiques opposées. 
À l'interface, le TPS chute fortement après 50 h de 
vieillissement (de ~39 % à ~7 %), indiquant une densification 
locale rapide, puis se stabilise autour de ~20 %. En zone 
Ag, le TPS augmente progressivement au cours du vieillissement, 
passant de ~11 % à ~46 % après 500 h.

Ces évolutions opposées expliquent un résultat central de la 
thèse : la densité **globale** de l'échantillon reste constante 
au cours du vieillissement, alors que les propriétés 
**locales** évoluent de manière significative. Sans cette 
méthode de segmentation, ce phénomène serait resté invisible.

<!-- IMAGE SLIDE 11 : graphique TPS -->
<img src="{{ '/images/portfolio-interface-tps-evolution.png' | relative_url }}" 
     alt="Évolution du TPS au cours du vieillissement" 
     style="display: block; width: 100%; max-width: 600px; height: auto; margin: 0 auto;">

*Évolution du taux de porosité en surface (TPS) en zone Ag 
et en zone d'interface au cours du vieillissement à 350 °C. 
Les bandes ombrées représentent les écarts-types.*

## Ce que cette méthode a permis

Les mesures de TPS obtenues par cette méthode ont ensuite 
alimenté une chaîne d'estimation reliant la porosité locale 
à la densité locale, puis la densité à la conductivité 
thermique. C'est cette chaîne qui a permis d'estimer qu'à 
500 h de vieillissement, environ **50 % de l'épaisseur de la 
couche d'Ag** est affectée, et de proposer un modèle en 
couches (Cu / interface / zone Ag affectée / Ag sain) pour 
décrire l'évolution de la conductivité thermique du système.

---

**Compétences mobilisées :**

<div style="display: flex; flex-wrap: wrap; gap: 0.5em; margin-top: 0.5em;">
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Traitement d'images</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Segmentation et binarisation</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">MATLAB</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Microscopie MEB</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Analyse quantitative de microstructures</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Préparation métallographique</span>
  <span style="background: #eaf2f8; padding: 0.4em 0.8em; border-radius: 5px; font-size: 0.9em;">Développement méthodologique</span>
</div>
