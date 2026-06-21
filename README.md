# ESP32 Servo Control Using Potentiometer

YouTube Demo: https://youtu.be/XlzOV5RobT8?si=4y_LoXy1C-mLtoDv

This project controls the position of a servo motor using a potentiometer and an ESP32. The ESP32 reads the analog voltage from the potentiometer, converts it into a digital value using its ADC, maps that value to an angle between 0° and 180°, and rotates the servo accordingly.

---

## Features

* Real-time servo control using a potentiometer
* Smooth ADC readings by averaging multiple samples
* Serial monitor output for ADC values and servo angle
* PWM-based servo control using the ESP32Servo library

---

## Components Used

| Component                | Quantity    |
| ------------------------ | ----------- |
| ESP32 Development Board  | 1           |
| Servo Motor (SG90/MG90S) | 1           |
| Potentiometer (10kΩ)     | 1           |
| Jumper Wires             | As required |
| Breadboard               | 1           |

---

## Circuit Connections

### Potentiometer

| Potentiometer Pin  | ESP32 Pin |
| ------------------ | --------- |
| Left Pin           | 3.3V      |
| Middle Pin (Wiper) | GPIO 34   |
| Right Pin          | GND       |

### Servo Motor

| Servo Wire | ESP32 Connection                 |
| ---------- | -------------------------------- |
| Signal     | GPIO 18                          |
| VCC        | 5V (External supply recommended) |
| GND        | GND                              |

Note: If you power the servo using an external 5V supply, connect the grounds of the ESP32 and the external supply together.

---

## How It Works

1. The potentiometer produces a voltage between 0 V and 3.3 V.
2. The ESP32 ADC converts this voltage into a value between 0 and 4095.
3. The ADC value is mapped to an angle between 0° and 180°.
4. The servo rotates to the corresponding angle.
5. Multiple ADC readings are averaged to reduce noise and make the movement smoother.

---

## Mapping

ADC Range:

0 → 4095

Servo Angle Range:

0° → 180°

```cpp
angle = map(val, 0, 4095, 0, 180);
```

---

## Serial Monitor Output

Example:

```text
ADC = 2048  Angle = 90
ADC = 3072  Angle = 135
ADC = 4095  Angle = 180
```

---

## Project Structure

```text
ESP32-Servo-Control/
│
├── servo_control.ino
├── README.md
└── images/
    └── circuit_diagram.png
```

---

## Possible Improvements

* Display the angle and ADC value on an OLED screen
* Control the servo wirelessly using Wi-Fi
* Save preset servo positions in EEPROM
* Control multiple servos
* Implement additional filtering techniques such as an Exponential Moving Average (EMA)

---

## Library Used

```cpp
#include <ESP32Servo.h>
```

Install it from the Arduino Library Manager:

Tools → Manage Libraries → Search for "ESP32Servo" → Install

---

## Concepts Used

* Analog-to-Digital Conversion (ADC)
* PWM-based servo control
* Signal averaging and noise reduction
* Mapping sensor values to actuator output
* Basic embedded programming with ESP32

---

## Author

Nilkanta

B.Tech, Computer Science and Engineering (IoT and Cybersecurity)

Interested in Embedded Systems, Robotics and IoT.
