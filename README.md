# IOT_MULTIMETER
IoT-enabled current &amp; voltage monitoring on any screen.

# IoT Energy Meter with Blynk and INA219

This project implements an IoT-enabled energy meter using an ESP32 (NodeMCU), an INA219 current/voltage sensor, and a Blynk app for remote monitoring and display.  It also includes a local display on an OLED screen.

## Overview

The system measures voltage, current, power, energy consumption, and energy cost of a connected load.  The data is displayed both on a local OLED screen and sent to a Blynk app for remote monitoring and visualization.

## Hardware Requirements

* ESP32 (NodeMCU)
* INA219 Current/Voltage Sensor
* SSD1306 OLED Display (128x64)
* Jumper wires

## Software Requirements

* Arduino IDE
* Blynk Library
* Adafruit INA219 Library
* Adafruit SSD1306 Library
* Adafruit GFX Library

## Installation

1. **Arduino IDE Setup:** Install the Arduino IDE and configure it for your ESP32 board.  Install the necessary libraries (Blynk, Adafruit INA219, Adafruit SSD1306, and Adafruit GFX) through the Arduino Library Manager.

2. **Hardware Connection:** Connect the hardware components as follows:

   * **INA219:**
     * VIN+ to the positive side of your load.
     * VIN- to the negative side of your load.
     * VCC to ESP32 3.3V.
     * GND to ESP32 GND.
     * SDA to ESP32 SDA (GPIO 21).
     * SCL to ESP32 SCL (GPIO 22).

   * **OLED Display:**
     * VCC to ESP32 3.3V.
     * GND to ESP32 GND.
     * SDA to ESP32 SDA (GPIO 21).
     * SCL to ESP32 SCL (GPIO 22).

3. **Blynk Setup:**
   * Create a Blynk account and a new project.
   * Add the necessary widgets to your Blynk app (e.g., Value Display for Voltage, Current, Power, Energy, Cost).  Note the virtual pins assigned to each widget (V0, V1, V2, V3, V4, V5, V6, V7 in the code).
   * Copy the Template ID and Template Name from your Blynk project and paste them into the code where indicated.

4. **Code Upload:** Upload the Arduino code to your ESP8266 board.

## Usage

Once the code is uploaded and the hardware is connected, the system will start measuring and displaying the electrical parameters.  The OLED display will show the voltage, current, power, energy, capacity, and energy cost locally.  The same data will be sent to the Blynk app, where you can monitor it remotely.

## Code Explanation

* **INA219:** The code uses the Adafruit INA219 library to read voltage and current from the sensor.  The `ina219values()` function reads the raw values, calculates power and energy, and sends the data to Blynk.
* **OLED Display:** The Adafruit SSD1306 and GFX libraries are used to control the OLED display. The `displaydata()` function formats the data and displays it on the screen.
* **Blynk:** The Blynk library handles the communication between the ESP32 and the Blynk app. The `Blynk.virtualWrite()` function sends the measured values to the corresponding virtual pins in the Blynk app.
* **Energy Calculation:** The code calculates energy consumption by integrating power over time.  It also calculates the energy cost based on a user-defined price per unit.

## Troubleshooting

* **Serial Monitor:** Use the Serial Monitor to debug any issues with the hardware or software.
* **Blynk App:** Check the Blynk app for any connection issues or incorrect widget configurations.
* **Hardware Connections:** Double-check all hardware connections to ensure they are secure and correct.


