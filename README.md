
<p align="center">
  <img src="https://github.com/user-attachments/assets/09ff27da-2a33-4134-b87a-0563f750b113" width="400">
</p>


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

<img src="https://github.com/user-attachments/assets/7f654464-1c34-4b22-81dc-f2182843401a" width="350">


#### Green LED
- Long leg (anode) → D4 through 220Ω resistor
- Short leg (cathode) → GND

<img src="https://github.com/user-attachments/assets/b5494ebf-328c-431f-95a4-0953ed8fa815" width="350">


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

<p float="left">
  <img src="https://github.com/user-attachments/assets/1340137a-392e-4a1f-bfb9-273943df011f" width="350" />
  <img src="https://github.com/user-attachments/assets/13f9b2de-3f8c-4b0d-9733-fe8667f9846d" width="350" />
</p>

---

## 🖥️ Serial Plotter

Open:

Tools → Serial Plotter

You will see:
- Blue line: measured distance
- Red line: 15 cm threshold

---

📘 What I Learned

This project strengthened my understanding of embedded systems, electronics, and sensor integration. Throughout the build process, I worked with multiple hardware and software components and improved my ability to design reliable, real-world systems.

Key learning outcomes:

🔹 Embedded Programming (Arduino C/C++)

Writing clean, structured embedded code

Working with timing-based functions (pulseIn, microsecond calculations)

Handling conditional logic for sensors & indicators

Displaying real-time dynamic data on an LCD

🔹 Electronics & Circuit Design

Understanding digital I/O behaviour

Correctly wiring LEDs with resistors

Using ultrasonic sensors (HC-SR04) with trigger/echo timing

Debugging incorrect wiring and interpreting unstable sensor readings

Power management and grounding for stable sensor operation

🔹 System Integration

Coordinating multiple subsystems:
✅ Ultrasonic sensor
✅ LCD display
✅ Red/green LEDs

Ensuring stable operation when multiple components share power

Planning component layout on a breadboard for clean cable management

🧠 Engineering Skills Demonstrated

This project shows practical skills that are directly relevant to Electrical Engineering, Mechatronics, and Computer Systems Engineering.

✔️ Hardware/Software Integration

Demonstrates ability to connect physical electronics to digital logic through reliable firmware.

✔️ Real-Time Systems

Distance is measured continuously, processed instantly, and displayed without delays — showing understanding of simple real-time loops.

✔️ Sensor Interfacing

The ultrasonic module requires understanding of:

microsecond timing

signal reflection

threshold detection

noise handling

✔️ Problem Solving & Debugging

During development I troubleshooted:

floating sensor values

incorrect LED polarity

LCD I2C addressing and pin mapping

breadboard short circuits

This shows initiative, independence, and hands-on troubleshooting skills — all valuable to employers hiring interns.

🚀 Why This Project Matters

Although simple, this system represents a real engineering workflow:

Define the requirement (detect nearby objects <15 cm)

Select appropriate sensors

Integrate electronics safely

Write embedded software to process signals

Display feedback and provide warnings

Test, debug, and refine

This is the exact process used in:

robotics obstacle detection

parking sensors

automation systems

mechatronics safety systems

embedded product development

Recruiters look for projects that prove you can take something from idea → working prototype, and this project does exactly that.

🛠️ Potential Improvements (Future Work)

These optional upgrades show initiative and forward-thinking engineering ability:

Add a servo motor to create rotating radar scanning

Send distance data to a PC via serial plotting

Log readings for analysis (CSV output)

Integrate with an ESP32 for wireless IoT monitoring

Replace LEDs with a buzzer for audible warnings

Create a full graphical radar interface using Processing

Including a list like this shows that you think like an engineer — always improving.

🏁 Summary

This project demonstrates my ability to:

✔️ design circuits
✔️ write embedded code
✔️ integrate sensors
✔️ debug hardware
✔️ document engineering work clearly

It represents a strong foundation in electrical and computer systems engineering principles and is a valuable step toward more advanced embedded and robotics projects.

📝 License

MIT License
