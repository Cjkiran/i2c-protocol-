# RTL to GDS2 @2025-2026

I2C stands for Inter-Integrated Circuit. It's a serial communication protocol used for short-distance communication between integrated circuits. This protocol facilitates data exchange between a master device and multiple slave devices over a shared bus, often utilizing two lines: Serial Clock (SCL) and Serial Data (SDA). 

<img width="613" alt="image" src="https://github.com/user-attachments/assets/963ec0a5-1f00-4cbf-88d9-a44f8d607005" />

I2C stands for Inter-Integrated circuit. It can also be referred to as IIC or I2C. I2C Protocol is a serial communication protocol, and it is widely used for short-distance communication. It provides simple and robust communication between the Peripheral device and the microcontroller.

I2C Protocol consists of two wires SDA and SCL which is bidirectional synchronous serial bus communication. Thus, I2C Protocol takes two wires for communication which also translates to low cost and this low cost has made I2C Protocol the most commonly used Serial Bus across most applications including IoT, consumer electronics, automotive, aerospace, and industrial equipment.

I2C Protocol is a synchronous protocol that allows a master to initiate communication with a slave device. I2C protocol is a master-slave communication where the master provides the clock which becomes the data transfer rate or clock frequency. It is a bi-directional bus meaning the master can write to the slave and read from the slave it is a serial bus which means data is a clock and it is shifted bit by bit and there are two bus lines serial clock (SCL) and serial data (SDA).

As u see in the diagram three slaves are connected to the same I2C Master and there is two pull-up resistor which is required for the I2C device to communicate properly this is because the I2C protocol works on the SCL and SDA bus lines which are an open drain or open collector the transmitting device just lets go of the I2C bus to create logic one and pulls or drives the line the ground to create logic 0.

I2C Protocol there are 5-speed categories including standard mode, fast mode, fast plus mode, high-speed mode, and ultra speed mode these speed categories range from 100 kHz to 5MHz, where standard mode is 100KHz, Fast mode is 400KHz, Fast mode plus is 1MHz, High-Speed Mode is 3.4MHz and Ultra-fast mode is 5MHz. 100KHz up to 1MHz are very similar, while 3.4 MHz needs some special consideration, and 5MHz being unidirectional requires even more special attention. But the most common speed categories for I2C Protocol are Standard mode, Fast Mode, and Fast mode plus these modes are easy to implement.

I2C Protocol transactions are initiated with a start condition, the start condition is defined as the master driving SDA line low while SCL remains high, and note that it must be initiated with the I2C bus in an idle state means SDA and SCL lines are both high.

The slave address immediately follows the start condition, and it will be 7 bits or 10 bits long it should be noted that each device on the I2C bus needs a unique slave address. Next is the read-and-write bit, which immediately follows the slave’s address, this bit informs the slave if the master wants to read or write. 1 indicates the master wants to read from the slave and 0 indicates the master wants to write.

The next section is the Acknowledge bit and we can think of ack bits like a handshake between the master and slave and they occur on every 9th clock cycle, if ACK is 0 then data can be transmitted, and if ACK is 1 data cannot be sent. Next is the data byte which contains the information being transferred between the master and slave, It contains 8 bits of data.

The last section of the I2C protocol is the Stop condition all I2C transactions should be terminated with a stop condition, the stop condition is defined as the master releasing the line while the SCL signal level is high after a stop condition the I2C bus will remain in idle state and won’t be free for the next I2C transaction.

There are two important concepts of I2C Protocol: I2C Arbitration and I2C Clock Stretching

# I2C Arbitration: 
I2C Protocol is a multi-master bus it can be possible that multiple masters are driving the bus simultaneously, If one of them detects SDA is low when it should be high, it assumes that another master is active and immediately stop its transfer.

# I2C Clock Stretching:
The master wants to send the data where the slave is not ready to receive data so the  I2c slave pulls the SCL line low.

# Advantages:
I2C Protocol supports multi-master, multi-slave communication
It uses only two wires
In I2C Protocol ACK/NACK functions can be proved useful for error handling
Adaptable as it can adapt to the needs of various slave device
In I2C Protocol the addressing is very simple and does not need any CS lines to add extra devices like SPI Protocol
It uses flow control

# Disadvantages:
I2C Protocol is a half-duplex mode of communication
The hardware complexity increases when the number of master/slave devices is more in the circuit
Many devices have multiple addresses stored which can cause conflicts

# Applications of I2C Protocol:
Accessing DACs and ADCs
Reading certain memory ICs
Reading hardware sensors
Communicating with multiple micro-controller
Transmitting and controlling user-directed actions



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
LICENSE @ VIT-10.10.5.247 -24MVD0166  







