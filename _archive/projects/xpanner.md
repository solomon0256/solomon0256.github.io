---
show: true
width: 6
date: 2025-09-03 00:00:00 +0900
group: Projects
layout: project
title: "Xpanner: Perception System for Solar Power Plant Construction"
date_range: "Sep. 2025 - Present"
status: "In Progress"
permalink: /archive/xpanner
tags: ["4D Radar", "Camera", "3D Detection", "Edge Deployment", "ROS2"]
cover: /assets/images/archive/xpanner_arizona.jpg
---

<div class="mb-3">
    <span class="badge badge-primary" style="font-size: 0.75rem;">In Progress</span>
    <a href="/assets/papers/Xpanner_work1.pptx" target="_blank" class="btn btn-sm btn-outline-primary ml-2">
        <i class="fas fa-file-powerpoint mr-1"></i> Presentation 1
    </a>
    <a href="/assets/papers/Xpanner_weeklyreport4.pptx" target="_blank" class="btn btn-sm btn-outline-primary ml-2">
        <i class="fas fa-file-powerpoint mr-1"></i> Weekly Report 4
    </a>
    <a href="/assets/papers/Camera_Assisted_Radar_Clustering.pdf" target="_blank" class="btn btn-sm btn-outline-secondary ml-2">
        <i class="fas fa-file-pdf mr-1"></i> Ref: Camera-Assisted Radar Clustering
    </a>
</div>

**ISLab, University of Ulsan** — Advised by Prof. Kang-Hyun Jo

**Funded by Xpanner Inc.** | Field data collected in **Arizona, USA**

---

## Overview

<img src="/assets/images/archive/xpanner_arizona.jpg" class="w-100 rounded shadow-sm mb-3" alt="Xpanner project - Arizona field test">

Xpanner is an automated construction platform for **solar power plant sites**. The goal is to build a real-time perception system that detects and localizes key objects on the construction site using **4D radar and camera** fusion, deployed on an **edge computing platform** mounted on the excavation vehicle.

---

## Approach

The construction site environment presents low visibility (dust, weather), severe mechanical vibration, and dynamic obstacles. Our pipeline addresses these challenges in three stages:

**1. Noise Reduction** — Radar and IMU-based algorithmic denoising at the signal level. Vibration from the excavation vehicle introduces significant noise into the raw radar point cloud. We apply filtering (Go-RIO, Uncertainty-Aware, Iterated Kalman Filter) to suppress vibration noise and calibrate asynchronous radar-IMU data before feeding to the detection model.

**2. Detection** — 4D radar + camera fusion for 3D object detection. After denoising, the cleaned radar points and camera images are fed into the detection model to identify and locate targets on the construction site.

**3. Mapping** — Localize all visible support pillars and build a site map for construction automation and path planning.

### Detection Targets

- Support pillars (solar panel mounting structures)
- Construction workers
- Other construction machines
- Construction materials to be installed

---

## Motivation

Solar power plant construction involves heavy machinery operating alongside workers and scattered materials in open, unstructured environments. Low visibility due to dust, severe vibration from excavation vehicles, and dynamic obstacles make reliable perception critical for both safety and automation. A robust detection system must work under these harsh conditions — motivating the use of 4D radar (weather/dust-robust, provides Doppler velocity) combined with camera for accurate object classification and localization.

---

## 2D Detection Results

<div class="row mb-3">
    <div class="col-md-4 p-1"><img src="/assets/images/archive/xpanner_2d_result1.png" class="w-100 rounded shadow-sm" alt="2D detection result 1"></div>
    <div class="col-md-4 p-1"><img src="/assets/images/archive/xpanner_2d_result2.png" class="w-100 rounded shadow-sm" alt="2D detection result 2"></div>
    <div class="col-md-4 p-1"><img src="/assets/images/archive/xpanner_2d_result3.png" class="w-100 rounded shadow-sm" alt="2D detection result 3"></div>
</div>

*YOLO 2D detection on Xpanner construction site data: detecting support pillars, workers, and construction materials.*

---

## Sub-projects

- [DE-FastPoly: Doppler-Enhanced 3D MOT](/archive/de-fastpoly) — ISIE 2026 paper on Doppler-enhanced tracking
- [Cluster Detection](/archive/hdx-cluster) — Radar point cloud clustering for 3D object detection

---

## Timeline

{% assign rw_items = site.data.profile.recent_work.items | where: "project", "Xpanner" | sort: "sort_date" %}
{% if rw_items.size > 0 %}
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
{% else %}
*Timeline entries coming soon.*
{% endif %}
