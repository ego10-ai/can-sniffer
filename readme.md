# CAN Adapter

![MCU](https://img.shields.io/badge/MCU-STM32G431-blue?style=flat-square)
![Hardware](https://img.shields.io/badge/Hardware-Open_Source-green?style=flat-square)
![Firmware](https://img.shields.io/badge/Firmware-candleLight_%7C_SLCAN-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)



This is a simple adapter board I designed to connect a computer to a CAN bus network using a USB-C cable. 

It is built using the STM32G431 microcontroller and the TJA1462 CAN transceiver. It supports both standard CAN and CAN FD.

## Features
* USB-C connection for power and data.
* Supports CAN FD (Flexible Data-rate).
* Switchable 120 ohm termination resistor.
* 4 LEDs to show status (Power, RX, TX, Error).

## The Hardware


The board uses these main parts:
* MCU: STM32G431CBU6
* Transceiver: TJA1462
* Power: 3.3V Regulator (AP7343)
* Termination: A 2-pin header with a jumper cap.

## Bill of Materials (BOM)
A complete BOM file (`BOM for can sniffer.xlsx`) is included in this repository. It lists all the exact part numbers, values, and packages you need to order or assemble this board.

## Wiring


Connect your wires to the header pins like this:
* CAN H: Connect to the High line.
* CAN L: Connect to the Low line.
* GND: Always connect the ground wire.

Warning: Do not connect 12V or vehicle battery power to this board. It gets all the power it needs from the USB port.

## How to use the Jumper
There is a 120 ohm resistor on the board to help the signal. You can turn it on or off using the 2-pin header.

* Jumper ON (Cap is on): The resistor is connected. Do this if the adapter is at the very end of the wire.
* Jumper OFF (Cap is off): The resistor is disconnected. Do this if the adapter is in the middle of the network.

## Firmware Options
You can flash different firmware depending on your needs:

1. candleLight: Makes the device show up as a native CAN interface. Good for Linux and modern Windows tools.
2. SLCAN: Makes the device show up as a Serial COM Port. Good for older software.
3. Custom: You can write your own C code using STM32CubeIDE to make the board do specific tasks automatically.

## License
This project is open-source and licensed under the MIT License.