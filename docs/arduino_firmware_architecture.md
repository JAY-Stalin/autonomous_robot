
# Arduino Firmware Architecture

Project: Autonomous 4-Wheel Robot
Controller: Arduino (Nano / Uno)
Role: Real-time control layer

---

## 1. Firmware Responsibilities

The Arduino is responsible for all **time-critical physical interaction** with the robot.

### Core duties

* Motor PWM control
* Direction control
* Ultrasonic sensor acquisition
* Serial command reception
* Safety overrides
* Telemetry feedback to Raspberry Pi

The Arduino must operate safely even if the Raspberry Pi fails.

---

## 2. Architectural Philosophy

### Key principles

* Modular design
* Hardware abstraction
* Non-blocking logic
* Safety priority
* Deterministic loop timing

The Arduino loop must never contain long blocking delays.

---

## 3. Module Overview

The firmware is divided into functional modules.

### 3.1 Motor Control Module

**Purpose**

* Abstract motor driver hardware
* Provide high-level motion primitives

**Responsibilities**

* Set wheel speeds
* Direction control
* Stop motors
* Tank steering support

**Interface**

* setSpeed(left, right)
* stopMotors()
* moveForward(speed)
* rotateLeft(speed)

---

### 3.2 Ultrasonic Module

**Purpose**

* Read three ultrasonic sensors
* Provide filtered distance values

**Responsibilities**

* Trigger pulses
* Echo timing
* Distance conversion
* Basic noise mitigation

**Interface**

* readFront()
* readLeft()
* readRight()
* getDistances()

---

### 3.3 Serial Parser Module

**Purpose**

* Interpret commands from Raspberry Pi

**Responsibilities**

* Receive ASCII commands
* Parse tokens
* Validate commands
* Dispatch actions

**Supported commands**

* FWD
* BACK
* LEFT
* RIGHT
* STOP

---

### 3.4 Safety Module

**Purpose**

* Enforce collision avoidance independent of Pi

**Responsibilities**

* Emergency stop threshold
* Command timeout watchdog
* Override motion commands

**Safety rules**

* Front < 20 cm → stop
* No command for 1000 ms → stop

---

### 3.5 Telemetry Module

**Purpose**

* Provide robot state to Raspberry Pi

**Responsibilities**

* Send distance measurements
* Send emergency events
* Send command acknowledgments

---

## 4. File Structure

```
firmware/arduino/
├── main.ino
├── motor_control.h
├── motor_control.cpp
├── ultrasonic.h
├── ultrasonic.cpp
├── serial_parser.h
├── serial_parser.cpp
├── safety.h
├── safety.cpp
└── telemetry.h
```

This separation allows independent testing of each subsystem.

---

## 5. Data Flow

### Command path

Raspberry Pi → Serial → Parser → Motor Control

### Sensor path

Ultrasonic → Safety → Telemetry → Raspberry Pi

### Override path

Ultrasonic → Safety → Motor Control (direct)

Safety always has highest priority.

---

## 6. Main Loop Concept

The loop executes continuously with no blocking delays.

Sequence:

1. Read serial input
2. Update ultrasonic distances
3. Evaluate safety conditions
4. Execute motion commands
5. Send telemetry
6. Repeat

This creates a cooperative scheduling model.

---

## 7. Timing Targets

| Task                | Rate       |
| ------------------- | ---------- |
| Serial processing   | Continuous |
| Ultrasonic sampling | ~10 Hz     |
| Safety evaluation   | Every loop |
| Telemetry update    | ~5–10 Hz   |

---

## 8. Debug Strategy

### Unit-level

* Test serial parser via monitor
* Mock ultrasonic values
* Motor test without sensors

### Integration-level

* Serial + motor
* Ultrasonic + safety
* Full loop

---

## 9. Future Extensions

* Encoder support
* PID speed control
* IMU integration
* Battery monitoring
* Motion profiles

Architecture is designed to accommodate these without refactor.

---

## 10. Design Guarantee

The Arduino firmware guarantees:

* Safe stopping
* Deterministic motor behavior
* Continuous sensing
* Robust command handling

Even in case of Raspberry Pi failure.
