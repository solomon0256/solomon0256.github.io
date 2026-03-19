---
show: true
width: 6
date: 2026-01-01 00:00:00 +0900
group: Projects
layout: project
title: "DE-FastPoly: Doppler-Enhanced Learning-Free Multi-Object Tracking using 4D Radar"
date_range: "Jan. 2026 - Mar. 2026"
status: "Submitted"
permalink: /archive/de-fastpoly
tags: ["4D Radar", "MOT", "Doppler", "Kalman Filter", "ISIE 2026"]
parent: "Xpanner"
cover: /assets/images/archive/de-fastpoly_cover.jpg
---

<div class="mb-3">
    <a href="/assets/papers/DE-FastPoly_ISIE2026.pdf" target="_blank" class="btn btn-sm btn-outline-primary mr-2">
        <i class="fas fa-file-pdf mr-1"></i> Paper (PDF)
    </a>
</div>

**Yuhe Wen**, Jaeho Jung, Quan Gan, Jehwan Choi, Duy-Linh Nguyen, Xuan-Thuy Vo, Kang-Hyun Jo

*Dept. of Electrical, Electronic and Computer Engineering, University of Ulsan, Korea*

**Submitted to ISIE 2026** (IEEE International Symposium on Industrial Electronics)

---

## Abstract

Four-dimensional (4D) imaging radar provides radial velocity (Doppler), radar cross section (RCS), and detection confidence alongside 3D spatial information. Yet among existing learning-free multi-object trackers, these signals remain largely unexploited. This paper proposes DE-FastPoly, a plug-in extension of the FastPoly tracker with three core training-free modules — Doppler velocity initialization (DVI), measured-v_r Doppler association (DA), and score-adaptive measurement noise (SAN) — plus an optional RCS-aware association module (RCSA) as a dataset-specific extension.

---

## Proposed Method

DE-FastPoly integrates four lightweight, training-free modules into the FastPoly tracking pipeline as plug-in components that enhance three stages: track initialization, data association, and measurement modeling.

### Module 1: Doppler Velocity Initialization (DVI)

Standard Kalman-filter-based trackers initialize the velocity of newly created tracks to zero. In 4D radar, each detection provides a radial velocity measurement v_r. DVI uses v_r to seed the Kalman filter velocity state for newly created tracks, reducing convergence latency.

- Decompose v_r into Cartesian velocity: v_x = v_r * x/r, v_y = v_r * y/r
- Provides physically grounded initial velocity estimate
- **Result**: +1.1pp MOTA improvement (oracle setting)

### Module 2: Measured-v_r Doppler Association (DA)

The association stage is augmented with a velocity consistency term derived from raw radar measurements. Each track stores v_r^trk from its most recently matched detection (measured value, not Kalman-filter-derived).

- Doppler consistency score: s_d = exp(-(delta_v_r)^2 / (2 * sigma^2)), sigma = 10.0 m/s
- Blended cost: c = alpha * c_geo + beta * (1 - s_d), alpha = 0.95, beta = 0.05
- **Result**: +5.4pp MOTA improvement alone (oracle), the dominant contributor

### Module 3: Score-Adaptive Measurement Noise (SAN)

Detection confidence serves as a proxy for localization reliability. SAN adaptively scales the Kalman measurement noise covariance R based on detection score.

- Noise scale: lambda = max(1 - k*s, lambda_min), k = 0.7, lambda_min = 0.3
- High score -> trust measurement more (reduce R); Low score -> trust prediction more
- Position-only scaling (not full R) preserves indirect velocity estimation
- **Result**: +4.6pp MOTA gain over DVI+DA under detector noise

### Module 4: RCS-Aware Association (RCSA, optional)

Radar cross section consistency as a training-free, class-specific soft cue for pedestrian association. Presented as a scene-specific exploratory enhancement.

- RCS consistency cost: c_rcs = 1 - exp(-(delta_RCS)^2 / (2 * sigma_rcs^2)), sigma_rcs = 6.0 dBsm
- Applied only to Pedestrians (stable RCS across frames)
- **Result**: additional -9 IDS on VoD

---

## Key Results

### Main Results on VoD (PointPillars, score >= 0.2)

| Method | MOTA | MOTP | IDS |
|--------|------|------|-----|
| FastPoly (baseline) | 0.294 | 0.347 | 169 |
| Poly-MOT | 0.301 | 0.268 | 290 |
| ByteTrack (3D) | 0.321 | 0.268 | 417 |
| SimpleTrack | 0.345 | **0.245** | 151 |
| **DE-FastPoly** | **0.361** | 0.265 | **127** |

**+6.7pp MOTA** over FastPoly baseline, **-25% IDS**

### Oracle Ablation (GT boxes as detections)

| Config | MOTA | IDS |
|--------|------|-----|
| Baseline | 0.837 | 190 |
| DVI | 0.848 | 171 |
| DA | 0.891 | 153 |
| DVI+DA | 0.892 | 148 |
| DVI+DA+SAN (pos-only) | 0.953 | 59 |
| **DVI+DA+SAN+RCSA** | **0.954** | **41** |

**+11.7pp MOTA** in oracle setting

### Per-Class Breakdown (Detector Setting)

| Class | Baseline MOTA | Ours MOTA | Baseline IDS | Ours IDS |
|-------|---------------|-----------|--------------|----------|
| Car | 0.326 | 0.355 (+2.9) | 61 | 56 (-8%) |
| Pedestrian | 0.177 | **0.284 (+10.7)** | 83 | **55 (-34%)** |
| Cyclist | 0.506 | **0.577 (+7.1)** | 25 | **16 (-36%)** |

### Cross-Dataset Transfer on nuScenes

| Method | AMOTA | MOTA | IDS |
|--------|-------|------|-----|
| FastPoly (baseline) | 0.7367 | 0.6319 | 414 |
| **DE-FastPoly (DA+SAN)** | **0.7367** | **0.6324** | **347 (-16%)** |

### Runtime Performance

| Config | ms/frame | FPS | Overhead |
|--------|----------|-----|----------|
| Baseline | 4.34 | 230.5 | — |
| Full DE-FastPoly | 4.61 | **216.8** | +6.3% |

All modules involve only scalar operations — no matrix decompositions or neural network inference. **Real-time at 217 FPS.**

### Parameter Sensitivity

All five hyperparameters tested with +/-50% perturbation: maximum MOTA change is only 0.004. The proposed modules are **robust to perturbation on VoD**.

---

## Links

- <i class="fas fa-file-pdf mr-1"></i> [Paper PDF](/assets/papers/DE-FastPoly_ISIE2026.pdf)
- Part of: [Xpanner](/archive/xpanner) project
