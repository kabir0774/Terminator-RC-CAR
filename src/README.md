# 🔧 Source & Circuit Design Files

This directory contains the **core logic, signal processing concepts, and circuit-level design philosophy** behind the BLITZ RC Car.

Unlike conventional RC systems that rely on microcontrollers, this project demonstrates **pure hardware-based signal decoding and control**.

---

## 🧠 System Philosophy

> ⚡ *"No code. No microcontroller. Only hardware intelligence."*

The system directly converts **RC PWM signals → motor control signals** using analog/digital circuitry.

---

## 🧩 Functional Overview
RC Receiver (PWM Output)
│
▼
Signal Conditioning Stage
│
▼
PWM Interpretation Logic
│
▼
Direction + Speed Separation
│
▼
Motor Driver Interface (BTS7960)

---

## 📡 Signal Characteristics

| Parameter | Value |
|----------|------|
| Signal Type | PWM (Pulse Width Modulation) |
| Frequency | ~50 Hz |
| Pulse Width | 1000µs – 2000µs |
| Neutral | 1500µs |

---

## ⚙️ Signal Interpretation Logic

| Input Pulse | Action |
|------------|-------|
| < 1500µs | Reverse |
| = 1500µs | Stop |
| > 1500µs | Forward |

---

## 🔄 Logic Mapping
Throttle Input (CH2)
│
├──► Forward → RPWM ↑
│
└──► Reverse → LPWM ↑

---

## 🔌 Hardware Design Considerations

### 1. Voltage Stability
- Logic circuits require **stable 5V**
- Provided via LM2596 buck converter

### 2. Noise Handling
- PWM signals are sensitive to noise
- Short signal wires recommended

### 3. Grounding Strategy
> ⚠️ ALL components must share a common ground

---

## 📊 Design Advantages

- ✅ Zero latency (no software processing)
- ✅ Extremely reliable
- ✅ Simple architecture
- ❌ Less flexible than programmable systems

---

## 🚧 Future Scope

- PCB design (KiCad)
- Analog filtering improvements
- Signal smoothing circuits

---

## 📎 Notes

This folder may include:
- Circuit diagrams
- Logic sketches
- Simulation files (future)
