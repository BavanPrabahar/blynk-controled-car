# Blynk-Controlled Car (Arduino)

This repository contains an Arduino sketch for a motorized car with obstacle detection. Although the repository name suggests it's controlled via [Blynk](https://blynk.io/), the current codebase implements an autonomous obstacle-avoiding routine using an ultrasonic sensor.

## Hardware Components

* **Arduino Board** (e.g., Arduino Uno)
* **Motor Driver** (e.g., L298N or similar) connected to two DC motors
* **Ultrasonic Sensor** (HC-SR04) for obstacle detection
* *(Optional)* IR Sensors (Defined in code but currently unused in the main loop)

## Pin Configuration

| Component | Pin Function | Arduino Pin |
| :--- | :--- | :--- |
| **Motor 1** | IN1 | 2 |
| | IN2 | 4 |
| **Motor 2** | IN1 | 6 |
| | IN2 | 8 |
| **Ultrasonic Sensor** | TRIG | 12 |
| | ECHO | 11 |
| **IR Sensors** | IR1 | 8 (Note: pin conflict with Motor 2 IN2) |
| | IR2 | 9 |

## How It Works

The car continuously checks the distance of objects in front of it using the ultrasonic sensor.
1. **Obstacle Detected (< 50 cm):** If an object is closer than 50 cm, the motors stop and the car halts.
2. **Clear Path (>= 50 cm):** The car moves forward for 1 second, then backward for 1 second. (This behavior can be modified in the `loop()` function to suit your needs).

## Getting Started

1. Clone this repository: `git clone https://github.com/BavanPrabahar/blynk-controled-car.git`
2. Open the `blynk-controled-car.ino` file in the [Arduino IDE](https://www.arduino.cc/en/software).
3. Connect your Arduino board and configure the correct board and port under the **Tools** menu.
4. Verify and upload the code to your Arduino.
5. Open the Serial Monitor at 9600 baud to see obstacle detection logs.

## Future Improvements

* Integrate the **Blynk IoT platform** to enable remote control via Wi-Fi/Bluetooth.
* Implement steering or turning logic when an obstacle is detected.
* Resolve the pin conflict between IR1 and Motor 2.
