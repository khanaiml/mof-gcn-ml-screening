<div align="center">

# Physics-Informed Machine Learning Screening and Validation of MOF/g-C₃N₄ Heterojunction Photocatalysts

[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.cjph.2026.07.025-36454F?style=flat-square)](https://doi.org/10.1016/j.cjph.2026.07.025)
[![Journal](https://img.shields.io/badge/Chinese_Journal_of_Physics-Q1_·_IF_5.3-36454F?style=flat-square)](https://doi.org/10.1016/j.cjph.2026.07.025)
[![License](https://img.shields.io/badge/License-MIT-36454F?style=flat-square)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.9+-36454F?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)

**Abdullah Khan**, Muhammad Saeed, Fakhrud Din*, Farhat Ullah, Sami Ullah*

*University of Malakand · KFUPM (Saudi Arabia) · Bahrain Polytechnic*

Published in the **Chinese Journal of Physics** — Q1 (Physics, Multidisciplinary) · Impact Factor 5.3 · CiteScore 7.9

</div>

---

## Overview

Screening the 20,000+ known MOF/g-C₃N₄ heterojunction candidates for photocatalytic
water splitting via DFT would cost **>10⁷ CPU-hours**. This work bypasses that
bottleneck with **physics-informed machine learning**: six interpretable descriptors
derived from Sanderson electronegativity theory and Butler–Mulliken band alignment,
computed directly from composition — no per-structure quantum calculations.

**Pipeline:** QMOF + CoRE-MOF integration (20,152 structures) → physics-informed
feature engineering → Random Forest + XGBoost consensus ensemble → SHAP
interpretability → hybrid Physics–ML screening cascade

<div align="center">
<img src="results/volcano_plot_filtered.png" width="70%" alt="Screening criteria volcano plot">
</div>

## Key Results

| Metric | Value |
|---|---|
| ROC-AUC (consensus ensemble, 4,029-structure test set) | **0.912** |
| Top-50 screening precision (hybrid cascade) | **98%** |
| External validation — family-level recall (11 closed-shell families) | **100%** |
| External validation — precision | **85.7%** |
| Accuracy lift vs. physics-rule baselines | **+27.6 pp** (McNemar *p* = 0.004) |
| Candidates: 20,152 → | **983** high-confidence |
| Computational cost reduction vs. exhaustive HSE06 | **~20.5×** |

**Validated against experiment:** correctly identifies MOF-5, UiO-66, NU-1000,
NH₂-MIL-53(Al) as compatible (P = 0.75–0.99); correctly rejects ZIF-8 and Cu-BTC.

## Design Rules (SHAP Analysis)

Explainable AI analysis identified **metal ionic radius** and **linker
π-conjugation** as the dominant compatibility factors, yielding actionable
synthesis guidance:

- **Metal nodes:** Ti / Zr / Fe (ionic radius 60–75 pm) — optimal band alignment + stability
- **Frameworks:** high-stability aluminum-halide families
- **Linkers:** electron-donating aromatics (C/H = 1.2–1.5, π-conjugation > 0.45); –NH₂ / –OH functionalization red-shifts absorption 0.3–0.7 eV
- **Porosity:** pore limiting diameter > 3.5 Å

<div align="center">
<img src="results/random_forest_shap_summary.png" width="46%" alt="RF SHAP summary">
<img src="results/xgb_sum.png" width="46%" alt="XGBoost SHAP summary">
</div>

## External Validation

Strict leakage-controlled protocol: 17 experimentally characterized MOF families
(40 structures) isolated from training via chemical-fingerprint matching.
Ensemble vs. physics-rule baselines on the closed-shell subset:

<div align="center">
<img src="results/baseline_comparison_closed_shell.png" width="70%" alt="Baseline comparison">
</div>

## Repository Structure
├── data/ # Dataset integration (QMOF + CoRE-MOF) — see Data section
├── notebooks/ # Feature engineering, training, screening, SHAP analysis
├── results/ # All paper figures and output tables
├── requirements.txt
└── README.md

## Data

Original data sources (both CC-BY-4.0):

- **QMOF Database v1.0** — https://doi.org/10.6084/m9.figshare.13147324
- **CoRE-MOF 2019** — https://doi.org/10.5281/zenodo.3677685

## Installation & Reproduction

```bash
git clone https://github.com/khanaiml/mof-gcn-ml-screening.git
cd mof-gcn-ml-screening
pip install -r requirements.txt
```

Run the notebooks in pipeline order; each states its inputs and outputs at the top.

## Citation

```bibtex
@article{Khan2026MOF,
  title   = {Physics-Informed Machine Learning Screening and Validation of
             Metal-Organic Framework/g-C3N4 Heterojunction Photocatalysts},
  author  = {Khan, Abdullah and Saeed, Muhammad and Din, Fakhrud and
             Ullah, Farhat and Ullah, Sami},
  journal = {Chinese Journal of Physics},
  year    = {2026},
  doi     = {10.1016/j.cjph.2026.07.025}
}
```

## Contact

**Abdullah Khan** — abdullahkhan.prof@gmail.com ·
[LinkedIn](https://www.linkedin.com/in/mrabdullahkhan) ·
[GitHub](https://github.com/khanaiml)
