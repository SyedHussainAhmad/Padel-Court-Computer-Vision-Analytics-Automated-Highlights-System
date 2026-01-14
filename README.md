# Padel Court Computer Vision Analytics & Automated Highlights System

## Overview
This repository contains the complete, production-ready implementation of an edge-based computer vision system designed specifically for **Padel courts**.  
The system performs **real-time AI inference locally on a single NVIDIA Jetson device per court**, generating structured match analytics and automated highlight videos without uploading raw video to the cloud.

The solution is optimized for **outdoor environments**, scalable to **100+ courts**, and incurs **no per-court or per-instance software licensing fees** after delivery.

---

## Key Features

### 1. Ball & Court Intelligence
- High-accuracy **In / Out detection**
- **Net hit detection**
- Precise **ball bounce localization** in real-world court coordinates
- **Ball speed estimation**

### 2. Match Analytics (Padel-Optimized)
Automatic classification of:
- Winners
- Unforced errors
- Rally segmentation and outcome logic

Padel-specific shot classification:
- Smash
- Volley
- Bandeja

### 3. Advanced Player Analytics
- Persistent player identity tracking across the match
- Player movement heatmaps
- Estimated running distance per player

### 4. Automated Highlights
- Event-driven video clipping
- Professional video overlays:
  - Ball speed
  - Decision labels (IN / OUT / NET)
- Multi-angle synchronization using event timestamps

---

## System Architecture

### Edge-First Processing Model
- All AI inference, tracking, and analytics run **locally on the edge device**
- **No raw video** is uploaded to the cloud
- Only:
  - Final highlight clips
  - Structured analytics metadata  
  are uploaded

### Core Characteristics
- Fully containerized using **Docker**
- Optimized for **NVIDIA Jetson Orin Nano**
- Supports **OTA updates**
- Designed for **fleet-level deployment**

---

## Accuracy Targets & Validation

- **Target Accuracy:** ≥95% for:
  - Ball bounce detection
  - In / Out classification

### Validation Methodology
- Dataset size: **≥200 raw video samples**
- Accuracy evaluation criteria finalized during the **Design Phase**, including:
  - Ground-truth labeling methodology
  - Definition of correct vs incorrect decisions
  - Tolerance margins for borderline line calls
  - Camera specifications, FPS, resolution, and lighting assumptions

> Accuracy targets are subject to physical limitations of cameras, optics, and lighting conditions.

---

## Hardware Requirements

### Option 1: High Range (Production / Scale-Ready) – Recommended

**Best for:** Long-term deployment, maximum accuracy, future expansion

**Edge Compute**
- NVIDIA Jetson Orin Nano – 16GB

**Storage**
- NVMe SSD – 1TB (Gen3 or Gen4)
  - Read ≥3000 MB/s
  - Write ≥2500 MB/s

**Cameras**
- 2× Sony IMX415 sensor cameras
- Run at 1080p @ 60 FPS
- USB 3.0 or GMSL (preferred for long cable runs)

**Lenses**
- Fixed lens 4mm or 6mm
- Low distortion
- No autofocus

**Power & Connectivity**
- 12V / 5A Jetson-compatible power supply
- Active USB 3.0 cables (for runs >3m)
- Cat6 Ethernet cable

**Why choose this tier**
- Highest stability and accuracy
- Best choice for real deployments
- Clean scalability to 100+ courts
- Future analytics headroom

---

### Option 2: Medium Range (MVP / Pilot Deployment)

**Best for:** Pilot courts, cost-sensitive rollouts

- Jetson Orin Nano – 8GB
- NVMe SSD – 512GB
- Sony IMX577 cameras (1080p @ 60 FPS)
- Fixed 4mm lenses
- 12V / 4A power supply

**Notes**
- Meets accuracy targets
- Slightly reduced performance headroom
- Ideal for early-stage deployment

---

### Option 3: Low Range (Testing / Data Collection Only)

**Not recommended for production**

- Jetson Nano (4GB) or Xavier NX (used)
- 256GB NVMe or high-quality SD card
- 1080p @ 60 FPS USB cameras (IMX327 or similar)

**Limitations**
- Lower accuracy
- Limited analytics
- No long-term scalability

---

## Deployment Model

- One Jetson device per court
- Multi-camera support per court
- Docker-based services:
  - Inference
  - Tracking
  - Analytics
  - Highlight generation
- Fleet-manageable with OTA update support

---

