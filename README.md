# Explainable AI (SHAP) for Land-Clearing Detection in the Merauke PSN Area (T13)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.ANGKA.svg)](https://doi.org/10.5281/zenodo.ANGKA)

Code, data and results for the study *"Explainable AI for Land-Clearing Detection in the Merauke National Strategic Project, Indonesia: Importance, Agreement and Stability of SHAP Explanations"*.

> **Ringkasan (ID):** Repositori ini berisi notebook, sampel, nilai SHAP, dan tabel hasil untuk menjelaskan model deteksi pembukaan lahan (XGBoost, Random Forest, regresi logistik) dengan SHAP di Blok G dan H kawasan PSN Merauke: fitur penentu, kesepakatan dengan ukuran kepentingan lain, stabilitas penjelasan, dan model ringkas. Semua tabel dan gambar tersedia dalam versi Indonesia (_ID) dan Inggris (_EN).

## Study design

| Item | Value |
|---|---|
| Study area | Blocks G and H, 20 × 20 km each, Merauke Regency (next-ranked cells by 2024–2025 Hansen loss after Blocks A–F) |
| Features | 27 in 6 groups: optical state, optical change (2023→2025), radar state, radar change, terrain, texture |
| Labels | Automatic from Hansen + RADD/TMF consensus: cleared, stable forest, stable open land (binary model: cleared vs not) |
| Models | XGBoost (main), Random Forest, logistic regression; 5-fold spatial CV (1 km groups) and G↔H transfer |
| Explanation | SHAP TreeExplainer; agreement with RF SHAP, gain, permutation, \|logistic coefficient\|; Kendall's W across folds; G vs H Spearman |
| Extras | Top-k reduced models; false-positive analysis by source class |

## Main results

Blocks G (140.364° E, 8.413° S; 435.8 ha Hansen loss 2024–2025) and H (140.364° E, 8.232° S; 384.8 ha).

| Item | Result |
|---|---|
| Spatial CV F1 (G / H) | XGBoost 0.806 / 0.815; Random Forest 0.813 / 0.792; logistic regression 0.833 / 0.840 (AUC 0.90–0.93) |
| Transfer F1 G→H / H→G | XGBoost 0.581 / 0.788; logistic regression 0.723 / 0.791 |
| Top SHAP features | G: dNDVI_m, dBSI, elevation, NDVI, dNBR; H: elevation (mean \|SHAP\| 2.22), B2, dNDVI_m, NDVI, VH_sd |
| Group shares | Optical state 31–32%; terrain 15% (G) / 34% (H); radar 11–14% |
| Agreement with other measures | Spearman ρ 0.21–0.77 (lowest: permutation importance) |
| Stability | Across folds Kendall's W 0.79–0.84; G vs H ρ = 0.45 (3 of top 5 shared) |
| Reduced model (top 5) | CV F1 0.813 (27 features: 0.805); transfer 0.630 (vs 0.577) |
| False positives | Mostly stable forest (14.9–23.6%) vs stable open land (1.5–4.1%) |

SHAP reveals reliance on elevation as a contextual cue (cleared land median 14.5–17.4 m vs stable open land 3.4–4.1 m).

## Repository structure

```
notebooks/T13_notebook.ipynb   full pipeline (Google Colab + Earth Engine + XGBoost + SHAP)
data/                          samples, SHAP values, importance measures, block boundaries
results/tables/                result tables and T13_hasil_ringkas.json
results/figures/               figures used in the manuscript
docs/diagrams/                 flowchart, context diagram, level-1 DFD (ID & EN)
```

## License

Code: MIT (`LICENSE`). Data, results and figures: CC BY 4.0.
