---
layout: single
title: "Research Projects"
permalink: /projects/
toc: true
toc_label: "Projects"
toc_icon: "flask"
author_profile: false
---

Four independent, research-grade frameworks covering the core domains of industrial AI. Each repo is a self-contained platform with dataset loaders, model implementations, evaluation metrics, benchmark scripts, and tutorial notebooks.

---

## Industrial Predictive Maintenance

**GitHub:** [IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance)

Industrial machines fail unexpectedly, causing costly unplanned downtime. This framework provides complete AI pipelines for **Remaining Useful Life (RUL) prediction** and **fault detection** on real industrial sensor data.

### Models

| Model | Architecture | Task | Key Strength |
|-------|-------------|------|--------------|
| **LSTM** | 2-layer stacked LSTM + Bahdanau attention | RUL regression | Long-range temporal dependencies |
| **Transformer** | Encoder-only + sinusoidal positional encoding | RUL regression | Parallel sequence modeling |
| **TCN** | Dilated causal convolutions + residual connections | RUL regression | Exponential receptive field growth |
| **Autoencoder** | LSTM encoder-decoder | Anomaly detection | Unsupervised — no fault labels required |

### Datasets

| Dataset | Domain | Signals | Fault Types |
|---------|--------|---------|-------------|
| [NASA CMAPSS](https://ti.arc.nasa.gov/c/6/) | Turbofan engine | 21 sensors | HPC/fan degradation |
| [CWRU Bearing](https://engineering.case.edu/bearingdatacenter) | Rolling bearing | Vibration (2ch) | Outer/inner race, ball |
| [IMS Bearing](https://ti.arc.nasa.gov/c/3/) | Rolling bearing | Vibration (4ch) | Outer/inner race, roller |
| [Paderborn Bearing](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/) | Rolling bearing | Vibration + current | 32 damage conditions |

### Key Features

- Unified dataset loaders with automatic download for CMAPSS
- Signal preprocessing: Butterworth filter, wavelet denoising, Z-score normalization
- Time-domain features: RMS, kurtosis, crest factor, Shannon entropy
- Frequency-domain features: FFT, PSD, spectral centroid, band energy
- ONNX export + INT8 quantization for edge deployment
- Real-time sliding window inference pipeline
- 6 fully reproducible Jupyter notebooks

[View Repo →](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance){: .btn .btn--primary}
[Notebooks →](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance/tree/main/notebooks){: .btn .btn--inverse}

---

## Industrial Time-Series AI

**GitHub:** [IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI)

Factories generate massive multivariate sensor streams that standard ML libraries handle poorly. This framework provides **reproducible SOTA baseline implementations** specifically designed for industrial IoT, ICS/SCADA systems, and smart-manufacturing data.

### Models

| Model | Architecture | Forecasting | Anomaly | Paper |
|-------|-------------|:-----------:|:-------:|-------|
| **LSTM** | Stacked RNN + linear head | ✓ | ✓ (AE) | Hochreiter & Schmidhuber, 1997 |
| **TCN** | Causal dilated Conv1d + residual | ✓ | — | Bai et al., 2018 |
| **Transformer** | Self-attention + positional encoding | ✓ | — | Vaswani et al., 2017 |
| **PatchTST** | Patching + channel-independent attention | ✓ | — | Nie et al., ICLR 2023 |
| **DLinear** | Trend/residual decomposition + linear | ✓ | — | Zeng et al., AAAI 2023 |

### Datasets

| Dataset | Domain | Features | Task | Access |
|---------|--------|:--------:|------|--------|
| ETTh1/h2, ETTm1/m2 | Power grid | 7 | Forecasting | Free |
| PSM | Server metrics | 25 | Anomaly detection | Free |
| SMAP / MSL | NASA telemetry | Multi | Anomaly detection | Free |
| SWaT / WADI | Water ICS | 51 / 123 | Both | Request from iTrust |

### Key Features

- Zero-copy strided window extraction for large sensor archives
- Point-Adjust (PA) metric — standard for ICS/SCADA anomaly benchmarks
- DLinear insight: strong linear baseline that matches Transformers on ETT
- Built-in synthetic SWaT/WADI data — no download required to run benchmarks
- 3 end-to-end tutorial notebooks

[View Repo →](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI){: .btn .btn--primary}
[Notebooks →](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI/tree/main/tutorials){: .btn .btn--inverse}

---

## AI Power Electronics Diagnostics

**GitHub:** [IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics](https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics)

Industrial power electronics systems — inverters, motor drives, converters — fail due to switching faults, overheating, and harmonic distortions. This framework provides **AI-based early fault detection from electrical signals** (voltage waveforms, current signals, harmonic spectrum).

### Models

| Model | Architecture | Key Strength | Parameters |
|-------|-------------|--------------|:----------:|
| **1D CNN** | Residual Conv1d blocks + GAP | Fast training, strong baseline | ~1.2M |
| **Spectrogram CNN** | ResNet-18 on STFT images | Transient fault signatures | ~11M |
| **Transformer** | Patch-based encoder | Long-range temporal patterns | ~800K |
| **BiLSTM + Attention** | 2-layer BiLSTM + additive attention | Interpretable, sequential | ~1.8M |
| **Autoencoder** | 1D Conv encoder-decoder | Unsupervised, no labels needed | ~500K |

### Signal Processing Pipeline

```
Raw Signal (C, T)
       ├─→ FFT Analysis       → amplitude spectrum, THD, harmonic features
       ├─→ STFT Spectrogram   → (C, H, W) time-frequency image for CNN
       ├─→ Wavelet Features   → DWT sub-band energies, CWT scalogram
       └─→ Harmonic Analysis  → IEEE 519 compliance, ITSC sideband detection
```

### Fault Domains

| Domain | Fault Classes | Signals |
|--------|:-------------:|---------|
| 3-Phase VSI Inverter | 9 (IGBT T1–T6 open, short, DC fault, normal) | Va, Vb, Vc, Ia, Ib, Ic |
| PMSM Motor Drive | 5 (phase loss, ITSC, bearing, overtemp, normal) | Ia, Ib, Ic |

### Key Features

- Physics-informed synthetic data generators — no download needed
- Unified `SignalFeatureExtractor` with FFT, STFT, wavelet, and harmonic modes
- IEEE 519-2022 harmonic compliance checking built in
- Streaming fault detection with `SwitchFaultDetector` and `HarmonicFaultDetector`
- 4 tutorial notebooks from EDA to streaming inference

[View Repo →](https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics){: .btn .btn--primary}
[Notebooks →](https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics/tree/main/notebooks){: .btn .btn--inverse}

---

## Smart Manufacturing AI

**GitHub:** [IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI)

Modern factories need AI across four interconnected challenges. This framework provides **research-grade pipelines** for visual defect detection, robot anomaly detection, RL-based scheduling, and digital twin simulation.

### Modules

| Module | Problem | Approach | Key Models |
|--------|---------|----------|------------|
| `vision/` | Surface defect detection | Fine-tuned + GradCAM | ResNet-50, EfficientNet-B4, ViT-B/16 |
| `robotics/` | Robot joint fault detection | LSTM Autoencoder | LSTM-AE variants |
| `optimization/` | Production scheduling | Proximal Policy Optimization | PPO (SB3) |
| `digital_twin/` | Production line simulation | Discrete-event + MQTT/OPC-UA | — |

### Datasets

| Dataset | Domain | Size | Access |
|---------|--------|------|--------|
| [MVTec AD](https://www.mvtec.com/company/research/datasets/mvtec-ad) | Industrial surfaces & objects | ~4.9 GB | Research (non-commercial) |
| [NEU Surface Defect](http://faculty.neu.edu.cn/yunhyan/NEU_surface_defect_database.html) | Hot-rolled steel strip | ~36 MB | Free |
| Robot Sensor (synthetic) | 6-DOF robot joints | Generated locally | Built-in |

### Key Features

- Attention Rollout visualization for ViT-B/16
- GradCAM heatmap overlay on defect images
- `ManufacturingEnv` (Gymnasium-compatible) for RL training
- `TwinSimulator` with `TwinSync` for MQTT/OPC-UA integration
- 5 tutorial notebooks covering all modules

[View Repo →](https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI){: .btn .btn--primary}
[Notebooks →](https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI/tree/main/notebooks){: .btn .btn--inverse}
