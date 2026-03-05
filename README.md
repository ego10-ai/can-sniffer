# CAN sniffer
![MCU](https://img.shields.io/badge/MCU-STM32G431-blue?style=flat-square)
![Hardware](https://img.shields.io/badge/Hardware-Open_Source-green?style=flat-square)
![Firmware](https://img.shields.io/badge/Firmware-candleLight_%7C_SLCAN-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)



This is a simple adapter board I designed to connect a computer to a CAN bus network using a USB-C cable. 

It is built using the STM32G431 microcontroller and the TJA1462 CAN transceiver. It supports both standard CAN and CAN FD.

## Features
* Direct plug-in to vehicle OBD2 ports.
* Safe car power circuit (handles 12V from the vehicle battery).
* USB-C connection for computer data and USB power.
* 3-pin power selector jumper to protect your computer.
* Switchable 120 ohm termination resistor.
* 4 LEDs to show status (Power, RX, TX, Error).

## The Hardware


The board uses these main parts:
* MCU: STM32G431CBU6
* Transceiver: TJA1462
* USB Power: 3.3V Regulator (AP7343)
* Car Power: XL1509-3.3 Buck Converter (steps 12V down to safe 3.3V)
* Protection: SS14 diodes to stop backward power flow.
* Connections: USB-C port, OBD2 16-pin male plug, and a standard CAN pin header.

## Bill of Materials (BOM)
A complete BOM file (`BOM for can sniffer.xlsx`) is included in this repository. It lists all the exact part numbers, values, and packages you need to order or assemble this board.

## How to use the Power Jumper (Very Important)


Because this board can plug into a car and a computer at the same time, you must select where the power comes from using the 3-pin header.

* Cap on Pins 1 and 2: The board runs on USB power. Use this when sitting at your desk.
* Cap on Pins 2 and 3: The board runs on Car power. Use this when plugged into the car's OBD2 port.

## How to use the Termination Jumper
There is a 120 ohm resistor on the board to help the CAN signal. You can turn it on or off using the 2-pin header.

* Jumper ON (Cap is on): The resistor is connected. Do this if the adapter is at the very end of the wire.
* Jumper OFF (Cap is off): The resistor is disconnected. Do this if the adapter is in the middle of a network that already has resistors.

## Wiring for Custom Cables


If you use the pin header instead of the OBD2 plug, connect your wires like this:
* CAN H: Connect to the High line.
* CAN L: Connect to the Low line.
* GND: Always connect the ground wire.

## Firmware Options
You can flash different firmware depending on your needs:

1. candleLight: Makes the device show up as a native CAN interface. Good for Linux and modern Windows tools.
2. SLCAN: Makes the device show up as a Serial COM Port. Good for older software.
3. Custom: i will write soon but You can also write your own C code using STM32CubeIDE to make the board do specific tasks automatically.

## License
This project is open-source and licensed under the MIT License.
