---
show: true
width: 6
date: 2025-09-01 00:00:00 +0900
group: Projects
layout: project
title: "HDX: 4D Radar Perception for Construction Sites"
date_range: "Sep. 2025 - Present"
status: "In Progress"
permalink: /archive/hdx
tags: ["4D Radar", "LiDAR", "3D Detection", "GUI", "ROS2"]
cover: /assets/images/archive/hdx_cover.jpg
---

## Background

The HDX project develops a comprehensive perception system for construction site safety monitoring, integrating 4D radar, LiDAR, and camera sensors mounted on excavators. The goal is real-time detection of workers, vehicles, and obstacles in hazardous construction environments.

## My Contributions

- **LiDAR 3D Object Detection**: Deployed and optimized LiDAR-based 3D detection pipeline for construction site objects
- **Radar Ground Mapping**: Developed radar-based ground surface mapping for terrain analysis
- **Radar vs LiDAR Comparison**: Built comparison framework to evaluate detection accuracy between 4D radar and LiDAR
- **Velocity & Distance Analysis**: Conducted experiments measuring radar accuracy for object speed (workers, excavators) and radial distance at UOU test site
- **GUI Application**: Designed and completed the full GUI visualization system with installation manual
- **SLAM Visualization**: Automated RViz-based SLAM visualization with custom bash scripts and `.rviz` configuration

## Technical Details

**Sensors**: 4D Radar (HDX) + LiDAR + Camera + IMU
**Framework**: ROS2, RViz, Python
**Detection**: LiDAR 3D object detection pipeline
**Data Collection**: UOU campus (workers, excavators), HDX construction sites
**Experiments**: Velocity accuracy (real speed vs radar measurement), distance accuracy (radial distance measurement)

## Key Results

- GUI application completed and delivered
- Radar velocity/distance precision validated on real construction site data
- SLAM visualization pipeline automated (one-click setup)

## Sub-projects

- [Cluster Detection](/archive/hdx-cluster) — Radar point cloud clustering for 3D object detection
