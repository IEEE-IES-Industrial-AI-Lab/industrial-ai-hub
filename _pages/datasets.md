---
layout: single
title: "Benchmark Datasets"
permalink: /datasets/
toc: true
toc_label: "Contents"
toc_icon: "database"
author_profile: false
---

An overview of all benchmark datasets used across the four frameworks, with access instructions and usage notes. We prioritize well-established public datasets that appear in IEEE TIE, TII, and PHM conference papers.

---

## Predictive Maintenance Datasets

Used in: [Industrial-Predictive-Maintenance](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance)

### NASA CMAPSS / N-CMAPSS

| Property | Value |
|----------|-------|
| Source | [NASA PCoE](https://ti.arc.nasa.gov/c/6/) |
| Domain | Turbofan engine degradation simulation |
| Subsets | FD001–FD004 (CMAPSS), DS01–DS08 (N-CMAPSS 2021) |
| Signals | 21 sensor channels + 3 operational settings |
| Task | Remaining Useful Life (RUL) regression |
| Size | ~70K engine cycles (CMAPSS) |
| Access | **Free download** |

> **Note:** N-CMAPSS (2021) is the updated dataset used in recent IEEE TII papers and the PHM 2021 challenge. It differs from the original CMAPSS in fault modes and sensor resolution. Always specify which version you use when comparing published results.

**Download via the provided loader:**
```bash
python datasets/cmapss_loader.py  # auto-downloads from NASA PCoE
```

### IMS Bearing (University of Cincinnati)

| Property | Value |
|----------|-------|
| Source | [NASA PCoE](https://ti.arc.nasa.gov/c/3/) |
| Domain | Rolling element bearing run-to-failure |
| Signals | Vibration from 4 bearings at 20 kHz |
| Task | Anomaly detection / RUL estimation |
| Size | ~1 GB raw (3 run-to-failure tests) |
| Access | **Free download** |

### Paderborn University Bearing Dataset

| Property | Value |
|----------|-------|
| Source | [KAt DataCenter](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/) |
| Domain | Rolling element bearing (electrical motor) |
| Signals | Vibration + motor current |
| Conditions | 32 (12 artificial + 14 real + 6 healthy) |
| Task | Fault classification |
| Size | ~32 GB |
| Access | **Free** — registration required |

> **Note:** Paderborn requires following their specific train/test split protocol to produce comparable results with published baselines. See the `paderborn_loader.py` documentation.

### CWRU Bearing Dataset

| Property | Value |
|----------|-------|
| Source | [Case Western Reserve University](https://engineering.case.edu/bearingdatacenter) |
| Domain | Rolling element bearing |
| Signals | Vibration at drive end and fan end |
| Conditions | 4 motor loads (0–3 HP); 4 fault diameters |
| Task | Fault classification |
| Access | **Free download** |

> **Note:** Motor load conditions (0–3 HP) significantly affect signal characteristics. Published results must specify which load conditions were used in train/test split.

---

## Time-Series AI Datasets

Used in: [Industrial-Time-Series-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI)

### ETT (Electricity Transformer Temperature)

| Property | Value |
|----------|-------|
| Source | [GitHub — ETDataset](https://github.com/zhouhaoyi/ETDataset) |
| Domain | Power grid — electricity transformer |
| Subsets | ETTh1, ETTh2 (hourly), ETTm1, ETTm2 (15-min) |
| Features | 7 (1 target + 6 covariates) |
| Task | Multivariate long-horizon forecasting |
| Access | **Free download** |

### PSM (Pooled Server Metrics)

| Property | Value |
|----------|-------|
| Domain | Server infrastructure metrics |
| Features | 25 |
| Task | Anomaly detection |
| Access | **Free** — via download script |

### SMAP / MSL (NASA Telemetry)

| Property | Value |
|----------|-------|
| Source | [NASA JPL](https://github.com/khundman/telemanom) |
| Domain | Spacecraft / Mars Science Laboratory telemetry |
| Features | Multi-channel |
| Task | Anomaly detection |
| Access | **Free download** |

### SWaT / WADI (Singapore iTrust)

| Property | Value |
|----------|-------|
| Source | [iTrust, SUTD Singapore](https://itrust.sutd.edu.sg/testbeds/secure-water-treatment-swat/) |
| Domain | Secure Water Treatment / Water Distribution ICS |
| Features | 51 (SWaT) / 123 (WADI) |
| Task | Anomaly detection + forecasting |
| Access | **Request required** — data agreement with iTrust |

> **Note:** SWaT and WADI require submitting a data-access request form to iTrust SUTD. The framework includes synthetic versions of both datasets to allow running benchmarks immediately without the access request.

```bash
# Synthetic versions — run immediately
python benchmarks/run_benchmark.py --task anomaly

# Real SWaT/WADI — after obtaining access
python datasets/download_datasets.py --datasets swat wadi
```

---

## Power Electronics Datasets

Used in: [AI-Power-Electronics-Diagnostics](https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics)

### Kaggle Electric Motor Temperature

| Property | Value |
|----------|-------|
| Source | [Kaggle — wkirgsn](https://www.kaggle.com/datasets/wkirgsn/electric-motor-temperature) |
| Domain | Permanent Magnet Synchronous Motor (PMSM) drive |
| Features | 13 (motor currents, voltages, ambient temp, speed, torque) |
| Task | Temperature prediction and thermal anomaly detection |
| Size | ~1.3M time steps (185 sessions) |
| Access | **Free** — Kaggle account required |
| Reference | Kirchgässner et al., IEEE IEMDC 2019 |

```bash
# Prerequisites: pip install kaggle and configure ~/.kaggle/kaggle.json
python datasets/download_scripts/setup_datasets.py --dataset motor_temp
```

### Synthetic Inverter and Motor Drive Signals

| Property | Value |
|----------|-------|
| Type | Physics-informed simulation |
| Inverter faults | 9 classes (IGBT T1–T6 open, short, DC undervoltage, normal) |
| Motor faults | 5 classes (phase loss, ITSC, bearing, overtemp, normal) |
| Signals | 3-phase voltage and current waveforms |
| Access | **Built-in** — generated with numpy/scipy, no download needed |

```python
from datasets.synthetic import InverterFaultSimulator
sim = InverterFaultSimulator()
X, y = sim.generate_dataset(n_per_class=300, window_size=1024)
```

---

## Smart Manufacturing Datasets

Used in: [Smart-Manufacturing-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI)

### MVTec Anomaly Detection (MVTec AD)

| Property | Value |
|----------|-------|
| Source | [MVTec Software](https://www.mvtec.com/company/research/datasets/mvtec-ad) |
| Domain | Industrial surfaces and objects |
| Categories | 15 (bottle, cable, capsule, carpet, grid, hazelnut, leather, metal nut, pill, screw, tile, toothbrush, transistor, wood, zipper) |
| Images | ~5,354 (training + test) |
| Labels | Binary (normal/defective) + pixel-level segmentation masks |
| Task | Anomaly detection + defect segmentation |
| Size | ~4.9 GB |
| Access | **Non-commercial research license** — see [MVTec terms](https://www.mvtec.com/company/research/datasets/mvtec-ad) |
| Reference | Bergmann et al., CVPR 2019 |

> **License note:** MVTec AD is provided for non-commercial research use only and cannot be redistributed. The dataset loaders point to the official MVTec download page.

### NEU Surface Defect Database

| Property | Value |
|----------|-------|
| Source | [Northeastern University](http://faculty.neu.edu.cn/yunhyan/NEU_surface_defect_database.html) |
| Domain | Hot-rolled steel strip surface defects |
| Classes | 6 (crazing, inclusion, patches, pitted surface, rolled-in scale, scratches) |
| Images | 1,800 (300 per class), 200 × 200 px grayscale |
| Task | Defect classification |
| Size | ~36 MB |
| Access | **Free download** |

### Robot Sensor Data (Synthetic)

| Property | Value |
|----------|-------|
| Type | Simulated 6-DOF robot joint sensor streams |
| Channels | 12 (joint angles, velocities, torques) |
| Classes | Normal / Fault |
| Access | **Built-in** — generated locally, no download needed |

---

## Dataset Access Summary

| Dataset | Access Type | Notes |
|---------|:-----------:|-------|
| NASA CMAPSS / N-CMAPSS | Free | Auto-download via loader |
| IMS Bearing | Free | Manual download from NASA PCoE |
| Paderborn Bearing | Free + registration | Follow their split protocol |
| CWRU Bearing | Free | Specify load condition in results |
| ETT | Free | Auto-download via script |
| PSM / SMAP / MSL | Free | Via download script |
| **SWaT / WADI** | **Request required** | iTrust SUTD data agreement |
| Kaggle Motor Temp | Free | Kaggle account + API key |
| **MVTec AD** | **Research license** | Non-commercial only |
| NEU Surface Defect | Free | Direct download |
| Synthetic (PED + SM) | Built-in | No download needed |
