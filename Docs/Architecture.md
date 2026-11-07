# Software Architecture

## Overview

The Smart Data Logger is designed with modular layers to isolate platform code from application logic.

## Main Layers

- **Hardware Abstraction Layer (HAL)**: STM32 HAL drivers manage low-level peripheral setup.
- **Drivers**: Sensor, display, storage, and communication drivers provide reusable APIs.
- **Application Layer**: Coordinates sensor reads, LCD updates, SD card logging, and UART telemetry.

## Data Flow

1. Sensor data is acquired from the BME280 over I2C.
2. The application formats measurements for the LCD and UART.
3. Log entries are written to the SD card through FATFS.
4. UART sends a status frame to the PC terminal.

## Error Handling

- Sensor read failures should report to UART and avoid corrupting logs.
- SD card mount failures should be retried with graceful fallback.
- UART transmit errors should be logged locally and retried if possible.
