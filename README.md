# IoT25-Hw07 -BLE-Based Distance Estimation System

🛠 Project Overview

This project implements a Bluetooth Low Energy (BLE)-based distance estimation system using two ESP32 boards. One board acts as a BLE advertiser (server), while the other works as a scanner (client) to estimate the distance between the two based on the RSSI (Received Signal Strength Indicator) value.

The estimated distance is displayed in real-time on the serial monitor and a LED is blinked when the devices are within 1 meter of each other.

🔧 System Configuration

1. ESP32 BLE Server (Advertiser)

Function: Advertises BLE signals with a fixed Tx Power

BLE Device Name: BLE_Server

TX Power: Set internally (assumed as -59 dBm)

Code Highlights:

BLEDevice::init("BLE_Server")

Starts advertising without a service or characteristic

2. ESP32 BLE Client (Scanner + Distance Estimator)

Function: Scans for BLE_Server, reads RSSI, and calculates distance

Distance Formula:

distance (m) = 10 ^ ((txPower - RSSI) / (10 * n))

txPower: -59 (estimated power at 1m)

n: 2.0 (environment factor for indoor)

LED Alert: LED on GPIO 26 blinks when distance <= 1.0m

Web Output: Displays distance info via simple web server (optional)

⚙ Required Libraries

BLEDevice.h

WiFi.h (for optional web server)

ESPAsyncWebServer (optional, if web-based display is implemented)



✅ Output Example

RSSI: -70 dBm → Estimated Distance: 1.58 m
RSSI: -64 dBm → Estimated Distance: 0.89 m ➜ LED Blinking

📸 Experiment Results

Distance tested at: 0.5m, 1m, 2m, 3m, 4m

Table comparing actual vs estimated distances

Bar graph showing error margins




