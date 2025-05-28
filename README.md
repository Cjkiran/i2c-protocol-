
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


# 🔹 1. RTL Design
Verilog source files for functionality
Required Files:
i2c_master.v
i2c_slave.v
i2c_top.v (optional wrapper for integration)
i2c_defs.vh (optional, for constants/macros)

# 🔹 2. Testbench (for functional verification)
Verifies RTL behavior before synthesis
Required Files:
tb_i2c.v
Stimulus files (stimulus_master.txt, etc.)
Makefile or simulation script (e.g., run_vsim.sh)

# 🔹 3. Synthesis (Design Compiler or Fusion Compiler)
RTL → Gate-level netlist

![Screenshot 2025-05-28 144107](https://github.com/user-attachments/assets/4aed6c77-ec8a-4177-aa2c-cfe84b29c40a)

![POWER (1)](https://github.com/user-attachments/assets/8d6649d1-7f0b-4cf0-b03e-0f755fdbafc3)





Required Files:
synthesis_script.tcl
dc_constraints.sdc (timing/area constraints)
library.db (technology library)
i2c_top.v (RTL top)
i2c_netlist.v (output from synthesis)

# 🔹 4. Formal Verification (Formality)
Checks RTL = Netlist (equivalence)
![Screenshot 2025-05-28 142733](https://github.com/user-attachments/assets/d16f67e1-7510-4153-a0f4-e5045918e1cc)

![Screenshot 2025-05-28 142754](https://github.com/user-attachments/assets/79eebc97-254f-438f-953f-5234c7cd6085)

Required Files:
formality_script.tcl
i2c_top.v (RTL)
i2c_netlist.v (gate-level)
library.db

# 🔹 5. Static Timing Analysis (PrimeTime)
Checks timing after synthesis or post-layout

![Screenshot 2025-05-28 154229](https://github.com/user-attachments/assets/8e34ece2-42aa-4d93-b5b7-1051d7926b9c)

![Screenshot 2025-05-28 154254](https://github.com/user-attachments/assets/04c6c10d-c822-4400-9a80-a4bd5c439e2d)

![Screenshot 2025-05-28 154410](https://github.com/user-attachments/assets/f8f4ea1b-7f9e-4d94-8781-443c1ead7735)

![Screenshot 2025-05-28 142950](https://github.com/user-attachments/assets/b422af08-61e6-413a-afd1-000b1ec8c4c7)

![Screenshot 2025-05-28 143021](https://github.com/user-attachments/assets/3c598f72-2947-4966-9587-afee2493a2eb)


Required Files:
pt_script.tcl
dc_constraints.sdc
i2c_netlist.v
.spef (optional, from PD)
.sdf (optional, back-annotated delay)

# 🔹 6. Physical Design (Fusion Compiler)
Netlist → GDSII
Required Files:
floorplan.tcl
placement.tcl
cts.tcl
routing.tcl
pd_constraints.sdc
i2c_netlist.v
technology.lef or milkyway library
i2c.def (optional intermediate DEF output)
i2c_final.gds (output)

# 🔹 7. Physical Verification (Calibre)
DRC, LVS, Antenna
Required Files:
i2c_final.gds
i2c_final.v (post-layout netlist)
i2c.spice (optional, for LVS)
Rule deck files:
drc.rules
lvs.rules
antenna.rules
Output logs:
drc.log
lvs.log
antenna.log

# 🔹 8. Project Documentation
Helpful Files:
README.md
architecture_diagram.png (block diagram)
report_summary.pdf 
LICENSE 







