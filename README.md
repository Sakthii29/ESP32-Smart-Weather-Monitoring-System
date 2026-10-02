# ESP32 Smart Weather Monitoring System

An **IoT-based weather monitoring system** built using an **ESP32** and multiple environmental sensors. The system collects real-time environmental data and displays it through a **Wi-Fi-based web dashboard**.

## 🌦️ Project Overview

This project is designed to monitor environmental conditions using an ESP32 microcontroller. Sensor readings are collected, processed, and displayed on a web interface that can be accessed from a phone or computer connected to the same Wi-Fi network.

The system can monitor:

* 🌡️ Temperature
* 💧 Humidity
* 🌤️ Atmospheric pressure
* 💨 Air-quality/gas sensor readings
* 🌧️ Rain detection

## 🔧 Hardware Components

| Component        | Purpose                                 |
| ---------------- | --------------------------------------- |
| ESP32            | Main controller and Wi-Fi communication |
| DHT11            | Temperature and humidity                |
| BMP180/BMP280    | Atmospheric pressure                    |
| MQ-series sensor | Air-quality/gas sensing                 |
| Rain sensor      | Rain/water detection                    |
| Breadboard       | Circuit assembly                        |
| Jumper wires     | Electrical connections                  |

## 🔌 Pin Configuration

### DHT11

```text
DHT11 VCC   → ESP32 3.3V
DHT11 DATA  → GPIO 4
DHT11 GND   → ESP32 GND
```

### BMP180

```text
BMP180 VCC → ESP32 3.3V
BMP180 GND → ESP32 GND
BMP180 SDA → GPIO 21
BMP180 SCL → GPIO 22
```

### MQ Sensor

```text
MQ VCC → ESP32 VIN/5V
MQ GND → ESP32 GND
MQ AO  → GPIO 34 through voltage divider
```

> **Important:** Do not connect a potentially 5V MQ analog output directly to an ESP32 ADC pin. Use an appropriate voltage divider to keep the ESP32 input within its safe voltage range.

### Rain Sensor

```text
Rain VCC → ESP32 3.3V
Rain GND → ESP32 GND
Rain AO  → GPIO 35
```

## 💻 Software Requirements

* Arduino IDE
* ESP32 board package
* DHT sensor library
* Adafruit Unified Sensor library
* Appropriate BMP180/BMP280 library
* Wi-Fi network

## 📚 Libraries

Install the required libraries through:

**Arduino IDE → Sketch → Include Library → Manage Libraries**

Required:

```text
DHT sensor library by Adafruit
Adafruit Unified Sensor
Adafruit BMP085 Library
```

If your pressure sensor is a **BMP280**, use the appropriate BMP280 library instead.

## 🚀 How It Works

```text
Environmental Sensors
        ↓
      ESP32
        ↓
   Data Processing
        ↓
      Wi-Fi
        ↓
   Web Server
        ↓
Phone / Computer Dashboard
```

The ESP32 reads the sensor values and hosts a simple web server. After connecting the ESP32 to Wi-Fi, the assigned IP address can be opened in a browser to view the sensor readings.

## 🌐 Web Dashboard

The dashboard displays information such as:

```text
ESP32 Weather Station

Temperature
28.5 °C

Humidity
65 %

Atmospheric Pressure
1010 hPa

Air Quality Sensor
750

Rain Sensor
NO RAIN
```

The webpage can automatically refresh to show updated readings.

## 📁 Project Structure

```text
ESP32-Smart-Weather-Monitoring-System/
│
├── ESP32_Smart_Weather_Station.ino
├── README.md
└── images/
    ├── circuit.jpg
    └── dashboard.jpg
```

## ⚙️ Setup

1. Connect all sensors to the ESP32 according to the pin configuration.
2. Install the required Arduino libraries.
3. Open the `.ino` file in Arduino IDE.
4. Enter your Wi-Fi credentials:

```cpp
const char* ssid = "YOUR_WIFI_NAME";
const char* password = "YOUR_WIFI_PASSWORD";
```

5. Select the ESP32 board.
6. Select the correct COM port.
7. Upload the program.
8. Open Serial Monitor at **115200 baud**.
9. Copy the IP address displayed by the ESP32.
10. Open the IP address in a browser connected to the same Wi-Fi network.

## ⚠️ Notes

* DHT11 readings may return `NaN` if the sensor cannot communicate with the ESP32.
* Verify SDA/SCL connections for the BMP180/BMP280.
* The MQ sensor's raw ADC value is **not automatically an accurate AQI or PPM measurement**; calibration is required for quantitative gas/air-quality measurements.
* Keep the rain sensor electronics protected from direct water exposure.
* Ensure all sensors share a common ground with the ESP32.

## 🔮 Future Improvements

* 📱 Mobile-friendly dashboard
* ☁️ Cloud data storage
* 📊 Historical graphs
* 🚨 Weather alerts
* 📈 Real-time data visualization
* 🌍 Remote monitoring over the Internet
* 🔋 Solar/battery-powered operation
* 🤖 AI-based weather/environment prediction

## 👨‍💻 Project

**Project:** ESP32 Smart Weather Monitoring System
**Platform:** ESP32
**Programming:** Arduino C/C++
**Communication:** Wi-Fi
**Category:** IoT / Embedded Systems / Environmental Monitoring

## 📜 License

This project is intended for **educational and academic purposes**.
