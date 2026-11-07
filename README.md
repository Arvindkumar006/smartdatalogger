# Smart Data Logger

**ARM-based IoT Data Logger using STM32**  
Modern, portfolio-ready embedded system documentation for a sensor-driven data logger built around STM32 HAL.

---

## Project Overview

This project demonstrates a production-quality STM32 data logger with the following capabilities:

- Read environmental data from the **BME280** sensor over **I2C**
- Display live measurements on a **16x2 LCD** module
- Log timestamped records to an **SD card** using **SPI + FATFS**
- Stream sensor data to a **PC terminal** over **UART**
- Support modular firmware design with reusable driver abstractions

---

## Key Features

- Real-time BME280 temperature, humidity, and pressure acquisition
- LCD status and live data presentation
- Persistent SD card logging for offline review and analytics
- UART telemetry for debugging, monitoring, and PC integration
- Clean software architecture targeting embedded IoT use cases

---

## Hardware Requirements

- STM32 development board (F1/F4/H7-compatible HAL)
- BME280 I2C environmental sensor
- 16x2 character LCD with I2C or GPIO interface
- SD card module connected over SPI
- USB-to-UART serial adapter for PC communication
- Power supply compatible with the target STM32 board

---

## Software Architecture

The documentation and supporting layout are modeled on a modular embedded project structure with clean separation:

- `Core/` – application entry and platform initialization
- `Drivers/` – sensor, display, storage, and communication driver modules
- `Docs/` – architecture, build instructions, and roadmap documentation
- `Images/` – diagrams and visual references

The firmware is designed for future enhancements such as DMA-based transfers, interrupt-driven UART, RTC timestamping, and bootloader updates.

---

## Communication Protocols Used

- **I2C** for BME280 sensor interaction
- **SPI** for SD card access with FATFS
- **UART** for serial telemetry and command interface
- **FATFS** for file system logging on removable storage

---

## Repository Structure

```
smart-data-logger/
├── Core/
├── Drivers/
│   ├── BME280/
│   ├── LCD/
│   ├── SD_Card/
│   ├── UART/
│   └── I2C_SPI/
├── Docs/
├── Images/
├── README.md
└── LICENSE
```

> Existing example code for the BME280 and LCD modules remains available in the original `BME280/I2C` and `LCD1602_I2C_NOHAL` folders.

---

## System Architecture Diagram

```text
[ BME280 ] --I2C--> [ STM32 MCU ] --SPI--> [ SD Card ]
                            |\
                            | \-- UART --> PC Terminal
                            \------ LCD Display
```

> Add a visual architecture diagram in `Images/` for portfolio presentation.

---

## Project Workflow

1. Initialize STM32 HAL and onboard peripherals
2. Configure I2C for the BME280 sensor
3. Read environmental data at regular intervals
4. Render current values on the 16x2 LCD
5. Save structured log entries to the SD card via FATFS
6. Send serialized output to PC via UART

---

## Sample UART Output

```text
[SmartDataLogger] 2026-06-25 12:08:42
Temp: 24.8 C  Humidity: 49.2 %  Pressure: 1013.7 hPa
SD Log: OK  | UART: OK  | LCD: Updated
```

---

## Sample SD Card Log

```csv
timestamp,temperature_c,humidity_pct,pressure_hpa
2026-06-25 12:08:42,24.8,49.2,1013.7
2026-06-25 12:09:42,24.9,49.3,1013.6
2026-06-25 12:10:42,25.0,49.1,1013.5
```

---

## Interview Questions and Answers

**Q1: What makes this project a strong embedded portfolio piece?**

- It combines sensor acquisition, display output, persistent storage, and serial communication in a single STM32 system.

**Q2: What protocols are used and why?**

- I2C for sensor access, SPI for SD card performance, UART for PC telemetry, and FATFS for filesystem compatibility.

**Q3: How would you extend this project?**

- Add DMA support, use interrupt-driven UART, incorporate RTC timestamps, implement a UART command interface, and enable a bootloader-based firmware update path.

**Q4: Why is modular driver organization important?**

- It improves maintainability, accelerates debugging, and makes it easier to reuse components across future STM32 projects.

---

## Resume Description

Embedded IoT Data Logger built on STM32 HAL with BME280 environmental sensing, 16x2 LCD display, SD card FATFS logging, and UART telemetry. Delivered a modular firmware layout optimized for production-style embedded software and interview-ready documentation.

---

## Build Instructions

1. Open the STM32CubeIDE workspace for the target board.
2. Configure the `I2C`, `SPI`, and `USART` peripherals in CubeMX.
3. Import the project and add the HAL driver source files.
4. Build with the STM32CubeIDE toolchain.
5. Flash the binary to the STM32 board.

> Detailed build steps and environment setup are available in `Docs/Build_Instructions.md`.

---

## Roadmap

- DMA support for I2C/SPI peripherals
- Interrupt-based UART telemetry and command handling
- RTC timestamp generation for log entries
- UART command interface for configuration and status
- Firmware update via bootloader and secure transfer

---

## License

This repository includes example content and documentation for educational and portfolio use. See `LICENSE` for terms.
