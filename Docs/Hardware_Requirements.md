# Hardware Requirements

## Recommended Components

- STM32 development board (F1/F4/H7 series)
- Bosch BME280 environmental sensor module
- 16x2 character LCD module with I2C or GPIO interface
- SPI SD card module with full-size or microSD adapter
- USB-to-UART adapter for serial output
- Breadboard, jumper wires, and power supply

## Notes

- Use level shifting when connecting 3.3V devices with a 5V board.
- Confirm the I2C address of the BME280 before firmware initialization.
