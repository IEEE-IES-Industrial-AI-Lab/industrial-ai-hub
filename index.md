---
layout: splash
title: "IEEE IES Industrial AI Lab"
header:
  overlay_color: "#00629B"
  overlay_filter: 0.75
  actions:
    - label: "Explore Projects"
      url: "#projects"
    - label: "GitHub Organization"
      url: "https://github.com/IEEE-IES-Industrial-AI-Lab"
excerpt: >-
  Open-source, research-grade frameworks for applying AI to industrial systems —
  predictive maintenance, time-series modeling, power electronics diagnostics,
  and smart manufacturing.

intro:
  - excerpt: >-
      **4 research repos** &nbsp;·&nbsp; **20+ SOTA models** &nbsp;·&nbsp;
      **15+ benchmark datasets** &nbsp;·&nbsp; **20+ tutorial notebooks**

feature_row:
  - title: "Industrial Predictive Maintenance"
    excerpt: >-
      AI pipelines for **Remaining Useful Life (RUL) prediction** and fault
      detection on NASA CMAPSS, CWRU, IMS, and Paderborn bearing datasets.
      Includes LSTM, Transformer, TCN, and LSTM Autoencoder with a unified
      `fit / predict / evaluate` API and ONNX edge-deployment support.
    url: "https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance"
    btn_label: "View Repo →"
    btn_class: "btn--primary"
  - title: "Industrial Time-Series AI"
    excerpt: >-
      SOTA benchmark suite for multivariate industrial sensor stream analysis —
      **forecasting and anomaly detection**. Implements PatchTST (ICLR 2023),
      DLinear (AAAI 2023), TCN, Transformer, and LSTM Autoencoder on ETT,
      SWaT, PSM, and SMAP datasets.
    url: "https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI"
    btn_label: "View Repo →"
    btn_class: "btn--primary"

feature_row2:
  - title: "AI Power Electronics Diagnostics"
    excerpt: >-
      Deep learning pipelines for **fault detection in inverters and motor
      drives** from voltage, current, and harmonic signals. Covers FFT, STFT
      spectrograms, wavelet analysis, and 5 model architectures (1D CNN,
      Spectrogram CNN, Transformer, BiLSTM, Autoencoder).
    url: "https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics"
    btn_label: "View Repo →"
    btn_class: "btn--primary"
  - title: "Smart Manufacturing AI"
    excerpt: >-
      AI pipelines for **vision-based defect detection** (MVTec AD, NEU Steel),
      robot joint anomaly detection, RL-based production scheduling with PPO,
      and discrete-event digital twin simulation with MQTT/OPC-UA sync.
    url: "https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI"
    btn_label: "View Repo →"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

<div class="splash-section-wrap">
<h2 id="projects" class="splash-section-heading">Research Projects</h2>
<p class="splash-section-sub">Four independent frameworks covering the core domains of industrial AI</p>
</div>

{% include feature_row %}

{% include feature_row id="feature_row2" %}

---

<div class="splash-section-wrap">
<h2 class="splash-section-heading">Benchmark Datasets</h2>
<p class="splash-section-sub">Real industrial datasets used across the four frameworks</p>
</div>

<div class="centered-content" markdown="1">

| Dataset | Domain | Task | Used In |
|---------|--------|------|---------|
| [NASA CMAPSS](https://ti.arc.nasa.gov/c/6/) | Turbofan engine | RUL prediction | Predictive Maintenance |
| [CWRU Bearing](https://engineering.case.edu/bearingdatacenter) | Rolling bearing | Fault classification | Predictive Maintenance |
| [IMS Bearing](https://ti.arc.nasa.gov/c/3/) | Rolling bearing | RUL / anomaly | Predictive Maintenance |
| [Paderborn Bearing](https://mb.uni-paderborn.de/kat/forschung/kat-datacenter/bearing-datacenter/) | Rolling bearing | Fault classification | Predictive Maintenance |
| [ETT (h1/h2/m1/m2)](https://github.com/zhouhaoyi/ETDataset) | Power grid | Forecasting | Time-Series AI |
| PSM / SMAP / MSL | Server / NASA telemetry | Anomaly detection | Time-Series AI |
| SWaT / WADI | Water treatment / distribution | Both | Time-Series AI |
| [Kaggle Motor Temp](https://www.kaggle.com/datasets/wkirgsn/electric-motor-temperature) | PMSM motor drive | Temp / anomaly | Power Electronics |
| [MVTec AD](https://www.mvtec.com/company/research/datasets/mvtec-ad) | Industrial surfaces | Defect detection | Smart Manufacturing |
| [NEU Surface Defect](http://faculty.neu.edu.cn/yunhyan/NEU_surface_defect_database.html) | Hot-rolled steel | Defect classification | Smart Manufacturing |

[Full dataset details →](/industrial-ai-hub/datasets/){: .btn .btn--primary}

</div>

---

<div class="splash-section-wrap">
<h2 class="splash-section-heading">Key Results</h2>
<p class="splash-section-sub">Reproducible benchmark results — run any benchmark with a single command</p>
</div>

<div class="centered-content" markdown="1">

| Framework | Dataset | Model | Metric | Result |
|-----------|---------|-------|--------|--------|
| Predictive Maintenance | CMAPSS FD001 | Transformer | RMSE ↓ | **12.89** |
| Predictive Maintenance | CMAPSS FD001 | Transformer | NASA Score ↓ | **198.7** |
| Time-Series AI | SWaT (synthetic) | LSTM Autoencoder | ROC-AUC ↑ | **0.9999** |
| Time-Series AI | SWaT (synthetic) | LSTM Autoencoder | F1-PA ↑ | **1.000** |
| Power Electronics | Inverter (9 classes) | 1D CNN | Accuracy ↑ | **~99%** |
| Smart Manufacturing | MVTec AD — bottle | ViT-B/16 | AUROC ↑ | **0.982** |

[Full benchmark tables →](/industrial-ai-hub/benchmarks/){: .btn .btn--primary}

</div>

---

<div class="splash-section-wrap">
<h2 class="splash-section-heading">About the Lab</h2>
</div>

The **IEEE IES Industrial AI Lab** develops open-source, research-grade AI frameworks for the [IEEE Industrial Electronics Society](https://www.ieee-ies.org/) community. Our goal is to provide reproducible baselines and benchmarks that bridge the gap between academic research and industrial deployment.

Each framework is designed as a **mini research platform** — not just code, but reproducible experiments, standardized evaluation protocols, and tutorial notebooks that make the work accessible to both engineers and researchers.

[GitHub Organization ↗](https://github.com/IEEE-IES-Industrial-AI-Lab){: .btn .btn--primary}
[IEEE IES ↗](https://www.ieee-ies.org/){: .btn .btn--inverse}
