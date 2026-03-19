---
show: true
width: 6
date: 2026-02-06 00:00:00 +0900
group: Projects
layout: project
title: "Camera-Assisted Radar Clustering with Velocity Extension"
date_range: "Feb. 2026 - Present"
status: "In Progress"
permalink: /archive/cluster-detection
tags: ["4D Radar", "Camera", "DBSCAN", "Doppler Velocity", "ROS2", "YOLO"]
parent: "Xpanner"
cover: /assets/images/archive/cluster_cover.jpg
---

<div class="mb-3">
    <a href="/assets/papers/Camera_Assisted_Radar_Clustering.pdf" target="_blank" class="btn btn-sm btn-outline-primary mr-2">
        <i class="fas fa-file-pdf mr-1"></i> Reference Paper (PDF)
    </a>
    <a href="/assets/papers/Xpanner_weeklyreport4.pptx" target="_blank" class="btn btn-sm btn-outline-secondary mr-2">
        <i class="fas fa-file-powerpoint mr-1"></i> Weekly Report (PPTX)
    </a>
</div>

**ISLab, University of Ulsan** — Advised by Prof. Kang-Hyun Jo

---

## Overview

Reproduces and extends the pipeline from *"Camera-Assisted Radar Detection Clustering for Extended Target Tracking"*. The original pipeline uses camera 2D detections to guide radar point cloud clustering for 3D object detection. Our contribution adds **velocity-based clustering** and **Kalman Filter + Doppler fusion** on top of this pipeline.

---

## Motivation

In the [Xpanner](/archive/xpanner) construction site, raw 4D radar point clouds are sparse and noisy. Simple spatial clustering often merges nearby objects or splits single objects into fragments. By incorporating camera-assisted region proposals, Doppler velocity consistency, and Kalman-based state estimation, we achieve stable and accurate 3D object localization for the downstream tracking and mapping modules.

---

## System Architecture

### Sensors
- **OAK-D Camera**: RGB image for 2D detection
- **Bosch 4D Radar**: PointCloud2 with Doppler velocity, RCS, SNR
- **Docker + ROS2 Humble**: Containerized deployment on Jetson Orin Nano

### Detection Classes

| Class | ID | 3D Size (m) |
|-------|----|-------------|
| vertical_pile | 0 | 0.5 x 0.5 x 1.5 |
| horizontal_pile | 1 | 3.5 x 0.5 x 0.5 |
| machine | 2 | 2.5 x 2.5 x 5.0 |
| worker | 3 | 1.2 x 1.2 x 2.2 |

---

## Approach

### Base Pipeline (Reference Paper)
- Camera 2D detections (YOLOv8) define regions of interest
- Radar points are projected into image and matched to 2D bounding boxes
- Spatial DBSCAN clusters radar points within each region

### Our Extension: 2-Stage Clustering

**Stage 1: Feature-based DBSCAN**
- Uses radial velocity, RCS, SNR as features
- Chebyshev distance metric
- Groups radar points from the same physical object

**Stage 2: Spatial DBSCAN**
- 3D Euclidean distance
- Range-adaptive eps (farther objects → larger eps)
- Class-specific parameters tuned to physical object sizes

### Kalman Filter + Doppler Fusion

- **State**: `[x, y, vx, vy]` (position + velocity)
- **Predict**: constant-velocity model
- **Update**: Doppler velocity decomposed into radial/tangential components
  - Radial: 80% Doppler + 20% Kalman
  - Tangential: Kalman only
- **Jump protection**: rejects measurements >1.5m from predicted position

---

## Timeline

{% assign rw_items = site.data.profile.recent_work.items | where: "project", "Cluster Detection" | sort: "sort_date" %}
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

---

Part of: [Xpanner](/archive/xpanner) project
