# mini-ev-design
Custom PCB design for a mini, remote-control electric car

Overview

The Mini Electric Vehicle (EV) Platform is a compact, battery-powered robotics platform designed to demonstrate embedded systems, motor control, and PCB design concepts. The project uses an ESP32 microcontroller and a DRV8833 dual H-bridge motor driver to control a brushed DC motor from a rechargeable LiPo battery.

This project was designed in KiCad as a custom PCB and serves as a learning platform for:

DC motor control using PWM
H-bridge motor drivers
Battery-powered embedded systems
Power distribution and decoupling
Wireless control using ESP32 Wi-Fi or Bluetooth
PCB schematiclayout

Features
ESP32-based control system
DRV8833 motor driver
Single brushed DC motor support
3.7V LiPo battery operation
On-board power regulation
Reverse polarity protection
Fuse protection
Decoupling and bulk capacitance for power stability
Expandable for sensors and remote-control functionality

System Architecture
Power System
The vehicle is powered by a 3.7V LiPo battery with integrated protection circuitry.

Power path:
Battery → Power Switch → Fuse → Buck Converter → 5V Rail

The 5V rail powers:
ESP32 Development Module
DRV8833 VM supply

All devices share a common ground.

Motor Control
The ESP32 generates PWM and direction signals that are connected to the DRV8833.

Control signals:
AIN1
AIN2
nSLEEP

Motor outputs:
AOUT1
AOUT2

The motor connects directly between AOUT1 and AOUT2.

No external flyback diode is required because the DRV8833 includes internal MOSFET body diode protection and current recirculation paths.

Power Integrity
DRV8833

Required capacitors:

100 µF bulk capacitor between VM and GND
0.1 µF ceramic capacitor between VM and GND
2.2 µF capacitor between VINT and GND
VCP capacitor according to datasheet recommendations
ESP32

10–47 µF bulk capacitor between 5V and GND
0.1 µF ceramic capacitor between 5V and GND
Battery Protection

Protection mechanisms include:

LiPo battery protection circuit (PCM)
PCB fuse protection
Optional ideal-diode MOSFET reverse polarity protection

Bill of Materials
ESP32 DevKitM-1 C3	Main microcontroller
DRV8833	Dual H-bridge motor driver
3V Brushed DC Motor	Vehicle propulsion
3.7V LiPo Battery	Main power source
Buck Converter	Generates regulated 5V rail
Fuse (3A)	Overcurrent protection
Capacitors	Decoupling and bulk filtering
Power Switch	System on/off control
JST Battery Connector	Battery connection
