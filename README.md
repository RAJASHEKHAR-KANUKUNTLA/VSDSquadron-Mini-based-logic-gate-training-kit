# VSDSquadron Mini based logic gate training kit

# Introduction to the VSDSquadron Mini 
The VSDSquadron Mini, is a mini board which is powered by RISCV 32 bit instruction set that elevates the development of the the board to a open source community and give it a new heights in the field of semiconductorIndustry . Whether you’re a new to this board or any experienced person will come to use this board who knows about RISC-V , he/she will be able to program and use this board easily which gives them the real exposure of the embedded system as well as the exposure to real world applications. The VSDSquadron Mini is your ideal companion, of Arduino UNO which is based on 28nm technology and it seamlessly bridges the gap between theory and practical application problems of the real world, offering an on-board flash programmer with single-wire programming protocol to jumpstart your projects in education and development with proficiency and ease with flexibility to powered it with c-type cable.

![vsdquadron mini](https://github.com/user-attachments/assets/66adfd74-4cd6-4792-b88e-6bfadedeca21)



# Key Features of the VSDSquadron Mini 

**Core Processor**


- The board is powered by CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set, which is optimized for high-performance computing providing support for 2-level interrupt pins and supports 24MHz system main clock frequency in the product function itself.

**Robust GPIO Support**


- It Boasts 3 groups of GPIO ports, totalling 15 I/O ports, which enables extensive peripheral connections to other pins and mapping it to the external interrupt capabilities as well.

**High-Speed Memory**


- The VSDQUADRON Mini Board is itself Equipped with 2KB SRAM for volatile data storage, 16KB CodeFlash for programming memory, and it's also providing the additional 1920B for bootloader functionalities.

**Clock and Reset Systems**


- It also Includes a built-in factory-trimmed 24MHz RC oscillator and a 128kHz RC oscillator, plus an external 24MHz oscillator option for variying clocking frequency requirements.



**Flexible Communication Interfaces**


- Offers multiple communication protocols including USART, I2C, and SPI to provide versatile connectivity options.

**On-board Programmer**


- It has a feature of Features on-board CH32V305FBP6 single-wire programming protocol, enhancing development efficiency with seamless code deployment and debugging.

**BOARD SPECS**

The Board specifications in the table format is given below:- 

| **CH32V003F4U6 chip with 32-bit RISC-V core based on RV32EC instruction set** |
| ------------------------------------------------------------------------- 
| SRAM                                                                       2kb onchip volatile sram     16kb external program memory                                    |
| Processor                                                                  24 MHz                                                                                       |
| Sink Current per I/O Pin                                                   8 mA                                                                                         |
| Source Current per I/O Pin                                                 8 mA                                                                                         |
| Input voltage (nominal)                                                    5 V                                                                                          |
| I/O voltage                                                                3.3 V                                                                                        |
| Programmer/debugger                                                        Onboard RISC-V programmer/debugger, USB to TTL serial port support                           |
| SPI                                                                        1x, PC5(SCK), PC1(NSS), PC6(MOSI), PC7(MISO)                                                 |
| I2C                                                                        1x, PC1(SDA), PC2(SCL)                                                                       |
| USART                                                                      1x, PD6(RX), PD5(TX)|


## Overview of the project
This project leverages the VSDSquadron Mini RISC-V based 32-bit microcontroller to create an intuitive system for learning logic gates. Designed for beginners, it offers a practical, interactive approach to understanding digital logic through a combination of LEDs, an LCD display, toggle switches, and a buzzer. The system makes learning easier and more engaging compared to traditional training kits by providing real-time feedback on gate operations.

## Features
- **Interactive Inputs and Outputs**: Toggle switches for binary input and LEDs for output visualization.
- **Real-Time LCD Feedback**: A 20x4 LCD display shows the selected logic gate, input states, and output.
- **Auditory Feedback**: A buzzer signals changes in logic gate selection.
- **Supports Six Logic Gates**: AND, OR, XOR, NAND, NOT, and NOR gates.
- **Customizable and Extendable**: Modify and add additional gates or features as desired.

## Components Used
- VSDSquadron Mini RISC-V based 32-bit microcontroller
- 20x4 LCD display (I2C interface)
- Push buttons for gate selection
- Toggle switches for binary inputs
- LEDs for visual output indication
- Buzzer for auditory feedback
- Resistors and connecting wires

## Circuit Diagram
*Include a link or image of your circuit diagram if available.*

## Code Overview
### Libraries Required
- `Wire.h` for I2C communication
- `LiquidCrystal_I2C.h` for LCD control

### How It Works
1. **Reading Inputs**: Inputs are read using toggle switches that represent binary values (0 and 1).
2. **Gate Selection**: Push buttons allow users to select from six logic gates.
3. **Logic Operation**: The system performs the logic operation based on the selected gate and inputs.
4. **Feedback Display**: Outputs are shown on the LEDs and the LCD display for real-time learning.
5. **Auditory Alerts**: The buzzer provides an audible alert when changing the selected gate.

## Getting Started
### Prerequisites
- Arduino IDE (with RISC-V support)
- VSDSquadron Mini Board Support Package (installable via the Boards Manager in Arduino IDE)
- Required libraries (installable via Library Manager)

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/RAJASHEKHAR-KANUKUNTLA/VSDSquadron-Mini-based-logic-gate-training-kit-.git
   ```
