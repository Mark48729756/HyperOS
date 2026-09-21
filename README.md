<div align="center">

# 🚀 Project Name / Hardware Hub
*Advanced Microcontroller & Sensor Integration Framework*

[![Version](https://img.shields.io/badge/version-1.303.1-blue.svg?style=flat-square)](../../releases/tag/v1.303.1)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg?style=flat-square)]()
[![Platform](https://img.shields.io/badge/platform-ESP32%20%2F%20Arduino-orange.svg?style=flat-square)]()

</div>

---

## 📖 About The Project

Welcome to the official repository! This project bridges high-performance hardware interfacing with clean, modular software architecture. Designed for engineers, hobbyists, and IoT developers, it provides robust communication protocols, real-time telemetry, and optimized pin configurations.

---

## 📌 Ultimate Pinout Reference

Below is the complete, high-resolution pin mapping table for version `1.303.1`. Ensure your wiring matches these specifications to prevent hardware conflicts.

| Pin Label | Hardware Pin | Primary Function | Alternate Function / Notes |
| :--- | :--- | :--- | :--- |
| **GND** | GND | Common Ground | System Reference Ground |
| **3V3** | 3.3V OUT | Power Output | Max current: 500mA |
| **5V** | VIN / 5V | Power Input/Output | USB Bus Voltage Pass-through |
| **GPIO 0** | D0 | Boot / IO | Pulled up internally (Avoid heavy external pull-downs) |
| **GPIO 1** | TX0 | UART0 TX | Debug Serial Output |
| **GPIO 3** | RX0 | UART0 RX | Debug Serial Input |
| **GPIO 4** | D4 | I2C SDA | Data line for external sensors |
| **GPIO 5** | D5 | I2C SCL | Clock line for external sensors |
| **GPIO 12** | MISO | SPI Master In Slave Out | Shared SPI Bus |
| **GPIO 13** | MOSI | SPI Master Out Slave In | Shared SPI Bus |
| **GPIO 14** | SCK | SPI Serial Clock | Shared SPI Bus |
| **GPIO 15** | CS | SPI Chip Select | Active Low |
| **GPIO 21** | SDA_EXT | Secondary I2C SDA | Reserved for expansion modules |
| **GPIO 22** | SCL_EXT | Secondary I2C SCL | Reserved for expansion modules |
| **GPIO 34** | ADC1_CH6 | Analog Input (3.3V Max) | High-impedance sensor reading |
| **GPIO 35** | ADC1_CH7 | Analog Input (3.3V Max) | Battery voltage monitoring |

> ⚠️ **Warning:** Never apply voltages higher than $3.3\text{V}$ to standard GPIO pins. Doing so may permanently damage the microcontroller.

---

## 🛠️ Wiring Diagram Schematics

```text
       +-----------------------------------------+
       |               MICROCONTROLLER           |
       |                                         |
       |   [3V3] --------+---------------------+ |
       |                 |                     | |
       |   [GND] --------+--------+            | |
       |                          |            | |
       |   [GPIO 4 (SDA)] ---+    |            | |
       |                     |    |            | |
       |   [GPIO 5 (SCL)] ---+--+ |            | |
       |                         ||            | |
       +-------------------------||------------+ |
                                 ||
            +--------------------+|
            |                     |
            v                     v
      +-----------+         +-----------+
      | Sensor A  |         | Sensor B  |
      |   (I2C)   |         |   (I2C)   |
      +-----------+         +-----------+
```

---

## 🔄 Changelog

### Version 1.303.1 (Latest) — *Telemetry & Pin Mapping Revamp*

This patch release focuses on stability improvements, pin mapping reorganizations, and major telemetry enhancements requested by the community.

* ✨ **New Features:**
  * Added dynamic real-time telemetry streaming over WebSockets.
  * Introduced secondary I2C expansion support on `GPIO 21` and `GPIO 22`.
  * Integrated automated pin-conflict detection during the boot sequence.
* ⚡ **Performance Improvements:**
  * Optimized analog-to-digital converter (`ADC`) polling intervals, reducing CPU load by $14\%$.
  * Refactored SPI bus communication loops for lower latency.
* 🐛 **Bug Fixes:**
  * Fixed an intermittent crash caused by floating states on `GPIO 0` during cold boots.
  * Resolved a memory leak in the background logging daemon.
  * Corrected minor typos in the hardware documentation mapping table.

---

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```
2. **Open the workspace** in your preferred IDE (VS Code / PlatformIO).
3. **Verify your wiring** against the [Pinout Reference](#-ultimate-pinout-reference).
4. **Build and Flash:**
   ```bash
   pio run --target upload
   ```

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
