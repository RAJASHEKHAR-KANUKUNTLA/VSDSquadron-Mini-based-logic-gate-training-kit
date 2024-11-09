# VSDSquadron Mini based logic gate training kit


## Overview
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
   git clone https://github.com/your-username/vsdsquadron-logic-gate-learning.git
