---
show: true
width: 6
date: 2025-09-03 00:00:00 +0900
group: Projects
layout: project
title: "Xpanner: Off-Road Perception & Mapping"
date_range: "Sep. 2025 - Present"
status: "In Progress"
permalink: /archive/xpanner
tags: ["SLAM", "Patchwork++", "YOLOv8", "RealSense", "Docker"]
cover: /assets/images/archive/xpanner_cover.jpg
---

## Background

Xpanner is an excavation vehicle platform requiring off-road perception capabilities including ground segmentation, 3D mapping, pothole/hole detection, and road surface analysis. The system operates in unstructured environments (construction sites, grasslands) where traditional approaches fail.

## My Contributions

- **Ground Segmentation**: Achieved x2.0 performance improvement using Patchwork++ optimization
- **LiDAR SLAM Pipeline**: x2.0 performance improvement for real-time mapping
- **3D Ground Map Processing**: Processed 1.5 billion points down to 300M points with filtering pipeline
- **Pothole/Hole Detection**: Evaluated YOLOv8 segmentation and BiSeNet for excavation hole detection with depth camera
- **Depth Camera Integration**: Selected and integrated Intel RealSense D435i (built-in IMU, IR filter)
- **Road Profile Estimation**: Implemented Unknown Input Kalman Filter (UIKF) for road surface estimation
- **Docker Environment**: Created all-in-one Docker setup for 3D detection (ROS2 + GPU packages)
- **Vibration Noise Filtering**: IMU-based vibration compensation for radar point clouds

## Technical Details

**Sensors**: LiDAR + 4D Radar + Intel RealSense D435i + IMU
**Ground Segmentation**: Patchwork++, GroundLoc
**Detection**: YOLOv8s, BiSeNet (custom-trained for excavation holes)
**SLAM**: LiDAR SLAM with vibration noise filtering
**Algorithms**: UIKF (Unknown Input Kalman Filter), Gaussian Process
**Infrastructure**: Docker, ROS2, Python, C++

## Key Results

| Metric | Improvement |
|--------|-------------|
| Ground Segmentation (Xpanner) | x2.0 |
| LiDAR SLAM (Xpanner) | x2.0 |
| 3D Map Points | 1.5B to 300M (filtered) |

## Sub-projects

- [DE-FastPoly: Doppler-Enhanced 3D MOT](/archive/de-fastpoly) — ISIE 2026 paper
