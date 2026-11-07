# Build Instructions

## Required Tools

- STM32CubeIDE or STM32CubeMX + arm-none-eabi toolchain
- STM32 HAL drivers
- FATFS middleware for SD card support
- USB-to-UART terminal application (e.g. PuTTY, Tera Term, minicom)

## Recommended Workflow

1. Open STM32CubeIDE and create or import the target board project.
2. Configure the MCU clock, I2C, SPI, and UART peripherals.
3. Add the HAL driver files and middleware for FATFS.
4. Place the BME280 sensor driver and LCD driver sources under the project folder.
5. Build the project using the STM32CubeIDE build action.
6. Connect the board and flash the firmware.
7. Open the UART console at the configured baud rate to observe serial telemetry.

## Notes

- Ensure the SD card module uses the correct chip select and SPI pin mapping.
- Verify the BME280 I2C address matches the hardware wiring.
- Use a proper `sdcard.log` or `DATA_LOG.CSV` file naming convention for the application.
