# 📡 Ultrasonic Radar Scanner (Arduino + Processing)

This project is a 180-degree ultrasonic **radar-style distance scanner** built using an Arduino-compatible microcontroller, an HC-SR04 ultrasonic sensor, and an SG90 servo motor. A Processing visualiser renders a real-time radar sweep, similar to a scanning SONAR or LiDAR system.

It demonstrates embedded systems fundamentals: **PWM, digital I/O, sensor integration, serial communication, and real-time data visualisation**.

---

## ✨ Features

- 🔄 **Servo-based scanning** from 0° → 180°
- 📏 **Distance measurement** using HC-SR04
- 🖥️ **OLED display output** (current angle + distance)
- 💻 **Processing visualiser** for classic radar sweep animation
- 🔌 Simple wiring, fully powered over USB
- 📡 Real-time serial communication between Arduino + PC

---

## 🧰 Hardware Used

- Arduino Uno–compatible CH340 board (ATmega328P)
- SG90 micro servo
- HC-SR04 ultrasonic distance sensor
- 0.96" I²C OLED (SSD1306) — optional
- Breadboard + jumper wires
- USB cable for power + data

---

## 🔌 Wiring Diagram

### **Ultrasonic Sensor (HC-SR04)**

| HC-SR04 Pin | Arduino Pin |
|-------------|-------------|
| VCC         | 5V |
| GND         | GND |
| TRIG        | D10 |
| ECHO        | D11 |

### **Servo (SG90)**

| Servo Wire           | Arduino Pin |
|----------------------|-------------|
| Brown/Black (GND)    | GND |
| Red (VCC)            | 5V |
| Orange/Yellow (PWM)  | D9 |

### **OLED Display (SSD1306, I²C)**

| OLED Pin | Arduino Pin |
|----------|-------------|
| VCC      | 5V |
| GND      | GND |
| SDA      | A4 |
| SCL      | A5 |

> All modules share the same **ground**.

---

## 📁 Project Structure

arduino-ultrasonic-radar/
│
├── src/
│ └── UltrasonicRadar/
│ └── UltrasonicRadar.ino
│
├── processing/
│ └── radar_visualizer/
│ └── radar_visualizer.pde
│
├── docs/
│ ├── radar-setup-photo.jpg
│ ├── radar-scan-screenshot.png
│ └── wiring-diagram.png
│
├── media/
│ └── radar-demo.mp4
│
├── LICENSE
└── README.md


---

## 🔧 Arduino Firmware

The Arduino firmware performs:

1. Servo sweep control (0° → 180°)
2. Ultrasonic distance measurement
3. Real-time display on OLED (optional)
4. Serial output to PC for visualisation

File:
src/UltrasonicRadar/UltrasonicRadar.ino


**Required Arduino Libraries**

- `Servo`
- `Adafruit GFX`
- `Adafruit SSD1306`

Install via **Sketch → Include Library → Manage Libraries**.

---

## 🖥 Processing Radar Visualiser

The Processing script renders a real-time radar UI and plots detected points based on serial data.

File:
processing/radar_visualizer/radar_visualizer.pde


### How to Run:

1. Upload Arduino sketch
2. Close Arduino Serial Monitor
3. Open Processing sketch
4. Adjust serial port index (`Serial.list()[x]`)
5. Click **Run**

---

## 🎥 Demo

media/radar-demo.mp4


Add screenshots in `docs/`.

---

## 🧠 How It Works (High-Level)

- The **servo** defines the scanning angle.
- The **ultrasonic sensor** measures distance using time-of-flight.
- Arduino prints data as:
angle,distance

- Processing converts polar → Cartesian coordinates.
- Points are plotted on a semi-circular radar graph.
- This mimics basic principles of radar and 2D LiDAR scanning.

---

## 🚀 Future Improvements

- Add LEDs or buzzer warnings for close objects
- Add SD card or CSV logging
- Replace Processing with Python visualiser
- Add Bluetooth (HC-05) to stream data to mobile
- Upgrade to ESP32 for WiFi dashboard
- Implement 360° scanning with continuous servo

---

## 📝 License

MIT License — free to use and modify.
