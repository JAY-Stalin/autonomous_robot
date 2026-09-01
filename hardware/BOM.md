# Bill of Materials (BOM)

Project: Autonomous 4-Wheel Robot
Author: Jay

---

# 1. Core Components

| Item         | Quantity | Specification         | Notes                  |
| ------------ | -------- | --------------------- | ---------------------- |
| Raspberry Pi | 1        | 8GB RAM               | Main processing unit   |
| Arduino      | 1        | Nano or Uno           | Motor + sensor control |
| MicroSD Card | 1        | 32–64 GB, Class 10    | Pi storage             |
| USB Cable    | 1        | USB A to Micro/Type-C | Pi ↔ Arduino           |

---

# 2. Motion System

| Item         | Quantity | Specification             | Notes               |
| ------------ | -------- | ------------------------- | ------------------- |
| DC Motors    | 4        | TT Gear Motors (~200 RPM) | Included in chassis |
| Wheels       | 4        | Diameter ~6.5 cm          | Confirmed           |
| Chassis      | 1        | 4WD base                  | Already owned       |
| Motor Mounts | 4        | Compatible with motors    | Usually included    |

---

# 3. Motor Control

| Item             | Quantity | Specification   | Notes                  |
| ---------------- | -------- | --------------- | ---------------------- |
| Motor Driver     | 1        | TB6612FNG       | Recommended over L298N |
| Jumper Wires     | ~20      | Male/Female mix | For connections        |
| Breadboard / PCB | 1        | Small           | Optional but useful    |

---

# 4. Sensors

| Item               | Quantity | Specification             | Notes              |
| ------------------ | -------- | ------------------------- | ------------------ |
| Ultrasonic Sensors | 3        | HC-SR04                   | Front, left, right |
| Camera             | 1        | Raspberry Pi Camera (CSI) | Required for CV    |

---

# 5. Power System

| Item           | Quantity | Specification    | Notes            |
| -------------- | -------- | ---------------- | ---------------- |
| Battery        | 1        | 7.4V Li-ion (2S) | Main power       |
| Battery Holder | 1        | 2-cell           | If not built-in  |
| Buck Converter | 1        | 7.4V → 5V (3A+)  | For Pi & Arduino |
| Power Switch   | 1        | Inline switch    | Safety           |
| Fuse           | 1        | 5A recommended   | Protect system   |

---

# 6. Mechanical & Assembly

| Item          | Quantity | Specification  | Notes            |
| ------------- | -------- | -------------- | ---------------- |
| Screws & Nuts | Assorted | M3 typical     | Mounting         |
| Standoffs     | 4–8      | Metal or nylon | For Pi mounting  |
| Zip Ties      | Few      | —              | Cable management |

---

# 7. Cooling

| Item     | Quantity | Specification    | Notes       |
| -------- | -------- | ---------------- | ----------- |
| Heatsink | 1 set    | For Raspberry Pi | Required    |
| Fan      | 1        | 5V               | Recommended |

---

# 8. Tools Required

| Tool           | Purpose         |
| -------------- | --------------- |
| Multimeter     | Voltage testing |
| Screwdrivers   | Assembly        |
| Soldering iron | Optional        |
| Laptop         | Programming     |

---

# 9. Estimated Electrical Load

| Component      | Current |
| -------------- | ------- |
| Raspberry Pi   | 2–3 A   |
| Arduino        | <0.2 A  |
| Motors (total) | 2–3 A   |
| Total Peak     | ~5 A    |

---

# 10. Notes

* The motor driver is to be powered from the arduino only
* The proper wire thickness for motor power lines must be used
* Battery must support the required current

---

# 11. Status Tracking

| Component          | Status |
| ------------------ | ------ |
| Raspberry Pi       | ☐      |
| Arduino            | ☐      |
| Motor Driver       | ☐      |
| Ultrasonic Sensors | ☐      |
| Camera             | ☐      |
| Battery            | ☐      |
| Buck Converter     | ☐      |

