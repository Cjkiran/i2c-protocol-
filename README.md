# i2c-protocol
RTL to GDS2 @2025-06

I2C stands for Inter-Integrated Circuit. It's a serial communication protocol used for short-distance communication between integrated circuits. This protocol facilitates data exchange between a master device and multiple slave devices over a shared bus, often utilizing two lines: Serial Clock (SCL) and Serial Data (SDA). 

<img width="613" alt="image" src="https://github.com/user-attachments/assets/963ec0a5-1f00-4cbf-88d9-a44f8d607005" />

Elaboration:
# Purpose:
I2C is primarily used for communication between ICs within a system, especially in scenarios where multiple devices need to interact on a limited number of wires. 
# Serial Communication:
It's a serial protocol, meaning data is transmitted bit by bit over the two lines, unlike parallel communication which transmits multiple bits simultaneously. 
# Master-Slave Architecture:
I2C operates on a master-slave architecture, where one or more master devices initiate and control communication with one or more slave devices. 
# Two-Wire Interface:
The core of I2C is its two-wire interface:
SDA (Serial Data): A bi-directional line for transmitting data. 
SCL (Serial Clock): A uni-directional line for synchronizing data transfer. 
# Applications in VLSI:
I2C is commonly used in VLSI designs for various purposes, including:
Communication between microcontrollers and peripherals (sensors, memory, etc.). 
Interface with LCDs, EEPROMs, and other integrated circuits. 
# Data Transfer Rates:
I2C supports different data transfer modes with varying speeds:
Standard Mode: Up to 100 kbps. 
Fast Mode: Up to 400 kbps. 
High-Speed Mode: Up to 3.4 Mbps.

# path of work 
The goal of this project is to demonstrate practical VLSI design skills including:
- RTL design and simulation
- Logic synthesis with constraints
- Equivalence checking
- Timing closure
- Floorplanning, placement, clock tree synthesis (CTS), and routing
- DRC, LVS, and Antenna rule checks
- Final GDSII generation

This project serves as a learning and showcase platform for digital design engineers and students interested in ASIC Physical Design.






