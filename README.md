# Autonomous Freediving ROV

Autonomous underwater camera platform for freedivers and scuba divers.

## Vision

A silent and stable underwater drone capable of:

- Following divers autonomously
- Recording cinematic underwater footage
- Future AI-based training analysis
- Optional safety assistance systems

---

# MVP Goals

- Stable follow mode
- Marker-based tracking
- Dual-camera architecture
- Smooth cinematic movement
- Robust underwater operation

---

# System Architecture

## High-Level Computer
- NVIDIA Jetson Orin Nano
- Computer Vision
- Tracking
- Follow Logic

## Low-Level Controller
- Pixhawk 6C / STM32
- Stabilization
- Thruster Control
- Sensor Fusion

---

# Tracking Strategy

Hybrid tracking system:

1. Marker Tracking (Primary)
2. Visual Tracking (Secondary)
3. Motion Prediction (Fallback)

State Machine:
- MARKER_LOCK
- VISUAL_TRACK
- LOST

---

# Hardware Overview

- 6 Thrusters
    - 4 Horizontal (X-Layout)
    - 2 Vertical

- Dual Camera System
    - Main Camera (Video)
    - Tracking Camera (Computer Vision)

- Passive Stability
- Future VBS Integration

---

# Development Phases

## Phase 1
Tracking & Follow Logic (Dry Tests)

## Phase 2
Pool Prototype

## Phase 3
Depth & Hydrodynamic Optimization

## Phase 4
AI Features & Advanced Autonomy

---

# Repository Structure

/docs          -> Documentation
/software      -> High-Level Software
/firmware      -> Low-Level Control
/hardware      -> CAD & Electronics
/simulations   -> Simulation & Testing
/datasets      -> AI Training Data

---

# Technologies

- OpenCV
- ROS2
- MAVLink
- Python
- C++
- Jetson Orin Nano
- Pixhawk

---

# Future Features

- Marker-free diver tracking
- AI diver recognition
- Gesture control
- Training analytics
- Safety functions

---

# Status

Currently in architecture & tracking prototype phase.
