# 🤖 RoachBot-SJSU: Autonomous Bug Detection and Capture Robot

**San Jose State University | Aug 2024 – May 2025**

An autonomous robotics system designed to detect, track, and capture insect-like mobile agents in indoor environments using LiDAR SLAM, AprilTag vision, and real-time path planning.

---

## 📌 Abstract

RoachBot is an intelligent mobile robot developed to tackle cockroach infestations in dormitory environments like those at **San Jose State University (SJSU)**. The system autonomously detects and pursues fast-moving targets using computer vision and LiDAR-based SLAM, simulating the challenge of tracking real insects in indoor spaces. Inspired by the robotic cat “Mechano” from *Tom and Jerry*, this project demonstrates practical applications of robotics in hygiene and pest control.

---

## 📚 Table of Contents

- [🧠 Project Motivation](#-project-motivation)
- [🔧 Methodology](#-methodology)
  - [Hardware Overview](#hardware-overview)
  - [Vision Tracking](#vision-tracking)
  - [SLAM & Localization](#slam--localization)
  - [PID Control](#pid-control)
  - [A* Path Planning](#a-path-planning)
  - [FSM Logic](#fsm-logic)
- [🗓️ Project Timeline](#️-project-timeline)
- [📊 Results & Discussion](#-results--discussion)
- [🚀 Future Work](#-future-work)

---

## 🧠 Project Motivation

Chemical-based pest control methods are common but carry health and environmental risks. RoachBot was developed as a non-toxic, scalable alternative that automates the pest-tracking process using vision, localization, and real-time motion planning — in an SJSU dorm-like environment.

---

## 🔧 Methodology

### Hardware Overview

| Component         | Description                                  |
|------------------|----------------------------------------------|
| **MBot**         | Differential drive robot base                |
| **Raspberry Pi 3** | Vision processing and AprilTag detection     |
| **BeagleBone Black** | Low-level motor actuation and sensor interfacing |
| **RPLIDAR A1**    | 360° LiDAR for SLAM                          |
| **Dual USB Cameras** | 720p, 100° FOV, front and rear mounted       |
| **RC Bug Simulator** | Remote-controlled car with AprilTag marker  |

### Vision Tracking

- AprilTags enable lightweight and fast pose estimation.
- Dual cameras expand field of view and minimize blind spots.
- Coordinates are transformed into SLAM’s world frame for consistency.
- Vision state machine manages Detect → Search → Follow transitions.

### SLAM & Localization

- SLAM constructs a real-time occupancy map and provides accurate robot localization.
- Used to avoid arena walls and maintain spatial awareness.
- Convex environment assumption simplifies mapping and path planning.

### PID Control

- PID loop ensures smooth velocity control of wheels.
- Tuned to be slightly underdamped for agility without overshoot.
- Real-time adjustments based on encoder and LiDAR feedback.

### A* Path Planning

- Plans optimal paths toward the detected bug.
- Recalculates dynamically as the target moves.
- Operates on SLAM’s occupancy grid.

### FSM Logic

- **Detect**: Scan camera feed for bug (AprilTag).
- **Search**: Rotate in place to reacquire lost target.
- **Follow**: Pursue target and update goal dynamically.

---

## 🗓️ Project Timeline

| Phase                         | Duration         |
|------------------------------|------------------|
| Concept & Requirements        | Aug 2024         |
| Hardware Setup & Calibration  | Sep 2024         |
| SLAM Development              | Oct 2024         |
| Vision + AprilTag Integration| Nov 2024         |
| FSM + PID Control             | Dec 2024         |
| A* Motion Planning            | Jan 2025         |
| Integration & Testing         | Feb–Apr 2025     |
| Final Demo & Documentation    | May 2025         |

---

## 📊 Results & Discussion

- ✅ Successfully tracks remote-controlled bug in convex dorm-like setup.
- ✅ Recovers from temporary loss using FSM and dual camera system.
- ✅ Avoids arena boundaries via LiDAR-based SLAM.
- ❌ Could not operate in non-convex or furnished environments (future scope).
- ❌ AprilTags required for tracking; not realistic for real bugs.

---

## 🚀 Future Work

- Replace AprilTags with ML-based bug detection (e.g., YOLOv8).
- Add 3D perception and maneuverability for tracking bugs on walls/ceilings.
- Reintroduce arm or suction-based bug capture.
- Enable patrolling in cluttered, multi-room layouts using advanced SLAM.
