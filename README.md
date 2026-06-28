# Smart Plant Mood Monitor 🌿

An Arduino-based IoT project that gives a plant a "voice" — fusing soil moisture and ambient light readings into one of four personality-driven mood messages, displayed live on an OLED screen. Designed and simulated entirely in **Cirkit Designer**.

**Author:** Mallampally Jayantha Siva Srinivas

---

## 📌 Project Overview

The Smart Plant Mood Monitor continuously reads two analog sensors — a soil moisture sensor and a photoresistor (LDR) — and combines their values to decide how the plant is "feeling." The result is shown as a short, expressive message on a 128×64 I2C OLED display, updated every 2 seconds.

| Project Title | Smart Plant Mood Monitor |
|---|---|
| **Software** | Cirkit Designer |
| **Microcontroller** | Arduino UNO (ATmega328P) |
| **Programming Language** | C++ (Arduino Framework) |
| **Sensors Used** | SparkFun Soil Moisture Sensor + Photoresistor (LDR) Module |
| **Display** | OLED 128×64 I2C Monochrome (SSD1306, address `0x3C`) |
| **Libraries Required** | `Wire.h`, `Adafruit_GFX.h`, `Adafruit_SSD1306.h` |
| **Mood States** | Cold & Thirsty / Water Me Please / Sleepy / I Feel Great |
| **Update Interval** | Every 2 seconds |

---

## 🧩 Components Required

| Component | Specification / Role | Pin | Qty |
|---|---|---|---|
| Arduino UNO | ATmega328P, central MCU | — | 1 |
| SparkFun Soil Moisture Sensor | Analog output, measures soil conductivity | A0 | 1 |
| Photoresistor (LDR) Module | Analog output, measures ambient light | A1 | 1 |
| OLED 128×64 I2C Display | SSD1306 controller, monochrome | SDA/SCL (I2C) | 1 |
| Resistors (200 Ω) | Current limiting for sensor signal lines | — | 2 |
| Breadboard | Component interconnection | — | 1 |
| Jumper Wires | Male-to-Male | — | Many |
| USB Cable | Type-A to Type-B, powers Arduino | — | 1 |

## 🔌 Circuit Connections

| Connection | Target |
|---|---|
| Soil Sensor – VCC | 5V rail |
| Soil Sensor – GND | GND rail |
| Soil Sensor – SIG | Arduino A0 (via 200Ω resistor) |
| LDR Module – VCC | 5V rail |
| LDR Module – GND | GND rail |
| LDR Module – AO | Arduino A1 (via 200Ω resistor) |
| OLED – VDD | 3.3V or 5V rail |
| OLED – GND | GND rail |
| OLED – SDA | Arduino A4 (Hardware I2C SDA) |
| OLED – SCL | Arduino A5 (Hardware I2C SCL) |

---

## 🧠 Mood Decision Logic

| Soil Moisture | Light Level | OLED Message |
|---|---|---|
| < 300 (Dry) | < 300 (Dark) | "Cold & Thirsty!" |
| < 300 (Dry) | ≥ 300 (Bright) | "Water Me Please!" |
| ≥ 300 (Moist) | < 300 (Dark) | "Sleepy zzz..." |
| ≥ 300 (Moist) | ≥ 300 (Bright) | "I Feel Great!" |

---

## 💻 How It Works

1. The soil moisture sensor is read on A0; values below 300 indicate dry soil
2. The LDR is read on A1; values below 300 indicate darkness
3. A 2-level conditional check evaluates both readings to determine the mood
4. The OLED clears and redraws with a "Plant Mood" title, a separator line, a large mood headline, and a smaller sub-message
5. The cycle repeats every 2 seconds

---

## 🛠️ Tools & Technologies

- **Hardware Platform:** Arduino UNO (ATmega328P)
- **Simulation Tool:** Cirkit Designer
- **Language:** Arduino C++
- **Concepts Covered:** Multi-sensor analog reading, I2C communication, conditional decision logic, modular function design

## 🎯 Learning Outcomes

- Reading multiple analog sensors (soil moisture + LDR) on separate Arduino analog pins
- I2C protocol for interfacing the SSD1306 OLED display
- Multi-variable conditional logic for sensor-driven decision making
- Modular function design to keep the main loop clean and readable
- Hands-on simulation workflow in Cirkit Designer, including library management

## 🚀 Future Scope

- Add a buzzer or RGB indicator for an additional sensory mood cue
- Log sensor history over time and visualize moisture/light trends
- Move from simulation to a physical build with real soil/light sensors and a battery-powered enclosure
- Add Wi-Fi (ESP32) for remote mood notifications via an app or webpage

---

*Smart Plant Mood Monitor — Simulated in Cirkit Designer — June 2026*
