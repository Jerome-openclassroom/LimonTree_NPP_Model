```python
# npp_model.py

"""
NPP Model — Lyra Project 2025

This script demonstrates why the Net Primary Production (NPP) is called NET:
It compares the theoretical maximum photosynthesis potential (GPP-like) adjusted
to account for typical autotrophic respiration (via the empirical factor 20 gC/MJ),
with the real production constrained by water availability and a WUE value.

"""

def compute_npp_equationnelle(SF, DO_green, Irradiance, R_photo, k_species):
    P_model_W = DO_green * SF * Irradiance * R_photo * k_species
    P_model_MJ_day = P_model_W * 86400 / 1e6
    NPP_equationnelle = P_model_MJ_day * 20  # Factor includes respiration losses
    return NPP_equationnelle

def compute_npp_wue(conso_eau_L_day, WUE_gC_per_kg):
    NPP_WUE = conso_eau_L_day * WUE_gC_per_kg
    return NPP_WUE

def main():
    SF = 2.31
    DO_green = 0.90 # 90% of the maximum possible green density
    Irradiance = 270
    R_photo = 0.02
    k_species = 1.0
    conso_eau = 2.0
    WUE = 3.5

    npp_eq = compute_npp_equationnelle(SF, DO_green, Irradiance, R_photo, k_species)
    npp_wue = compute_npp_wue(conso_eau, WUE)

    ratio = npp_wue / npp_eq * 100 if npp_eq != 0 else 0

    print("=== NPP Model — Lyra Project 2025 ===")
    print(f"Voie 1 (Equationnelle) : {npp_eq:.2f} gC/j")
    print(f"Voie 2 (WUE)           : {npp_wue:.2f} gC/j")
    print(f"Ratio WUE/Equationnelle: {ratio:.1f} %")
    print("\nFormulas:")
    print("P_model = DO_green × SF × Irradiance × R_photo × k_species")
    print("NPP_WUE = Conso_eau × WUE")

if __name__ == "__main__":
    main()

```

    === NPP Model — Lyra Project 2025 ===
    Voie 1 (Equationnelle) : 19.40 gC/j
    Voie 2 (WUE)           : 7.00 gC/j
    Ratio WUE/Equationnelle: 36.1 %
    
    Formulas:
    P_model = DO_green × SF × Irradiance × R_photo × k_species
    NPP_WUE = Conso_eau × WUE
    


```python

```
