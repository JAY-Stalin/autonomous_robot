# Integration Sequence Document

Project: Autonomous 4-Wheel Robot  
Purpose: Define exact step-by-step bring-up order  

---

# Integration Philosophy

Only integrate one new subsystem at a time.

If something breaks, you must know exactly what caused it.

Rule:
NEVER integrate two unknowns simultaneously.

---

# Phase 1 — Arduino Bring-Up (No Raspberry Pi)

Goal: Verify all low-level hardware works independently.

---

## Step 1.1 — Power System Test

- Power battery
- Verify 5V from buck converter
- Measure voltage with multimeter
- Ensure common ground connected

Success criteria:
- Stable 5V
- No overheating
- No voltage drop under idle

---

## Step 1.2 — Motor Driver Test

- Upload simple motor test sketch
- Run motors forward
- Run motors backward
- Test left/right rotation

Success criteria:
- Smooth motion
- No driver overheating
- No unexpected resets

---

## Step 1.3 — Ultrasonic Sensor Test

- Upload sensor-only test sketch
- Print front/left/right distances
- Test at multiple distances
- Check for noise and false readings

Success criteria:
- Stable readings
- Reasonable accuracy (±2 cm)
- No freezing

---

## Step 1.4 — Safety Logic Test

- Add emergency stop threshold
- Simulate obstacle (<20 cm)
- Confirm motors stop immediately

Success criteria:
- Instant motor halt
- Reliable override behavior

---

# Phase 2 — Serial Communication (Still No ML)

Goal: Connect Raspberry Pi to Arduino safely.

---

## Step 2.1 — Basic Serial Handshake

- Connect Pi via USB
- Open serial at 115200
- Send "FWD 100"
- Arduino responds "OK"

Success criteria:
- Reliable communication
- No garbled data

---

## Step 2.2 — Command Timeout Test

- Send movement command
- Stop sending data
- Verify Arduino stops after 1000 ms

Success criteria:
- Safe fail behavior confirmed

---

# Phase 3 — Raspberry Pi Camera Bring-Up

Goal: Verify CV pipeline independently.

---

## Step 3.1 — Camera Test

- Install camera drivers
- Display live feed
- Confirm stable FPS

Success criteria:
- Stable video stream
- No overheating

---

## Step 3.2 — ML Inference Test

- Run quantized model
- Measure FPS
- Confirm detection working

Success criteria:
- Acceptable FPS (>5–10 FPS)
- Correct detections

---

# Phase 4 — Controlled Integration

Goal: Combine systems gradually.

---

## Step 4.1 — Pi Sends Manual Commands

- Keyboard control on Pi
- Send movement commands
- Verify response

Success criteria:
- Immediate motion response
- No lag

---

## Step 4.2 — Add Ultrasonic Feedback to Pi

- Arduino sends DIST messages
- Pi prints distances

Success criteria:
- Stable telemetry
- No blocking behavior

---

## Step 4.3 — Autonomous Obstacle Avoidance

- Disable ML
- Use only ultrasonic
- Implement simple logic

Success criteria:
- Robot avoids obstacles reliably

---

# Phase 5 — Full Autonomy

Goal: Enable ML decision layer.

---

## Step 5.1 — Object Detection Stops Robot

- Detect person
- Send STOP command

Success criteria:
- Reliable behavior
- No safety violation

---

## Step 5.2 — Full Behavior Loop

- ML + Ultrasonic
- Navigation state machine active

Success criteria:
- Stable movement
- No oscillation
- No crashes

---

# Debugging Rule

If failure occurs:
1. Revert to previous successful phase.
2. Verify subsystem independently.
3. Reintegrate carefully.

Never debug full system blindly.

---

# Final Acceptance Criteria (v1.0)

- Robot moves forward autonomously
- Avoids obstacles
- Stops for detected object
- Recovers and continues
- No unsafe behavior
