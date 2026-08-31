# STM32F103C8T6-CUSTOM-DEVBOARD
A custom development board based on the STM32F103C8T6 microcontroller. I designed the schematic and 2-layer PCB from scratch in EasyEDA, including the power supply, USB interface, programming/debugging interface and commonly used communication peripherals.

## Schematic

## Schematic

[View Schematic](Schematic_MCU-devboard2_2026-08-31.png)
## PCB Layout

[View PCB Layout](PCB_PCB_MCU-devboard2_2_2026-08-31 (1).png)

## Features

- STM32F103C8T6 microcontroller
- USB-C power and USB communication
- USB ESD protection using USBLC6-2SC6
- 22Ω series resistors on USB D+ and D- lines
- AMS1117-3.3V regulator for 5V to 3.3V conversion
- 8 MHz external crystal with load capacitors
- Reset and BOOT0 circuitry
- User LED and power LED
- SWD programming and debugging interface
- UART1 interface
- I2C1 interface with 4.7kΩ pull-up resistors
- SPI1 interface
- Compact 2-layer PCB

## Interfaces

| Interface | STM32 Pins | Purpose |
|---|---|---|
| USB | PA11 / PA12 | USB communication |
| UART1 | PA9 / PA10 | Serial communication |
| I2C1 | PB6 / PB7 | Sensors, displays and other I2C devices |
| SPI1 | PA5 / PA6 / PA7 | High-speed peripheral communication |
| SWD | PA13 / PA14 | Programming and debugging |

## Power

The board is powered through USB-C.

**USB 5V → AMS1117-3.3V → 3.3V rail**

The 3.3V rail supplies the STM32 and other 3.3V circuitry. Decoupling capacitors are used around the MCU and regulator to help reduce supply noise and improve power stability.

## USB Protection

The USB data lines are protected using the USBLC6-2SC6 ESD protection device.

The USB data path is:

**USB D+ → ESD protection → 22Ω → PA12**

**USB D- → ESD protection → 22Ω → PA11**

Two 5.1kΩ pull-down resistors are connected to USB-C CC1 and CC2 for USB-C device/sink detection.

## Clock and Reset

An external 8 MHz crystal is connected to the STM32 oscillator pins with two 20pF load capacitors.

The board also includes a manual reset button connected to NRST and a pull-down resistor on BOOT0 so the MCU has a defined default boot state.

## Programming and Debugging

A 5-pin SWD header is provided for programming and debugging the STM32 using an ST-Link.

The header provides:

- SWDIO
- SWCLK
- 3.3V
- GND
- NRST

## Communication Interfaces

The board exposes several STM32 peripherals through headers:

- UART1 for serial communication
- I2C1 for sensors, displays and other I2C devices
- SPI1 for high-speed peripherals

## PCB

The PCB was designed as a compact 2-layer board in EasyEDA. Component placement and routing were carried out with attention to the USB section, oscillator, power supply and MCU connections.

## Bill of Materials

The complete Bill of Materials is available here:

**[BOM.xlsx](BOM/BOM.xlsx)**

## Tools Used

- EasyEDA
- STM32F103C8T6
- 2-layer PCB design

## What I Learned

This project helped me understand the complete process of designing a custom microcontroller board, from component selection and schematic design to PCB placement and routing.

It also gave me practical experience with USB, power regulation, decoupling, SWD, UART, I2C, SPI and basic PCB design.

## Future Improvements

- Add a CAN interface using an external CAN transceiver
- Fabricate and assemble the board
- Test the board hardware and interfaces
- Improve the PCB layout based on testing
