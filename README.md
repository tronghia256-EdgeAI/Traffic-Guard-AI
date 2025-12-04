# 🚦 AI Traffic Control & Accident Response System

![Python](https://img.shields.io/badge/python-3.9%2B-blue)
![YOLOv8](https://img.shields.io/badge/YOLO-v8s-green)
![ByteTrack](https://img.shields.io/badge/Tracking-ByteTrack-orange)
![RL](https://img.shields.io/badge/Reinforcement%20Learning-DQN-red)
![Telegram](https://img.shields.io/badge/API-Telegram-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> An intelligent traffic management system that detects accidents in real-time using **YOLOv8s + ByteTrack**, alerts emergency services via **Telegram**, and optimizes traffic light timings using **Deep Q-Networks (DQN)**.

## 📖 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Results](#-results)
- [License](#-license)

## 🔭 Overview
Urban traffic congestion and delayed accident response are critical issues in modern cities. This project leverages Computer Vision and Reinforcement Learning to solve these problems by:
1.  **Detecting Accidents:** Instantly identifying collisions and sending evidence (location + image) to hospitals/emergency centers.
2.  **Optimizing Flow:** Dynamically adjusting traffic light durations based on real-time vehicle counting at intersections.

## ✨ Key Features

### 1. Accident Detection & Alerting
* **Model:** YOLOv8s (Fine-tuned on accident datasets).
* **Tracking:** ByteTrack for robust vehicle tracking across frames.
* **Alert System:** Automatically captures the accident frame and sends it alongside GPS coordinates to a dedicated Telegram channel (Hospital/Police) via Telegram Bot API.

### 2. Smart Traffic Light Control
* **Algorithm:** Deep Q-Network (DQN).
* **Mechanism:** Counts vehicle flow (density) at each lane using the tracking system and decides the optimal green light duration to minimize wait time.
* **Simulation:** Trained and validated using [SUMO / CityFlow / Custom Environment].

## 🏗 System Architecture

```mermaid
graph TD
    A[Camera Feed] -->|Input Stream| B(Object Detection - YOLOv8s)
    B --> C{Accident Detected?}
    C -- Yes --> D[Capture Image & Location]
    D --> E[Send Alert via Telegram API]
    E --> F[Hospital / Emergency Services]
    
    B --> G(Object Tracking - ByteTrack)
    G --> H[Count Vehicle Density]
    H --> I[DQN Agent]
    I -->|Action| J[Adjust Traffic Lights]
    J --> K[Traffic Signal Controller]