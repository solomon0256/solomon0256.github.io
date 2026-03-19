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

Four-dimensional (4D) imaging radar provides radial velocity (Doppler), radar cross section (RCS), and detection confidence alongside 3D spatial information. Yet among existing learning-free multi-object trackers, these signals remain largely unexploited. This paper proposes DE-FastPoly, a plug-in extension of the FastPoly tracker with three core training-free modules — Doppler velocity initialization (DVI), measured-v_r Doppler association (DA), and score-adaptive measurement noise (SAN) — plus an optional RCS-aware association module (RCSA) as a dataset-specific extension. On the View-of-Delft (VoD) benchmark, DE-FastPoly achieves MOTA 0.361 under realistic detection (+6.7 pp over the FastPoly baseline) and MOTA 0.954 in the oracle setting (+11.7 pp), while running at 217 FPS with modest computational overhead (+6.3%). Cross-dataset transfer on nuScenes with a DA+SAN configuration reduces identity switches (IDS) by 16% without degrading AMOTA. All modules are learning-free and require no retraining.

---

## Motivation

The [Xpanner](/archive/xpanner) project is an automated construction platform for solar power plant sites. The operating environment — active construction zones — presents harsh sensing conditions: heavy dust, dynamic obstacles, and severe mechanical vibration from the excavation vehicle itself. Even with a deployed 4D radar detection model, the raw detections suffer from significant noise: bounding box drift, frequent missed detections, and false positives. To obtain stable object information for downstream safety and control applications, a lightweight tracking module is essential to (1) smooth detection noise, (2) compensate for intermittent missed detections, and (3) maintain consistent object identities across frames. This need motivated our investigation into exploiting the Doppler velocity unique to 4D radar for enhancing existing trackers, resulting in DE-FastPoly.

---

Part of: [Xpanner](/archive/xpanner) project
