# autonomous_robot
# Autonomous 4-Wheel Robot Platform

Author: Jay  
Status: Planning Phase 

---

## Project Goal

Building a 4-wheel autonomous robot with:

- Raspberry Pi (8GB) for Computer Vision & Quantized ML
- Arduino for motor control and ultrasonic sensing
- 3 fixed ultrasonic sensors (front, left[45 deg], right[45 deg])
- CSI camera for live feed and object detection
- Serial communication between Pi and Arduino

---

## Architecture Overview

High-Level Brain:
- Raspberry Pi
- OpenCV
- TensorFlow Lite (INT8 quantized model)
- Navigation logic

Low-Level Controller:
- Arduino
- PWM motor control
- Ultrasonic sensor management
- Emergency safety override

---

## Design Philosophy

-  Motors handled by Arduino for lowlevel machine control
- Ultrasonic safety overrides ML decisions
- System must fail safely
- Modular design for future upgrades

---

##  Hardware

- Raspberry Pi 8GB
- Arduino  Uno R3
- TB6612FNG motor driver
- 4 DC geared motors
- 3x HC-SR04 ultrasonic sensors
- Pi Camera (CSI)
- 2S Li-ion battery (7.4V)
- Buck converter (5V regulated)

---

##  Features 

- Obstacle avoidance
- Person detection (quantized model)
- Serial command protocol
- Autonomous navigation state machine

---

## Future Upgrades

- Inertial Measurement Unit (IMU) integration
- SLAM with Lidar
- Web dashboard / Mobile App
- Edge TPU acceleration for ML model

---

## Project Roadmap

### Phase 1 – Documentation
- [ ] System architecture
- [ ] Interfaces definition
- [ ] Pin mapping locked
- [ ] Power distribution plan

### Phase 2 – Arduino Development
- [ ] Motor control module
- [ ] Ultrasonic module
- [ ] Serial protocol implementation
- [ ] Safety timeout

### Phase 3 – Raspberry Pi Setup
- [ ] Camera integration
- [ ] TFLite object detection
- [ ] Serial communication

### Phase 4 – Integration
- [ ] End-to-end movement
- [ ] Obstacle avoidance
- [ ] Object-aware navigation

---

 
