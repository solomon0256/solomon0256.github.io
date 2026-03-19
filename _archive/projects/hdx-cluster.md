---
show: true
width: 6
date: 2026-02-06 00:00:00 +0900
group: Projects
layout: project
title: "Camera-Assisted Radar Clustering with Velocity Extension"
date_range: "Feb. 2026 - Present"
status: "In Progress"
permalink: /archive/hdx-cluster
tags: ["4D Radar", "Camera", "Clustering", "Velocity", "Point Cloud"]
parent: "Xpanner"
cover: /assets/images/archive/cluster_cover.jpg
---

<div class="mb-3">
    <a href="/assets/papers/Camera_Assisted_Radar_Clustering.pdf" target="_blank" class="btn btn-sm btn-outline-primary mr-2">
        <i class="fas fa-file-pdf mr-1"></i> Reference Paper (PDF)
    </a>
</div>

**ISLab, University of Ulsan** — Advised by Prof. Kang-Hyun Jo

---

## Overview

This sub-project reproduces and extends the pipeline from the reference paper *"Camera-Assisted Radar Detection Clustering for Extended Target Tracking"*. The original pipeline uses camera detections to assist radar point cloud clustering for 3D object detection. Our contribution is adding **velocity-based clustering** on top of this pipeline, leveraging the Doppler velocity from 4D radar to improve cluster separation.

---

## Motivation

In the [Xpanner](/archive/xpanner) construction site environment, raw 4D radar point clouds are sparse and noisy. Simple spatial clustering often merges nearby objects or splits a single object into fragments. By incorporating camera-assisted region proposals and Doppler velocity consistency, we achieve more stable and accurate clustering — providing better 3D bounding box inputs for the downstream tracking module.

---

## Approach

**Base pipeline (from reference paper):**
- Camera 2D detections define regions of interest
- Radar points within each region are clustered
- 3D bounding boxes are estimated from clustered radar points

**Our extension:**
- Added velocity-based clustering using Doppler v_r from 4D radar
- Points with similar spatial location AND similar radial velocity are grouped together
- Improves separation of objects moving at different speeds in close proximity

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
