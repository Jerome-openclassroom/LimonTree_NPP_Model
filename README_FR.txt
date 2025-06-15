# ✅ README – Suivi hydrique et modélisation de la production primaire nette (NPP) d’un citronnier en pot. Validation d'usage d'un appareil de mesure de l'humidité du sol "grand public".

## 📌 Contexte

Ce projet démontre un suivi cohérent de la consommation d’eau et de la productivité d’un citronnier cultivé en pot, en climat méditerranéen, avec :

* Capteur capacitif sans pile (grand public) calibré,
* Sonde Watermark pour la tension racinaire,
* Psychromètre pour microclimat et abaque interactif,
* Images pour validation géométrique par LLM,
* Données climatiques (Global Solar Atlas).

## 🌿 Dispositif expérimental

* Pot cylindrique : 50 cm Ø, 40 cm hauteur (\~78.5 L de substrat).
* Substrat : terreau + terre de bruyère, légèrement acide.
* Houppier : modélisé en double faisceau (géométrie + comptage feuilles), surface foliaire totale \~2.31 m².
* Capteur capacitif (10€) : suivi pratique (plage fiable 50–90%).
* Sonde Watermark à 21 cm : tension racinaire réelle (ressuyage = \~10 cb).
* Psychromètre : HR et T mesurées, comparées aux stations, abaque : [https://hvac-eng.com/fr/tableau-psychrom%C3%A9trique-interactif/](https://hvac-eng.com/fr/tableau-psychrom%C3%A9trique-interactif/).
* Irradiance indirecte : [https://globalsolaratlas.info/map?s=43.949249,4.805901\&m=site\&c=43.957484,4.645844,11](https://globalsolaratlas.info/map?s=43.949249,4.805901&m=site&c=43.957484,4.645844,11).

## 🌿 Méthodologie 

Calcul de la surface foliaire et de la teneur en chlorophylle : 

10 feuilles représentatives des dimensions foliaires ont été prélevées : 
1 groupe de 5 feuilles de tailles croissantes, de couleur vert clair, représentatives de la distribution des surfaces individuelles.
1 groupe de 5 feuilles de tailles croissantes, de couleur vert plus foncé, représentatives de la distribution des surfaces individuelles.
La surface foliaire moyenne pour les 10 feuilles a été calculée grâce à Mesurim.

Dans chaque sous groupe de 5 feuilles, 4 Mesures SPAD ont été effectuées pour chaque feuille, puis une moyenne des 20 mesures a été effectuée. 
Un mesure de la densité de vert moyenne a également été calculée pour chaque sous groupe.

2 faisceaux de données ont ensuite été préparés :

1er faisceau : comptage du nombre de feuilles pour 2 branches types avec leurs rameaux, calcul d'une valeur moyenne, puis comptage du nombre total de branches et multiplication. Le nombre estimé de feuille est ensuite multiplié par la surface moyenne pour obtenir la surface foliaire totale de la plante. Données : 1m40 X 1m30 et hauteur 1m20, 20 à 44 feuilles comptées par branche (moyenne 32) , 24 branches au total.

2eme faisceau : 3 mesures des dimensions du houppier ont été réalisées : 2 mesures dans le plan horizontal et une mesure verticale, et 2 photos ont été prises : en vue plongeante et latérale, ceci permettant une évaluation croisée avec l'estimation du LLM (GPT4o).

Paramètres climatiques : 
Mesures effectuées à l'aide d'un psychromètre, permettant l'évaluation régulière de la température et RH, avec comparaisons régulière aux données météo France, Infoclimat et Météociel.
Mise en évidence de différences intermittentes attribuables à un effet de microclimat (ombrage 90% du temps, micro évaporation locale...).


Suivi de la teneur en eau du substrat :

Après arrosage et ressuyage initial, la tension superficielle de l'eau du substrat a été suivie jusqu'à la valeur limite de la RFU estimée à 60 centibars, soit pendant une durée de 2.5 jours.
En parallèle, des mesures capacitives étaient effectuées à l'aide de l'appareil "grand public".

L'ETP locale a été calculé sur le bases des mesures locale (psychromètre) et des données météorologique (pression) et d'irradiance solaire globale.

A 60 cbars, un arrosage a été effectué à l'aide d'une petite quantité d'eau, 5 L ont permis une reconstitution des réserves (capteur capacitif : 100% , sonde Watermark : 10 cbars), sans signes de ressuyage (pas de pertes d'eau au pied du pot).

## 🌿 Résultats :

SPAD moyen (clair)	32.6
SPAD moyen (foncé)	56.1
DO verte (ImageJ, moyenne)	≈ 431.07 (clair), ≈ 457.12 (foncé)
Dimensions houppier	1.40 × 1.30 m, hauteur 1.20 m
Nombre estimé de feuilles	≈ 768 feuilles
Surface foliaire moyenne	≈ 30.14 cm²
Surface foliaire totale (estimation extrapolée)	2.31 m²


## 🧮 Modèle NPP

**Formule équationnelle (Voie 1)**
P\_model = DO\_green × Surface\_foliaire × Irradiance × R\_photo × k\_species (=1)
\= 0.90 × 2.31 × 270 × 0.02 ≈ 11.3 W = 0.488 MJ/j = 19.5 gC/j.

**ETP et réserve (Voie 2)**
ETP Penman pour surface foliaire + substrat : 7.28 L/j.
Réserve reconstituée : 5 L/2.5 j = 2 L/j réel.
NPP ajustée : 19.5 × (2/7.28) ≈ 5.4 gC/j.

**Bilan photosynthèse & WUE (Voie 3)**
Consommation réelle : 2 L/j = 2 kg H₂O.
WUE C3 typique : 3.5 gC/kg ➜ 2 × 3.5 = 7 gC/j.
Conversion photosynthèse → cellulose valide la cohérence.

## ✅ Résultats croisés

| Voie   | Méthode              | NPP estimée |
| ------ | -------------------- | ----------- |
| Voie 1 | Modèle équationnel   | \~19.5 gC/j |
| Voie 2 | ETP réelle vs Penman | \~5.4 gC/j  |
| Voie 3 | Bilan H₂O – WUE      | \~7 gC/j    |


Pour aligner la NPP équationnelle (19,5 gC/j) avec les conditions réelles, multipliez-la par le rapport de l'ETP réelle (2 L/j) à l'ETP Penman (7,28 L/j), soit 2/7,28 ≈ 0,2747, ce qui donne une NPP ajustée d’environ 5,4 gC/j, cohérente avec les données observées.

## 💧 Recommandations pratiques

* Capteur capacitif fiable pour potager et micro-parcelle (5–20 cm de profondeur racinaire).
* En verger amateur : limite car racines explorent 30–60 cm ➜ préférer Watermark multi-profondeur + dendromètre.

## 🗂️ Arborescence

```
📂 /
├── 📄 README.md               # Ton README final complet
│
├── 📂 data/
│   ├── datas_limon_tree_june2025.txt   # Journal Watermark + climat
│   ├── mesures_limon_tree_june2025.txt # Surfaces, DO, SPAD
│
├── 📂 photos/
│   ├── scan_feuilles.jpg       #  scan à plat (ex: scan_05.jpg)
│   ├── vue_plongeante.jpg      # Photo du houppier en vue du dessus
│   ├── vue_latérale.jpg        # Photo du houppier en profil
│   ├── panneau_psychrometre.jpg  # Panneau d’ombrage
│   ├── psychrometre.jpg        # Vue du psychromètre suspendu
│   ├── capteur_capacitif.jpg   # Vue du capteur capacitif en place
│   ├── Watermark_1.jpg         # Vue sonde Watermark 1 (profondeur)
│   ├── Watermark_2.jpg         # Vue sonde Watermark 2 (si tu as un double point)
│
├── 📂 scripts/   
│   ├── npp_model.md # Script in python for NPP calculation
```

## 🔗 Liens

* [Global Solar Atlas – Avignon](https://globalsolaratlas.info/map?s=43.949249,4.805901&m=site&c=43.957484,4.645844,11)
* [Abaque psychrométrique](https://hvac-eng.com/fr/tableau-psychrom%C3%A9trique-interactif/)
* [Météo France](https://meteofrance.com/)
* [Infoclimat](https://www.infoclimat.fr/)
* [Météociel](https://www.meteociel.fr/)

## 👤 Auteur

**Jérôme — Lyra Project 2025**
Licence : Open Science, usage pédagogique et reproductible.
