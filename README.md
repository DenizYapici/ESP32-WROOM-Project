# ESP32-WROOM Low-Power PCB Design

This repository contains the PCB design and schematics for a low-power ESP32-WROOM based board. The purpose of this board is to reduce the current consumption of the ESP32 for battery-powered applications.

## Features

- **Power Management**
  - Board powered by USB or 4.2V battery.
  - P-MOSFET used to switch between USB and battery (battery powers by default; USB takes over if both are present).
  - RT9080 linear voltage regulator used (switching regulator can be used in future for higher efficiency).

- **Sensors**
  - **DS18B20** temperature sensor.
  - **ADXL345** accelerometer sensor.

- **Communication**
  - **CP2102 USB to UART bridge** for serial communication.

- **PCB Design**
  - Designed with **Altium Designer**.
  - **2-layer PCB**: Top layer for routing, both layers used for GND.
  - USB D+/D- routed (note: for high-speed USB, differential impedance ~90Ω recommended).
  - ESP32 antenna keep-out zone: recommended at least 15mm from copper for proper RF performance.
  - DS18B20 placement consideration: keep away from ESP32 to avoid heat interference.

## Contents

- `schematics/` : Circuit diagrams (.SchDoc, PDF)  
- `pcb/` : PCB layout and Gerber files (.PcbDoc, Gerber)  
- `datasheets/` : ESP32-WROOM and component datasheets  
- `README.md` : Project description

## Notes / Design Considerations

- USB shield is typically grounded on the host side; it should not be connected directly to the ESP32 board GND.  
- Board is optimized for low power but linear regulator may reduce battery life; consider switching regulator in future versions.  
- PCB routing and layer usage: mostly top layer routing with ground planes on both layers.

## License

[MIT License](LICENSE)
