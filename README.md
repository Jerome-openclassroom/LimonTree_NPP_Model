
# ✅ Water monitoring and Net Primary Production (NPP) modeling for a potted lemon tree. Validation of a low-cost soil moisture sensor.

## 📌 Context

This project demonstrates a consistent monitoring of water consumption and productivity for a lemon tree grown in a pot under a Mediterranean climate, using:

* A battery-free low-cost capacitive soil moisture sensor (calibrated),
* A Watermark sensor for root tension monitoring,
* A psychrometer for microclimate measurement and an interactive psychrometric chart,
* Images for geometric validation with an LLM,
* Climate data (Global Solar Atlas).

## 🌿 Experimental Setup

* Cylindrical pot: 50 cm diameter, 40 cm height (~78.5 L substrate).
* Substrate: potting soil + heath soil, slightly acidic.
* Canopy: modeled with a double data stream (geometry + leaf count), total leaf area ~2.31 m².
* Capacitive sensor (~10€): practical monitoring (reliable range 50–90%).
* Watermark sensor at 21 cm depth: real root tension (drainage = ~10 cb).
* Psychrometer: HR and T measured, compared with weather stations, chart: [Interactive psychrometric chart](https://hvac-eng.com/fr/tableau-psychrom%C3%A9trique-interactif/).
* Indirect irradiance: [Global Solar Atlas](https://globalsolaratlas.info/map?s=43.949249,4.805901&m=site&c=43.957484,4.645844,11).

## 🌿 Methodology

**Leaf area and chlorophyll content:**

10 representative leaves were sampled:  
1 group of 5 light green leaves of increasing sizes, representative of the distribution of individual leaf areas.  
1 group of 5 darker green leaves, similarly distributed.  
The average leaf area for the 10 leaves was measured using Mesurim.

In each subgroup of 5 leaves, 4 SPAD measurements were taken per leaf, then averaged (20 measurements total).  
A mean green density (DO) was also calculated for each subgroup.

**Two data streams were then prepared:**

1st stream: counted the number of leaves on 2 representative branches with their twigs, calculated a mean, then extrapolated to the total number of branches. The estimated leaf number was multiplied by the average leaf area to get the total leaf area. Data: 1.40 m x 1.30 m canopy, height 1.20 m, 20–44 leaves per branch (average 32), 24 branches total.

2nd stream: 3 measurements of the canopy dimensions: 2 in the horizontal plane and 1 vertical. 2 photos were taken: top-down and lateral views, allowing cross-checking with LLM estimation (GPT-4o).

**Climate parameters:**  
Measurements taken with a psychrometer for regular temperature and RH checks, compared with Météo France, Infoclimat, and Météociel data. Microclimate effects identified (shade 90% of the time, local micro-evaporation, etc.).

**Soil moisture tracking:**

After watering and initial drainage, root zone tension was monitored until reaching the RFU limit estimated at 60 centibars over 2.5 days. In parallel, capacitive measurements were taken with the low-cost device.

Local ETP was calculated using local psychrometer measurements plus weather pressure and global solar irradiance data.

At 60 cb, a small watering (5 L) was applied to refill reserves (capacitive sensor: 100%, Watermark sensor: 10 cb), with no visible drainage (no water loss at the pot base).

## 🌿 Results:

| Parameter | Value |
|-----------|-------|
| Mean SPAD (light leaves) | 32.6 |
| Mean SPAD (dark leaves) | 56.1 |
| Green Optical Density (ImageJ, avg.) | ~431.07 (light), ~457.12 (dark) |
| Canopy dimensions | 1.40 × 1.30 m, height 1.20 m |
| Estimated number of leaves | ~768 leaves |
| Average leaf area | ~30.14 cm² |
| Total leaf area (extrapolated) | 2.31 m² |

## 🧮 NPP Model

**Equation-based (Path 1)**  
P_model = DO_green × Leaf_Area × Irradiance × R_photo × k_species (=1)  
= 0.90 × 2.31 × 270 × 0.02 ≈ 11.3 W = 0.488 MJ/day = 19.5 gC/day

**ETP and reserve (Path 2)**  
Penman ETP for leaf area + substrate: 7.28 L/day.  
Replenished reserve: 5 L over 2.5 days = 2 L/day actual.  
Adjusted NPP: 19.5 × (2/7.28) ≈ 5.4 gC/day.

**Photosynthesis & WUE balance (Path 3)**  
Actual water use: 2 L/day = 2 kg H₂O.  
Typical C3 WUE: 3.5 gC/kg → 2 × 3.5 = 7 gC/day.  
Photosynthesis → cellulose conversion confirms coherence.

## ✅ Cross-checked results

| Path | Method | Estimated NPP |
|------|--------|----------------|
| Path 1 | Equation-based | ~19.5 gC/day |
| Path 2 | Actual ETP vs Penman | ~5.4 gC/day |
| Path 3 | H₂O balance – WUE | ~7 gC/day |

To align the equation-based NPP (19.5 gC/j) with real conditions, multiply it by the ratio of actual ETP (2 L/j) to Penman ETP (7.28 L/j), i.e., 2/7.28 ≈ 0.2747, yielding an adjusted NPP of ~5.4 gC/j, consistent with observed data

## 💧 Practical recommendations

* Capacitive sensor reliable for vegetable gardens and micro-plots (root depth 5–20 cm).
* For hobby orchards: limitation due to deeper roots (30–60 cm) → prefer multi-depth Watermark + dendrometer.

## 📎 Addendum — Microscopic View of Leaf Stomatal Openings (Pedagogical Illustration)

As an educational complement, a microscope image of the lower epidermis of a leaf is included.  
This image was captured using the same optical microscope, calibrated with millimeter paper at **X40 magnification**, using digiscopy with a digital camera.

**How to interpret this image:**  
What you see are tiny, scattered openings on the lower leaf surface — these are **the external view of stomatal pores**, appearing as micro-holes in the epidermis. They mark the sites where CO₂ enters and O₂/H₂O exit, driving the gas exchange mechanisms studied in the NPP model.

Unlike stained histological sections, this direct surface view shows stomata as they appear naturally under reflected or transmitted light, without chemical clearing.

**Measurement:**  
Using ImageJ and the established scale, six of these pores were measured:
- **Mean apparent diameter:** 30 µm  
- **Standard deviation:** ± 3 µm

This confirms that the modeled gas fluxes are rooted in real, visible epidermal microstructures.


## 🗂️ Structure

```plaintext
/ (root)
├── README.md               # Full project description
├── README_FR.md               # French version
├── /data/
│   ├── datas_limon_tree_june2025.txt   # Watermark log + climate
│   ├── mesures_limon_tree_june2025.txt # Leaf area, DO, SPAD
├── /photos/
│   ├── scan_feuilles.jpg
│   ├── top_view.jpg
│   ├── side_view.jpg
│   ├── shading_panel.jpg
│   ├── psychrometer.jpg
│   ├── capacitive_sensor.jpg
│   ├── Watermark_1.jpg
│   ├── Watermark_2.jpg
    ├── X40.jpg #grid for microscope calibration at X40
    ├── stomates.jpg
├── /scripts/
│   ├── npp_model.py # Python script for NPP calculations
```

## 🔗 Links

* [Global Solar Atlas – Avignon](https://globalsolaratlas.info/map?s=43.949249,4.805901&m=site&c=43.957484,4.645844,11)
* [Interactive Psychrometric Chart](https://hvac-eng.com/fr/tableau-psychrom%C3%A9trique-interactif/)
* [Météo France](https://meteofrance.com/)
* [Infoclimat](https://www.infoclimat.fr/)
* [Météociel](https://www.meteociel.fr/)

🔗 **Related project**:  
## 🔗 Part of the Lyra Ecosystem

- [Lyra_Leaf_SPAD_Calibration](https://github.com/Jerome-openclassroom/Lyra_Leaf_SPAD_Calibration) – SPAD sensor calibration for estimating chlorophyll density in leaves.
- [TurbiditySensor_OpenScience](https://github.com/Jerome-openclassroom/TurbiditySensor_OpenScience) – Optical-based estimation of aquatic turbidity and primary productivity using open-source sensors.
- [Leaf_Chlorose_CNN_Training](https://github.com/Jerome-openclassroom/Leaf_Chlorose_CNN_Training) – CNN-based classification of chlorotic vs. healthy leaves from scanned images.
- [Lyra_DO_Green_Mesurim](https://github.com/Jerome-openclassroom/Lyra_DO_Green_Mesurim) - A low-tech protocol combining MesurimPro and ImageJ to estimate chlorophyll levels from scanned leaves, with validation against SPAD readings and AI-assisted correlation analysis.
- [AI_Assisted_Lake_Ecology](https://github.com/Jerome-openclassroom/AI_Assisted_Lake_Ecology) – A full-scale NPP model combining field measurements, physical modeling, and GPT-4o-assisted ecological interpretation. Includes empirical correction for realistic annual productivity in clear lakes.
- [Lyra_LowCost_Soil_Leaf](https://github.com/Jerome-openclassroom/Lyra_LowCost_Soil_Leaf) – Integrated low-cost soil and leaf model for terrestrial primary productivity.
  
## 👤 Author

**Jérôme — Lyra Project 2025**  
License: Open Science, for educational and reproducible use.
