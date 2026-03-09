# IEEE IES Industrial AI Lab — Hub Site

<div align="center">

![Jekyll](https://img.shields.io/badge/Jekyll-Minimal%20Mistakes-CC0000?logo=jekyll&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-222?logo=github&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)
![IEEE IES](https://img.shields.io/badge/IEEE-IES%20Industrial%20AI%20Lab-00629B)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

**Central navigation and documentation hub for the IEEE IES Industrial AI Lab.**

*Projects · Datasets · Benchmarks · GitHub Pages*

</div>

---

## Overview

This repo hosts the GitHub Pages website for the [IEEE IES Industrial AI Lab](https://github.com/IEEE-IES-Industrial-AI-Lab) — a central entry point that links and documents the four research repositories.

Built with [Jekyll](https://jekyllrb.com/) and the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme, styled with IEEE IES brand colors.

**Live site:** [ieee-ies-industrial-ai-lab.github.io/industrial-ai-hub](https://ieee-ies-industrial-ai-lab.github.io/industrial-ai-hub)

---

## Site Structure

| Page | URL | Content |
|------|-----|---------|
| Homepage | `/industrial-ai-hub/` | Hero, 4 project cards, dataset table, key results |
| Projects | `/industrial-ai-hub/projects/` | Detailed per-project descriptions, model tables, dataset links |
| Datasets | `/industrial-ai-hub/datasets/` | All 10+ benchmark datasets with access instructions |
| Benchmarks | `/industrial-ai-hub/benchmarks/` | Reproducible results tables across all 4 frameworks |

---

## Linked Repositories

| Repo | Description |
|------|-------------|
| [Industrial-Predictive-Maintenance](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Predictive-Maintenance) | RUL prediction and fault detection on CMAPSS, CWRU, IMS, Paderborn |
| [Industrial-Time-Series-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Industrial-Time-Series-AI) | SOTA forecasting and anomaly detection on industrial sensor streams |
| [AI-Power-Electronics-Diagnostics](https://github.com/IEEE-IES-Industrial-AI-Lab/AI-Power-Electronics-Diagnostics) | Fault detection in inverters and motor drives from electrical signals |
| [Smart-Manufacturing-AI](https://github.com/IEEE-IES-Industrial-AI-Lab/Smart-Manufacturing-AI) | Defect detection, robot anomaly detection, RL scheduling, digital twin |

---

## Run Locally

### Prerequisites

```bash
gem install bundler
```

### Setup

```bash
git clone https://github.com/IEEE-IES-Industrial-AI-Lab/industrial-ai-hub.git
cd industrial-ai-hub
bundle install
```

### Serve

```bash
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000/industrial-ai-hub/`.

> On first run, `bundle install` downloads the `github-pages` gem and all dependencies. This may take a few minutes.

---

## Activate GitHub Pages

1. Push this repo to `github.com/IEEE-IES-Industrial-AI-Lab/industrial-ai-hub`
2. Go to **Settings → Pages**
3. Source: `main` branch, `/ (root)` folder
4. Click **Save**

GitHub will build and publish the site automatically using Jekyll (no CI workflow needed — `remote_theme` is handled natively by GitHub Pages).

---

## File Structure

```
industrial-ai-hub/
├── _config.yml            # Site config, remote_theme, nav, baseurl
├── Gemfile                # github-pages + jekyll-include-cache gems
├── index.md               # Homepage: splash layout with hero and project cards
├── _pages/
│   ├── projects.md        # Detailed project descriptions
│   ├── datasets.md        # All benchmark datasets and access notes
│   └── benchmarks.md      # Benchmark results tables across all repos
├── _data/
│   └── navigation.yml     # Top navigation links
├── assets/
│   └── css/
│       └── main.scss      # IEEE blue (#00629B) theme override
└── README.md
```

---

## Contributing

To add or update content:

- **New project card:** add a `feature_row` entry in `index.md` and a section in `_pages/projects.md`
- **New dataset:** add a row to the table in `_pages/datasets.md`
- **New benchmark result:** add a row to the appropriate table in `_pages/benchmarks.md`

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">
Part of the <a href="https://github.com/IEEE-IES-Industrial-AI-Lab"><strong>IEEE IES Industrial AI Lab</strong></a> research initiative.
</div>
