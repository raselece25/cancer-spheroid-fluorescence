# 🧫 3D Cancer Spheroid Fluorescence Imaging

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)](https://opencv.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![DOI](https://img.shields.io/badge/Published-Pharmaceutics%20IF%205.5-blue?style=flat-square)](https://doi.org/10.3390/pharmaceutics)

> Mesoscopic fluorescence imaging pipeline for monitoring light-triggered drug release in 3D tumor spheroid models — enabling quantitative, spatially-resolved tracking of chemophototherapy (CPT) delivery.

**Published in Pharmaceutics (MDPI), Q1, Impact Factor 5.5.**

---

## 📖 Overview

3D tumor spheroids are powerful preclinical cancer models that better recapitulate the spatial heterogeneity and drug penetration characteristics of in vivo tumors compared to 2D cell cultures.

This project develops a **mesoscopic fluorescence imaging pipeline** that:
- Quantitatively images **light-triggered drug release** in 3D cancer spheroid models
- Combines **SFDI** and **fluorescence imaging** to extract spatially-resolved drug concentration maps
- Monitors pharmacokinetics of **Porphyrin-Phospholipid (PoP)** and **Doxorubicin (Dox)** over time
- Provides preclinical validation for intraoperative CPT monitoring systems

---

## ✨ Key Features

- **Mesoscopic fluorescence imaging** — wide-field, quantitative fluorescence at the spheroid scale
- **SFDI-based optical correction** — absorption and scattering correction for accurate fluorophore quantification
- **Light-trigger monitoring** — time-resolved imaging of drug release upon laser activation
- **3D spheroid segmentation** — automated spheroid boundary detection and ROI extraction
- **Multi-channel fluorescence** — simultaneous PoP and Dox channel imaging and unmixing
- **Pharmacokinetic analysis** — time-course drug concentration modeling

---

## 🔬 Experimental Pipeline

```
Spheroid Culture (MCF-7 / OVCAR-3)
         │
         ▼
Drug Loading (PoP-Dox nanoparticles)
         │
         ▼
Mesoscopic Fluorescence Imaging
  ├── Pre-trigger baseline
  ├── Light trigger (671 nm laser)
  └── Post-trigger time-lapse
         │
         ▼
SFDI Optical Property Extraction
  └── μa and μs' correction maps
         │
         ▼
Quantitative Fluorescence Maps
  ├── [PoP] concentration map
  └── [Dox] concentration map
         │
         ▼
Pharmacokinetic Modeling & Analysis
```

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Image Processing | Python, OpenCV, scikit-image |
| Numerical Analysis | NumPy, SciPy |
| Segmentation | OpenCV contour detection, watershed |
| Visualization | Matplotlib, seaborn |
| Data Management | Pandas, HDF5, TIFF stacks |

---

## 🗂️ Repository Structure

```
cancer-spheroid-fluorescence/
├── imaging/
│   ├── acquisition.py         # Image acquisition control
│   ├── fluorescence.py        # Fluorescence image processing
│   └── sfdi_correction.py     # SFDI-based optical correction
├── segmentation/
│   ├── spheroid_detect.py     # Automated spheroid detection
│   └── roi_extraction.py      # Region-of-interest extraction
├── analysis/
│   ├── quantification.py      # Fluorophore concentration quantification
│   ├── pharmacokinetics.py    # PK modeling (uptake/release curves)
│   └── spectral_unmixing.py   # Multi-channel fluorescence unmixing
├── notebooks/
│   ├── 01_spheroid_segmentation.ipynb
│   ├── 02_fluorescence_quantification.ipynb
│   └── 03_pharmacokinetics_analysis.ipynb
└── tests/
```

---

## 🚀 Getting Started

```bash
git clone https://github.com/raselece25/cancer-spheroid-fluorescence.git
cd cancer-spheroid-fluorescence
pip install -r requirements.txt
```

```python
from imaging.fluorescence import FluorescenceProcessor
from segmentation.spheroid_detect import SpheroidDetector
from analysis.quantification import FluorophoreQuantifier

processor = FluorescenceProcessor(channels=['PoP', 'Dox'])
fl_stack = processor.load('data/raw/spheroid_timecourse.tif')

detector = SpheroidDetector(min_area=5000)
mask, boundary = detector.detect(fl_stack[0, 0])

quantifier = FluorophoreQuantifier(mu_a=0.02, mu_sp=1.0)
pop_conc, dox_conc = quantifier.quantify(fl_stack, mask)
```

---

## 📊 Key Results

- Successful imaging of light-triggered PoP-Dox nanoparticle release in 3D spheroid models
- Spatial heterogeneity of drug penetration quantified across spheroid cross-sections
- Time-resolved release curves correlated with laser fluence and treatment duration
- Validated across multiple spheroid sizes (200–600 µm diameter)

---

## 📚 Publications

1. Kluiszo, E., **Ahmmed, R.**, Sunar, U. (2024). *Mesoscopic Fluorescence Imaging of Light-Triggered Chemotherapeutic Release in Cancer Spheroid Models*. **Pharmaceutics (MDPI)**, Q1, **IF 5.5**. [Read Paper](https://doi.org/10.3390/pharmaceutics)
2. **Ahmmed, R.**, et al. (2024). *Quantitative Fluorescence Imaging, Light-Triggering, and Monitoring*. **Taylor & Francis / NCI Handbook**, Chapter 5, Section 1.

---

## 🏆 Funding

NIH R01-funded — National Cancer Institute, Stony Brook University (2023–2026).

---

## 👤 Author

**Rasel Ahmmed** — PhD Candidate, Biomedical Engineering, Stony Brook University
[LinkedIn](https://www.linkedin.com/in/raahmmed) · [Portfolio](https://raselece25.github.io) · [Email](mailto:rasel.ahmmed@stonybrook.edu)

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.
