# ESP32 Heater Control System

An ESP32-based smart heater controller using FreeRTOS and a DHT22 sensor. This project reads temperature in real-time, 
controls a heater(LED Bar-Graph imitating heater) via relay, and displays system status through an LCD, LEDs, buzzer, and a 10-segment LED bar graph.

---

## Getting Started

### 1. Clone the repository
### 2. Configure Wokwi Simulator
### 3. Use the Heater_Control_System.cpp Code file in simulator
### 4. Compile and Start the simulator
### 5. Click on the DHT22 temperature sensor to control the Ambient Temperature 
### 6. Verify the different Temperature states 

---

## Overview

This system manages a heater automatically based on predefined temperature thresholds:

- Controls heater through relay
- Displays current temperature and system state on LCD
- Uses LEDs and buzzer for visual/audible feedback
- Simulates heater levels using a 10-segment LED bar
- Implements FreeRTOS tasks for concurrency
- Simulates MOCK BLE advertising via Serial monitor (It's Mock since WOKWI does not support real time BLE)

---

## Features

- Real-time temperature monitoring with DHT22
- Task-based architecture using FreeRTOS
- Overheat alert with buzzer
- LED & LCD indicators for system states
- Simulated BLE advertising over Serial

---

## Hardware Required

- ESP32 DevkitC-V4 Development Board
- DHT22 Temperature Sensor
- 16x2 I2C LCD Display
- Relay Module
- 2x LEDs (Heating and Idle indicators)
- Buzzer
- 10-segment LED bar imitating Real Heater
- Resistors, Breadboard, and Jumper Wires

---

## Pin Configuration

| Component      | GPIO Pin |
|----------------|----------|
| DHT22 (Data)   | 18       |
| LCD (SDA/SCL)  | 21 / 22  |
| Relay Control  | 26       |
| Heat LED       | 13       |
| Idle LED       | 25       |
| Buzzer         | 27       |
| Bar Graph LEDs | 23, 19, 17, 16, 15, 14, 12, 5, 4, 2 |

---

## FreeRTOS Tasks

| Task        | Interval | Function                         |
|-------------|----------|----------------------------------|
| tempTask    | 1s       | Reads temperature from DHT22     |
| controlTask | 200ms    | Controls heater, LEDs, LCD, buzzer |
| bleTask     | 1s       | Logs temperature over Serial (mock BLE) |

---

## System States

| State         | Description                        |
|---------------|------------------------------------|
| HEATING       | Temp < 28°C                        |
| STABILIZING   | 20°C ≤ Temp < 28°C                 |
| TARGET_OK     | Temp == 28°C                       |
| OVERHEAT      | Temp ≥ 45°C                        |
| IDLE          | Temp > 28°C and < 45°C             |

---


