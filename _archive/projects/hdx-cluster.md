---
show: true
width: 12
date: 2025-09-01 00:00:00 +0900
group: Projects
layout: project
title: "Cluster Detection for Construction Sites"
date_range: "Sep. 2025 - Present"
status: "In Progress"
permalink: /archive/hdx-cluster
tags: ["Clustering", "4D Radar", "Point Cloud", "DDCFusion"]
parent: "HDX"
---

## Background

In construction site environments, accurate 3D object detection from sparse radar point clouds requires effective clustering methods. This sub-project develops a radar-camera fusion clustering pipeline based on DDCFusion for the HDX platform.

## My Contributions

- **DDCFusion Integration**: Adapted DDCFusion framework for construction site radar data
- **3D BBox Estimation**: Radar + camera fusion for 3D bounding box estimation
- **Ground Truth Pipeline**: Using 3D LiDAR annotations as supervision
- **Iterative Training**: Minimizing detection loss through iterative training cycles

## Technical Details

**Method**: DDCFusion — Radar & camera estimate 3D bounding boxes with LiDAR annotations as Ground Truth
**Sensors**: 4D Radar + Camera (LiDAR for annotation only)
**Training**: Iterative loss minimization
**Framework**: Python, PyTorch

## Links

- Part of: [HDX](/archive/hdx) project
