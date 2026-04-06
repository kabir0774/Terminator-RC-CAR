
# ⚡TERMINATOR— DIY Brushed RC Car

![Project Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)
![Motors](https://img.shields.io/badge/Motors-4x%20Johnson%201000RPM-orange)
![Remote](https://img.shields.io/badge/Remote-FlySky-red)

> *A fully DIY RC car built from scratch — custom Li-Ion battery pack, BTS7960 motor driver circuit, four Johnson motors, and FlySky RC control. No microcontroller. Pure hardware engineering.*

---

## 📸 Vehicle Photos

> *(Add your photos here — front view, side view, top view, internals)*

| Front View | Side View | Internals |
|------------|-----------|-----------|
| ![front](v-photos/front.jpg) | ![side](v-photos/side.jpg) | ![internals](v-photos/internals.jpg) |

---

## 🎯 Project Overview

**Terminator** is a custom-built brushed RC car designed and assembled entirely from scratch. The goal was to build a high-torque, responsive 4-wheel drive RC car using off-the-shelf components with a fully custom power and control circuit — no development board, no code.

The challenge: decode FlySky PPM signals, drive four Johnson motors bidirectionally, and power everything from a DIY Li-Ion battery pack — all in pure hardware.

---

## ⚙️ Specifications

| Parameter | Value |
|-----------|-------|
| **Drive System** | 4WD — Four Johnson DC Motors |
| **Motor Speed** | 1000 RPM |
| **Motor Driver** | BTS7960 (IBT-2) H-Bridge |
| **Remote System** | FlySky CT6B Transmitter |
| **Receiver** | FlySky FS-R6B |
| **Battery** | DIY Li-Ion Pack (custom built) |
| **Signal Type** | PPM from RC Receiver |
| **Control** | Direct RC — no microcontroller |
| **Signal decoding** |  360 degree servo motor chip has been connected in between reciever and motor driver to decode PPM signal to duty cycle PWM signal |

---

## 🔧 Electronic Systems

### Component List

| Component | Quantity | Function |
|-----------|----------|----------|
| Johnson DC Motor (1000 RPM) | 4 | Drive wheels |
| BTS7960 Motor Driver (IBT-2) | 2 | Bidirectional motor speed control |
| FlySky FS-R6B Receiver | 1 | Radio Frequency signal input from transmitter |
| Buck converter | 1 | Voltage drop to give power to motor driver brain and reciver |
| Li-Ion Cells (DIY Pack) | — | Main power source |
| Custom Circuit Board | 1 | Signal decoding + power distribution |


### How It Works

```
FlySky Transmitter
       ↓  (2.4GHz RF)
FlySky Receiver (FS-R6B)
       ↓  (PPM Signals — Ch1: Steering, Ch2: Throttle)
360 Degree servo motor chip
       ↓  (Decodes PPM to PWM signal)
BTS7960 Motor Drivers (x2)
       ↓
4x Johnson Motors (1000 RPM)
       ↑
DIY Li-Ion Battery Pack
```

### BTS7960 Motor Driver

The **BTS7960 (IBT-2)** is a high-current H-bridge capable of handling up to **43A peak current**, making it ideal for driving multiple brushed DC motors simultaneously. Two drivers are used — one for the left side motors, one for the right side.

- **Operating Voltage**: 6V – 27V
- **Peak Current**: 43A
- **Control**: PWM signal input for speed, direction pin for forward/reverse

### DIY Li-Ion Battery Pack

Rather than using an off-the-shelf battery, a custom Li-Ion pack was assembled from individual cells. This was one of the most challenging aspects of the build, requiring careful attention to cell matching, series/parallel configuration, and protection circuitry.

- Custom cell arrangement for required voltage and capacity
- Manual spot welding / connection
- Basic protection for over-discharge

---

## 📡 Signal Decoding

The FlySky receiver outputs standard **PPM signals** (1000µs – 2000µs pulse width):

| Channel | Function | PWM Range |
|---------|----------|-----------|
| CH1 | Steering (Left/Right) | 1000µs – 2000µs |
| CH2 | Throttle (Forward/Reverse) | 1000µs – 2000µs |

The custom circuit decodes these PPM signals and maps them to the BTS7960 driver inputs — translating stick position directly into motor speed and direction without any microcontroller.

---

## 🔌 Wiring Diagram

> ![circuit diagram](https://github.com/user-attachments/assets/2ae3c843-e5b9-49ed-9c5d-079ba83c1e84)



---

## 🎥 Demo Video

> *(Add your YouTube/drive link here)*

[![Demo Video](https://img.shields.io/badge/Watch-Demo%20Video-red?logo=youtube)](YOUR_VIDEO_LINK_HERE)

---

## 🧠 Engineering Challenges & Solutions

### 1. PWM Signal Decoding Without a Microcontroller
**Challenge**: Translating RC receiver PWM output to motor driver input purely in hardware.
**Solution**: Designed a custom circuit that directly interfaces receiver PWM signals with the BTS7960 enable and direction pins, eliminating the need for any microcontroller.

### 2. DIY Battery Pack
**Challenge**: Building a safe, reliable Li-Ion pack from scratch.
**Solution**: Carefully matched cells by internal resistance, configured for appropriate voltage, and added basic protection. This gave hands-on experience in battery engineering rarely seen at this level.

### 3. 4-Motor Torque Balance
**Challenge**: Ensuring all four 1000 RPM motors receive equal power for straight-line stability.
**Solution**: Paired motors on left/right sides to a single BTS7960 channel each, ensuring symmetric power delivery.

---

## 📁 Repository Structure

```
BLITZ-RC-Car/
├── src/           # Circuit design files / any logic diagrams
├── schemes/       # Wiring diagrams and schematics
├── v-photos/      # Vehicle photos (multi-angle)
├── t-photos/      # Builder photos
├── video/         # Demo video links
├── other/         # Datasheets, component references
└── README.md      # This file
```

---

## 🔮 Future Improvements

- [ ] Add Arduino Nano for telemetry (speed, battery voltage display)
- [ ] Upgrade to proper BMS for battery pack
- [ ] Add FPV camera for first-person driving
- [ ] Design custom PCB to replace breadboard/perfboard circuit
- [ ] Implement RPM feedback using motor encoders

---

## 👤 Builder

**Kabir** — First-year Robotics & AI Engineering Student, GNDEC Ludhiana

[![GitHub](https://img.shields.io/badge/GitHub-Kabir0774-black?logo=github)](https://github.com/Kabir0774)

---

## 📜 License

This project is licensed under the **MIT License** — feel free to use, modify, and build upon this work with attribution.

---

*Built from scratch. Every wire soldered by hand. 🔧*
