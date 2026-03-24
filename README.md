# Automated Detection of Brugada Syndrome from 12-Lead ECG  
**NAFAS SQUAD — IDSC 2026**

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> Interpretable Machine Learning pipeline for early detection of Brugada Syndrome using 12-lead ECG signals with **SHAP explainability**.

### 📋 Abstract
Brugada Syndrome (BrS) is a rare but life-threatening cardiac condition characterized by distinctive coved-type ST-segment elevation in the right precordial leads (V1–V3). This project presents a fully reproducible, clinically interpretable ML pipeline that achieves **AUC-ROC 0.7845** and **sensitivity 0.50** on the Brugada-HUCA (PhysioNet) dataset.

### 👥 Team
- **Asfa Salsabilla Sucipto** (23-007)  
- **Nania Azzahra**  
**NAFAS SQUAD** — Universitas Singaperbangsa Karawang (UNSIKA)

**Submitted:** 25 March 2026  
**Competition:** International Data Science Challenge (IDSC) 2026 — “Mathematics for Hope in Healthcare”

---

### 📊 Dataset
- **Brugada-HUCA (PhysioNet)** — version 1.0.0  
- 363 subjects (364 ECG recordings)  
- 69 Confirmed Brugada (Class 1)  
- 287 Healthy Controls (Class 0)  
- 7 Atypical cases (excluded)  
- Sampling rate: 100 Hz, 12 seconds per record  
- 12-lead ECG in WFDB format

**Link**: [Brugada-HUCA on PhysioNet](https://doi.org/10.13026/q7m3-1g44)

---

### 🛠️ Features
- **65 hand-crafted clinical features** across all 12 leads:
  - Statistical (mean, std, max, min) → 48 features
  - Heart Rate Variability (HR, RR, RMSSD, etc.) → 5 features
  - ST-segment elevation (V1–V3) → 3 features
  - T-wave morphology (mean + inverted flag) → 6 features
  - QRS width (V1–V3) → 3 features

### 📈 Model Performance (Test Set)

| Model          | AUC-ROC | F1-Score | Sensitivity | Specificity | Accuracy |
|----------------|---------|----------|-------------|-------------|----------|
| Random Forest  | **0.7845** | 0.5185  | **0.5000** | 0.8966     | 0.8194  |
| XGBoost        | 0.7463  | 0.4615  | 0.4286     | 0.9138     | 0.7778  |

**5-Fold CV** (Random Forest): AUC-ROC = 0.8427 ± 0.0715

---

### 🔍 Interpretability (SHAP)
- SHAP TreeExplainer on Random Forest
- Top contributing feature: **`t_mean_V2`** (T-wave amplitude in lead V2)
- Waterfall plots show exact contribution of each ECG measurement per patient
- All predictions are traceable to clinically known Brugada markers (ST elevation & T-wave inversion in V1–V3)

---

### 🚀 How to Run

#### 1. Clone repo
```bash
git clone https://github.com/yourusername/Brugada-ECG-NAFAS.git
cd Brugada-ECG-NAFAS
