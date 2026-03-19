---
show: true
width: 12
date: 2026-01-01 00:00:00 +0900
group: Projects
layout: project
title: "DE-FastPoly: Doppler-Enhanced 3D Multi-Object Tracking"
date_range: "Jan. 2026 - Mar. 2026"
status: "Submitted"
permalink: /archive/de-fastpoly
tags: ["4D Radar", "MOT", "Doppler", "Kalman Filter", "ISIE 2026"]
parent: "Xpanner"
---

## Background

4D radar provides Doppler velocity measurements that existing 3D multi-object tracking (MOT) methods fail to exploit. DE-FastPoly proposes two lightweight enhancements to the FastPoly tracker to leverage Doppler information for improved tracking accuracy with zero runtime overhead.

## My Contributions

**Two core contributions:**

### C: Doppler Velocity Initialization
- Initialize Kalman filter velocity state from radar radial velocity (v_r) instead of zero
- Decompose v_r into vx/vy using detection-to-origin direction
- Class-adaptive v_r thresholds: Car=1.0, Pedestrian=0.3, Cyclist=0.5 m/s

### D: Doppler-Aware Association
- Blend Doppler velocity cost into the standard BEV distance cost matrix
- Cost = alpha * BEV_dist + beta * |v_r_track - v_r_det|
- Parameters: alpha=0.95, beta=0.05, sigma=10.0

## Technical Details

**Base Tracker**: FastPoly (polynomial motion model)
**Filter**: Extended Kalman Filter with dynamic observation matrix
**Datasets**: VoD (View-of-Delft), nuScenes
**v_r Aggregation**: VoD=mean, nuScenes=median
**Key Fix**: Reference frame bug — global vs ego coordinate direction mismatch (correlation 0.086 → 0.927 after fix)

## Key Results

| Dataset | Metric | Baseline | DE-FastPoly | Improvement |
|---------|--------|----------|-------------|-------------|
| VoD (Oracle) | MOTA | 0.854 | **0.893** | +3.9% |
| VoD (Oracle) | IDS | 207 | **165** | -20.3% |
| nuScenes | AMOTA | 0.737 | **0.737** | maintained |
| nuScenes | IDS | 414 | **379** | -8.5% |
| Runtime | ms/frame | 8.1 | **8.1** | zero overhead |

## Links

- Paper: Submitted to **ISIE 2026** (IEEE International Symposium on Industrial Electronics)
- Part of: [Xpanner](/archive/xpanner) project
