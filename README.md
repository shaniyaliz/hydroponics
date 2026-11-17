# Automated Hydroponics System

A custom ESP32-S3 board that monitors water quality and automatically doses nutrients, circulates water and runs grow lights, with remote monitoring over Wi-Fi.

Built for EECS 473 (Advanced Embedded Systems) at the University of Michigan.

**More details:** [shaniya.me/#eecs473](https://shaniya.me/#eecs473)

## Why

Hydroponic plants need water quality kept in a narrow range, which usually means checking and adjusting it by hand every day. This system monitors pH, nutrient levels, water temperature and water level on its own, corrects them automatically, and lets you check on the plants from anywhere.

## How it works

| Part | Details |
|---|---|
| Sensing | pH, TDS and water-temperature sensors read through an ADS1115 ADC and a DS18B20 probe, plus an ultrasonic water-level sensor and a flow sensor |
| Control | Closed-loop control drives the dosing pumps, water pump and mixer motor to keep nutrients and circulation in range |
| Lighting | The board switches the grow lights on and off |
| Connectivity | Wi-Fi set up over Bluetooth, with sensor data sent over MQTT (TLS) to a Node.js web dashboard |

**Hardware:** custom ESP32-S3 PCB (KiCad), pH and TDS sensors, DS18B20 temperature probe, ADS1115 ADC, ultrasonic water-level sensor, dosing pumps, water pump, mixer motor, grow lights

## Repository layout

| File | Purpose |
|---|---|
| `main/main.cpp` | Main loop: reads sensors, runs the control logic and sends data |
| `main/src/dosing_pump.cpp`, `water_pump.cpp`, `mixer_motor.cpp` | Pump and motor drivers |
| `main/src/pH_sensor.cpp`, `tds_sensor.cpp`, `water_temperature.cpp` | Water-quality sensor drivers |
| `main/src/water_level.cpp`, `water_flow.cpp` | Water-level and flow sensor drivers |
| `main/src/grow_light.cpp` | Grow-light control |
| `main/src/wifi.c`, `hydro_prov.c`, `hydro_mqtt.c` | Wi-Fi, Bluetooth provisioning and MQTT |
| `WebGUI/server.js`, `WebGUI/index.html` | Web dashboard |
| `PCB_V1.kicad_*` | Custom PCB schematic and layout |
