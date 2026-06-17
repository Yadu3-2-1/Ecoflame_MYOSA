# 🔥 EcoFlame – Smart LPG Optimization & Safety System

> Transform any existing gas stove into a smart, efficient, and safety-aware cooking station — without modifying gas lines, burners, or cylinders.

![EcoFlame Cover](ecoflame-cover.jpg)

## 📖 Overview

EcoFlame is a non-invasive IoT-based retrofit solution that helps households reduce LPG wastage and improve kitchen safety. Built on the Myosa 5.0 platform, the system continuously monitors:

* 🔥 Flame quality
* 🎛️ Knob position
* 🍲 Vessel presence
* 🌡️ Ambient temperature

The system provides real-time feedback through an OLED display and a Blynk IoT mobile dashboard, helping users cook more efficiently while preventing gas wastage and unsafe operating conditions.

---

## 🚀 Key Features

### 🔥 Intelligent Flame Analysis

* Real-time flame color classification
* Detects:

  * Blue (Optimal)
  * Yellow (Soot/Waste)
  * Orange (Inefficient)
  * Red (Danger/Impurity)
  * Erratic Flame
  * No Flame

### 🎛️ Smart Knob Tracking

* MPU6050-based angle sensing
* Automatic 3-point calibration:

  * OFF
  * HIGH
  * SIMMER
* Works with different stove models without manual tuning

### 🍲 Vessel Detection

* Detects whether a cooking vessel is present
* Uses ambient light obstruction rather than proximity sensing
* Debounced for reliable operation

### 📊 Gas Efficiency Score

* Live efficiency score (0–100)
* Factors considered:

  * Flame quality
  * Knob position
  * Vessel presence
  * Temperature

### ⏱️ Cooking Session Analytics

* Tracks cooking duration
* Stores last session statistics
* Pushes session summaries to Blynk

### 🚨 Safety Monitoring

* Flame-out detection
* Gas waste alerts
* Overheating alerts
* Long-idle warnings
* Poor combustion warnings

### 📱 IoT Dashboard

* Live stove status
* Efficiency gauge
* Cooking timer
* Alert management
* Historical session data

---

## 🏗️ System Architecture

```text
          ┌──────────────┐
          │  Gas Stove   │
          └──────┬───────┘
                 │
   ┌─────────────┼─────────────┐
   │             │             │
 APDS9960     MPU6050       BMP180
 Flame       Knob Angle    Temperature
 Sensor      Tracking      Monitoring
   │             │             │
   └─────────────┼─────────────┘
                 │
             ESP32
                 │
      ┌──────────┴──────────┐
      │                     │
   OLED Display        Blynk Cloud
      │                     │
      └──────────┬──────────┘
                 │
              User
```

---

## 🛠️ Hardware Components

| Component          | Purpose                        |
| ------------------ | ------------------------------ |
| ESP32 Dev Module   | Main Controller                |
| APDS9960           | Flame Color & Vessel Detection |
| MPU6050            | Knob Position Tracking         |
| BMP180             | Temperature Monitoring         |
| SSD1306 OLED       | Local Display                  |
| Myosa 5.0 Mini-Kit | Sensor Platform                |

---

## 📱 Blynk Dashboard

| Virtual Pin | Function              |
| ----------- | --------------------- |
| V1          | Knob State            |
| V2          | Flame Status          |
| V3          | Alert Status          |
| V4          | Alert Dismiss Button  |
| V5          | Efficiency Score      |
| V6          | Cooking Time          |
| V8          | Last Session Score    |
| V9          | Last Session Duration |

---

## 🚨 Alert Types

| Alert         | Trigger                           |
| ------------- | --------------------------------- |
| Overheat      | Temperature > 60°C                |
| Gas Waste     | Stove ON without vessel           |
| Long Idle     | High flame for prolonged duration |
| Flame Out     | Gas ON but flame absent           |
| Flame Quality | Poor combustion detected          |

---

## ⚙️ Installation

### 1. Install Required Libraries

```text
Blynk
Adafruit APDS9960
Adafruit MPU6050
Adafruit BMP085 Unified
Adafruit SSD1306
Adafruit GFX
Adafruit Unified Sensor
```

### 2. Configure Credentials

```cpp
#define BLYNK_TEMPLATE_ID   "YOUR_TEMPLATE_ID"
#define BLYNK_TEMPLATE_NAME "EcoFlame"
#define BLYNK_AUTH_TOKEN    "YOUR_AUTH_TOKEN"

char ssid[] = "YOUR_WIFI_SSID";
char pass[] = "YOUR_WIFI_PASSWORD";
```

### 3. Upload Firmware

1. Install ESP32 Board Package
2. Select **ESP32 Dev Module**
3. Connect the board
4. Upload `ecoflame.ino`

---

## 🔧 Startup Calibration

Each boot performs a guided calibration:

```text
OFF Position
      ↓
HIGH Position
      ↓
SIMMER Position
      ↓
System Ready
```

This allows EcoFlame to adapt automatically to different stove designs.

---

## 📂 Project Structure

```text
EcoFlame/
│
├── ecoflame.ino
├── README.md
├── ecoflame-cover.jpg
├── ecoflame-blynk-dashboard.jpg
├── ecoflame-oled-screens.jpg
├── ecoflame-calibration.jpg
├── ecoflame-demo.mp4
└── docs/
```

---

## 🧠 Technology Stack

* ESP32
* Arduino Framework (C++)
* Blynk IoT
* Myosa 5.0 Platform
* APDS9960
* MPU6050
* BMP180
* SSD1306 OLED

---

## 👥 Team

**EcoFlame Team**

* Ashlin Mariya
* Nakul Menon
* Yadunandan K P

---

## 🙏 Acknowledgements

Built as part of the **Myosa Innovation Competition** under the theme:

**Energy Conservation & Smart Home**

We extend our sincere gratitude to **Professor Sreeram** for his invaluable mentorship, guidance, and continuous support throughout the development of EcoFlame.

We would also like to thank **Vimal John M V**, whose insights and discussions served as the inspiration behind the EcoFlame concept.

Special thanks to the **Myosa platform** for providing the sensor ecosystem that enabled innovative hardware repurposing and rapid IoT prototyping, making EcoFlame possible.

---

## 📜 License

This project is released for educational and research purposes.

Feel free to fork, improve, and contribute.
