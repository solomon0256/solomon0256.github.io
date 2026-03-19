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
    <a href="https://github.com/solomon0256/DE-FastPoly" target="_blank" class="btn btn-sm btn-outline-dark mr-2">
        <i class="fab fa-github mr-1"></i> Code
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

## Main Results

<img src="/assets/images/archive/de-fastpoly_vod_main.png" class="w-100 rounded shadow-sm mb-2" alt="VoD Main Comparison: MOTA, IDS, FPS">

*VoD main comparison: DE-FastPoly achieves the highest MOTA (0.361) with the lowest IDS (127) while maintaining real-time speed (216.8 FPS).*

---

## Qualitative Results

<img src="/assets/images/archive/de-fastpoly_fig4_qualitative.png" class="w-100 rounded shadow-sm mb-2" alt="Qualitative comparison on VoD">

*Camera-view qualitative comparison on VoD (detector setting). Top: success case — baseline incurs an identity switch while DE-FastPoly maintains stable tracking. Bottom: failure case — both methods switch near frame 8377, showing that Doppler-aware association reduces but does not eliminate all failure modes.*

---

## Timeline

{% assign rw_items = site.data.profile.recent_work.items | where: "project", "DE-FastPoly" | sort: "sort_date" %}
{% for item in rw_items %}
<div class="mb-2 d-flex align-items-start">
    <i class="fas fa-circle mr-2" style="color: #5dade2; font-size: 6px; margin-top: 8px; flex-shrink: 0;"></i>
    <div style="flex: 1;">
        <div class="d-flex align-items-start justify-content-between">
            <div style="font-weight: 600; font-size: 0.9rem;">{{ item.title }}</div>
            <div class="ml-2 small text-muted" style="flex-shrink: 0;"><em>{{ item.date }}</em></div>
        </div>
    </div>
</div>
{% endfor %}

---

Part of: [Xpanner](/archive/xpanner) project
