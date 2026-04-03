# Power grid Monitor
Arduino-based Power grid Monitor that monitors real-time current draw and automatically toggles a DC fan using a MOSFET. Includes overcurrent protection logic, OLED display for system diagnostics, and estimated RPM calculation based on current sensing. Built using C++ and the Adafruit SSD1306 graphics library.
---
## 📌 Features

- ✅ Automatic fan ON/OFF control based on current threshold
- ⚠️ Cooldown delay after overcurrent detection
- 📟 OLED display shows:
  - Fan status (ON/OFF)
  - Real-time current (A)
  - Estimated fan RPM
- 🪛 MOSFET switching with flyback protection
- 📊 Serial monitor output for diagnostics/logging

---

## 🧰 Hardware Components

| Component             | Purpose                          |
|-----------------------|----------------------------------|
| Arduino Uno (or clone)| Main microcontroller             |
| IRF540N MOSFET        | Fan switching control            |
| ACS712 Current Sensor | Measures current draw of the fan |
| SSD1306 OLED Display  | Shows status, current, and RPM   |
| 12V DC Fan            | Target load                      |
| Flyback Diode (1N5822 or 1N4007) | Protects MOSFET from back EMF  |
| 220Ω + 10kΩ resistors | Gate control and pull-down       |
| Breadboard + wires    | Prototyping and connections      |
| 12V DC power supply   | Powers fan and load              |

---
## 🔌 Wiring Overview

- **MOSFET Gate** → Arduino Digital Pin (via 220Ω resistor), with 10kΩ pull-down to GND  
- **MOSFET Drain** → Negative terminal of the fan  
- **MOSFET Source** → GND  
- **Fan Positive** → +12V Power  
- **Flyback Diode** → Across fan terminals (stripe side to +12V)  
- **ACS712**:
  - `VCC` → Arduino `5V`
  - `GND` → Arduino `GND`
  - `OUT` → Arduino `A0`
- **OLED Display**:
  - `VCC` → Arduino `5V`
  - `GND` → Arduino `GND`
  - `SCL` → Arduino `A5`
  - `SDA` → Arduino `A4`

---

## 🧠 How It Works

1. Reads analog voltage from the current sensor.
2. Calculates current and estimates RPM.
3. If current is within safe range, fan stays ON.
4. If current exceeds a threshold, fan shuts down and enters a cooldown phase.
5. All key stats are displayed on the OLED.

---

## 📸 Preview

![image](https://github.com/user-attachments/assets/528935b4-bf2c-4e05-8c86-5a6a862e84e7)


---
