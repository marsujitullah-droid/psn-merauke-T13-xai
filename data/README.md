# Dataset T13 — Sampel Blok G dan H

Dihasilkan oleh notebook (`T13_hasil.zip` → `07_dataset/`).

| Berkas | Isi |
|---|---|
| `T13_sampel.csv` | Per blok 1.500 dibuka, 750 hutan stabil, 750 lahan terbuka stabil: `kelas` (1/2/3), `blok`, `lon`, `lat`, 27 fitur |
| `T13_nilai_SHAP.csv` | Nilai SHAP XGBoost (log-odds) setiap titik untuk 27 fitur, `kelas`, `y` (1 dibuka) |
| `T13_semua_ukuran_kepentingan.csv` | Per fitur: SHAP XGBoost, SHAP Random Forest, gain XGBoost, permutasi XGBoost, \|koefisien\| logistik |
| `T13_blokG.geojson`, `T13_blokH.geojson` | Batas blok |

Lisensi CC BY 4.0.

**EN.** Feature samples (27 features), XGBoost SHAP values, five importance measures and block boundaries for Blocks G and H. Class codes: 1 cleared, 2 stable forest, 3 stable open land. Licence CC BY 4.0.
