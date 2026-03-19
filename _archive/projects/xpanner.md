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
cover: /assets/images/archive/xpanner_cover.jpg
---

<div class="mb-3">
    <span class="badge badge-primary" style="font-size: 0.75rem;">In Progress</span>
</div>

**ISLab, University of Ulsan** — Advised by Prof. Kang-Hyun Jo

---

## Overview

Xpanner is an automated construction platform for **solar power plant sites**. The goal is to build a real-time perception system that detects and localizes key objects on the construction site using **4D radar and camera** fusion, deployed on an **edge computing platform** mounted on the excavation vehicle.

### Detection Targets

- Support pillars (solar panel mounting structures)
- Construction workers
- Other construction machines
- Construction materials to be installed

---

## Motivation

Solar power plant construction involves heavy machinery operating alongside workers and scattered materials in open, unstructured environments. Dust, vibration, and dynamic obstacles make reliable perception critical for both safety and automation. A robust detection system must work under these harsh conditions — motivating the use of 4D radar (weather/dust-robust, provides Doppler velocity) combined with camera for accurate object classification and localization.

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
