# Global Commodity Shock Analysis

Proyek ini menganalisis pergerakan harga komoditas global pada periode konflik Iran-Amerika Serikat 2026 dan hubungannya dengan Consumer Confidence Indonesia. Komoditas yang digunakan adalah Brent oil, natural gas, dan gold.

## Anggota Kelompok

| Nama | NIM |
|---|---|
| DANAR FATHURAHMAN | 24/538200/PA/22828 |
| FAHMI ABDILLAH ZAIN | 24/539422/PA/22904 |
| MUHAMMAD DHAFIN ALFEIZAR GANDHANG | 24/539735/PA/22916 |
| SATYA WIRA PRAMUDITA | 24/543649/PA/23102 |
| AJIE ARMANSYAH SUNARYO | 24/545286/PA/23170 |

## Tujuan

Tujuan proyek ini adalah melihat seberapa besar harga komoditas aktual tahun 2026 menyimpang dari baseline historis. Penyimpangan tersebut disebut `prediction gap` dan digunakan sebagai indikasi adanya shock pasar.

## Metode

Model utama yang digunakan adalah **ARIMA time series model**. Model dilatih memakai data bulanan sampai Desember 2025, lalu digunakan untuk membuat forecast periode 2026.

Rumus gap yang digunakan:

```text
Prediction Gap = Actual Value - ARIMA Forecast
```

Gap positif berarti harga aktual lebih tinggi dari forecast ARIMA. Hasil ini tidak digunakan untuk membuktikan kausalitas langsung, tetapi hanya untuk melihat indikasi pergerakan abnormal.

## Dataset

Dataset yang digunakan:

- Brent crude oil price
- Henry Hub natural gas price
- Gold price
- Indonesia Consumer Confidence Index proxy

## File Utama

- `global_commodity.ipynb`: notebook utama analisis
- `data/`: dataset mentah dan hasil olahan
- `figures/`: grafik untuk laporan dan infographic
- `outputs/`: hasil model, prediction gap, dan ringkasan insight
- `COPYWRITING.md`: teks singkat untuk infographic

## Output ARIMA

Output utama ARIMA disimpan dengan suffix `_arima`, contohnya:

- `figures/actual_vs_predicted_arima.png`
- `figures/prediction_gap_percent_arima.png`
- `figures/global_commodity_shock_index_arima.png`
- `outputs/shock_gap_2026_arima.csv`
- `outputs/model_metrics_arima.csv`
- `outputs/insight_summary_arima.txt`

## Cara Menjalankan

Install dependency dan jalankan notebook:

```bash
uv sync
./.venv/bin/jupyter notebook global_commodity.ipynb
```

Notebook juga bisa dieksekusi ulang dari terminal:

```bash
./.venv/bin/jupyter nbconvert --to notebook --execute --inplace global_commodity.ipynb
```

## Catatan

Analisis ini memakai ARIMA sebagai baseline sederhana untuk data time series bulanan. Prediction gap menunjukkan deviasi dari baseline, bukan bukti bahwa konflik menjadi satu-satunya penyebab perubahan harga komoditas.
