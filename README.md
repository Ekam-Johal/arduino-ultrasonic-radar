
![D9AEA2CF-7216-4B0C-94AC-D37052E8E851](https://github.com/user-attachments/assets/09ff27da-2a33-4134-b87a-0563f750b113)
![DEA39E66-49D9-4CD9-9026-E84804AA4C3F](https://github.com/user-attachments/assets/082e9747-e021-47e7-a0dc-72960607a310)
![03A4F70F-9705-4460-ACAD-28B3027B7960](https://github.com/user-attachments/assets/fa910105-7357-4ea3-b5c5-67c0341173d7)

# Ultrasonic Object Detection System (Arduino Project)

This project uses an HC-SR04 ultrasonic sensor to measure distance and display results on a 16×2 I2C LCD screen.
Two indicator LEDs provide visual warnings:

- Red LED → Object detected closer than 15 cm
- Green LED → Area clear

This is a simple and effective proximity alert system for Arduino beginners.

---

## 🚀 Features

- Real-time distance measurement
- LCD distance display (in cm)
- Red LED warning when object < 15 cm
- Green LED when area is clear
- Live data plotting using Arduino Serial Plotter
- Works on Arduino Uno and clones

---

## 🔧 Components Used

| Component | Quantity |
|----------|----------|
| Arduino Uno / clone | 1 |
| HC-SR04 Ultrasonic Sensor | 1 |
| 16×2 I2C LCD Display | 1 |
| Red LED | 1 |
| Green LED | 1 |
| 220Ω resistors | 2 |
| Jumper wires + breadboard | - |

---

## 🛠️ Wiring Guide

### Ultrasonic Sensor (HC-SR04)

| HC-SR04 Pin | Arduino Pin |
|-------------|-------------|
| VCC | 5V |
| GND | GND |
| TRIG | D10 |
| ECHO | D11 |

---

### LCD (16×2 I2C)

| LCD Pin | Arduino Pin |
|---------|-------------|
| SDA | A4 |
| SCL | A5 |
| VCC | 5V |
| GND | GND |

---

### LED Indicators

#### Red LED
- Long leg (anode) → D3 through 220Ω resistor
- Short leg (cathode) → GND

#### Green LED
- Long leg (anode) → D4 through 220Ω resistor
- Short leg (cathode) → GND

---

## 🧠 How It Works

1. The HC-SR04 sends out an ultrasonic pulse.
2. The pulse bounces off an object and returns to the sensor.
3. The Arduino calculates the distance.
4. Distance is shown on the LCD.
5. If distance < 15 cm:
   - Red LED turns on
   - LCD shows "OBJECT NEAR!"
6. If distance ≥ 15 cm:
   - Green LED turns on
   - LCD shows "CLEAR"
7. Distance data is plotted in Arduino Serial Plotter.

---

## 🖥️ Serial Plotter

Open:

Tools → Serial Plotter

You will see:
- Blue line: measured distance
- Red line: 15 cm threshold

---

📦 Future Improvements

Add buzzer alarm

Add servo rotation for radar scanning

Add OLED graphical display

Wireless alert using Bluetooth

📝 License

MIT License

## 📜 Code

```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// Ultrasonic pins
const int trigPin = 10;
const int echoPin = 11;

// LED pins
const int redLED = 3;
const int greenLED = 4;

const int threshold = 15; // cm

void setup() {
  lcd.init();
  lcd.backlight();

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);

  Serial.begin(9600);

  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Ultrasonic Ready");
  delay(1500);
  lcd.clear();
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  long distance = duration * 0.034 / 2;

  lcd.setCursor(0,0);
  lcd.print("Dist: ");
  lcd.print(distance);
  lcd.print(" cm   ");

  lcd.setCursor(0,1);

  if (distance > 0 && distance < threshold) {
    lcd.print("OBJECT NEAR!  ");
    digitalWrite(redLED, HIGH);
    digitalWrite(greenLED, LOW);
  } 
  else {
    lcd.print("CLEAR         ");
    digitalWrite(redLED, LOW);
    digitalWrite(greenLED, HIGH);
  }

  Serial.print(distance);
  Serial.print(",");
  Serial.println(threshold);

  delay(150);
}
