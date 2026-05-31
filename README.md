# ☀️ Solar Monitoring System — 2S2P Configuration

> **ESP32 + Blynk IoT | Real-Time Solar Panel Monitoring with Cloud Dashboard**

A complete solar panel monitoring system for a **2S2P (2 Series, 2 Parallel) 4-panel array** with real-time cloud monitoring via Blynk, multi-sensor data fusion, gas detection alerts, and a rotating LCD display.

---

## 🌟 Features

| Feature | Details |
|---|---|
| ☀️ **Solar Monitoring** | Voltage, Current, Power (2S2P array) |
| 🌡️ **Environmental** | Temperature & Humidity (DHT11) |
| 💨 **Gas Detection** | Smoke/LPG/CO (MQ2) + Air Quality (MQ135) |
| 🌊 **Atmospheric** | Pressure & Temperature (BMP180) |
| 📱 **Cloud Dashboard** | Blynk IoT — monitor anywhere |
| 📺 **Local LCD** | 5-page rotating 16×2 display |
| 🔔 **Smart Alerts** | Blynk push notifications on gas detection |
| 📶 **WiFi Auto-Reconnect** | Reconnects every 30s if disconnected |

---

## 🔌 Hardware

### Pin Configuration
| Sensor | Pin | Purpose |
|---|---|---|
| Voltage Sensor | GPIO 34 | Solar panel voltage |
| ACS712 | GPIO 35 | Solar current |
| DHT11 | GPIO 4 | Temp + Humidity |
| MQ2 | GPIO 32 | Smoke/Gas detection |
| MQ135 | GPIO 33 | Air quality |
| BMP180 | I2C (21,22) | Pressure sensor |
| LCD | I2C (21,22) | Display |

### Components Required
- ESP32 DevKit
- Voltage Divider Module (R1=20kΩ, R2=10kΩ)
- ACS712 Current Sensor (5A/20A/30A)
- DHT11 Temperature & Humidity Sensor
- MQ2 Gas Sensor
- MQ135 Air Quality Sensor
- BMP180 Pressure Sensor
- 16×2 I2C LCD (0x27)

---

## 📊 Calibration Values

```cpp
#define R1                   20000.0    // Voltage divider R1
#define R2                   10000.0    // Voltage divider R2
#define ACS712_SENSITIVITY   185.0      // mV/A (5A version)
#define MQ2_THRESHOLD        600        // Gas alert threshold
#define MQ135_THRESHOLD      700        // Air quality threshold
```

---

## 📱 Blynk Virtual Pins

| Virtual Pin | Data |
|---|---|
| V10 | Solar Voltage (V) |
| V11 | Solar Current (A) |
| V12 | Solar Power (W) |
| V13 | Temperature (°C) |
| V14 | Humidity (%) |
| V20 | MQ2 Status |
| V21 | MQ135 Status |
| V22 | Atmospheric Pressure |
| V18 | BMP180 Temperature |
| V19 | Overall Gas Alert |

---

## 🖥️ LCD Display Pages

```
Page 1: Solar Voltage + Current
Page 2: Solar Power + Status
Page 3: Temperature + Humidity
Page 4: MQ2 + MQ135 Status
Page 5: BMP180 Pressure + Temp
```

**Gas Alert (overrides all pages):**
```
⚠ MQ2  DETECTED!
Smoke/LPG/CO !!
```

---

## 🚀 Setup

### 1. Install Libraries
```
- BlynkSimpleEsp32
- LiquidCrystal_I2C
- DHT sensor library
- Adafruit BMP085
```

### 2. Configure WiFi & Blynk
```cpp
char ssid[] = "YourWiFiName";
char pass[] = "YourPassword";
#define BLYNK_AUTH_TOKEN "YourBlynkToken"
```

### 3. Create Blynk Template
- Go to blynk.cloud
- Create datastreams for V10–V22
- Configure event: `gas_alert`

### 4. Upload & Monitor
- Flash to ESP32
- Open Blynk app on phone
- Monitor solar output remotely!

---

## ⚡ Solar Array Specs (2S2P)

```
2 panels in Series  → doubles voltage
2 pairs in Parallel → doubles current

Example: 4 × 5V/2A panels
  2S = 10V per string
  2P = 4A total
  Total Power = 40W theoretical
```

---

## 🛠️ Skills Demonstrated

`ESP32` `Blynk IoT` `WiFi` `DHT11` `BMP180` `MQ2` `MQ135` `ACS712` `Voltage Sensing` `Cloud IoT` `Multi-Sensor Fusion` `Solar Energy` `MQTT` `Embedded C++`

---

## 👨‍💻 Developer

**Bhagathi Gangadhar**
B.Tech ECE — RVR & JC College of Engineering, Guntur
📧 gangadharbhagathi@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/gangadhara-bagathi-44657429a)
