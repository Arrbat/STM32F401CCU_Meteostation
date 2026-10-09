## Overview

Goal: To implement maintainable open-source Meteostation. 

Functionality includes:
- Pressure measurement
- Humidity measurement
- Temperature measurement
- Light detection
- Graphically presented values for display
- UART logging

Since project use MCU, interfaces, external devices, dealing with hardware and firmware, the expected user is likely experienced with embedded engineering 
so that is able to understand and (mainly) deploy the project for its own purposes (both learning or practical)

## Interfaces

User Interface supposes interaction between system and user, while device remains as black-box. User is needed to have interaction within the system, including:
- UART Logging of internal information and visible one (e.g. measurements extraction to external device)
- Turning the system ON/OFF

Software and Hardware interfaces are separated, meaning that every logic that somehow is dependent on hardware/platform/HAL is implemented independent of Software and API. 
Software is aimed to be portable (realistically possible to change and port), in other words application itself has business logic, API connects Software and Hardware, 
but both of them does not know about each other

## Quality Of Service 

Temperature: measurement between -20...+40°C ±0.5 °C. Verification is done by Reference Thermometer and comparison between project's one and reference.

Robustness: if station comes across the error, it should keep on working and report the issue through LED indicator.

Logging: is done just by wiring the pins and connecting interface to needed external device (like PC). Terminal is setup by user on its host.


## Design and Implementation 

Installation:
- Devices may be wired on breadboard
- Firmware must be loaded through ST-LINK
- Power must be delivered. Initially, 3.3V voltage source is required

Reusability:
- Drivers for peripherals are required to be portable
- License of project is MIT. Some parts of code may be distributed with other licenses, which will be noticed in License file

Hardware:
- STM32F401CCU6
- CH340C as UART-USB-C Converter (but any other with same pins may be used)
- Digital Light Sensor Module (NAMELESS, Characteristics:
` Photoresistor, LM393 comparator, output >15 mA, potentiometer threshold, 3.3–5 V, digital output (0/1), mounting hole, 3.2 × 1.4 cm. Pins: VCC (3.3–5 V), GND, DO (digital out).) `
- AHT10
- BMP280
- Display OLED (SSD1315) S0.96" I2C 128x64
- Red LEDs
