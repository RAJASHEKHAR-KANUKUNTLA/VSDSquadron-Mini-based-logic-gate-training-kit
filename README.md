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
  
## Source Code
``` c++
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

#define I2C_ADDR 0x27
#define LCD_COLUMNS 20
#define LCD_ROWS 4


// Define pin numbers for inputs, output, gate selection buttons, and reset button
const int inputPins[2] = {PD1, PD2};
const int outputPin = PD3;
const int gateSelectPins[6] = {PC0, PC3, PC4, PC5, PC6, PC7};
const int resetButtonPin = PD7;
const int buzzerPin = PD4;

// Create the LCD and OLED objects
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_ROWS);

// Variables to store inputs, output, and selected gate
bool inputs[2] = {0, 0};
bool output = 0;
int selectedGate = 0;

// Function to read input switches
void readInputs() {
  for (int i = 0; i < 2; i++) {
    inputs[i] = digitalRead(inputPins[i]);
  }
}

// Function to update output based on the selected logic gate
void updateOutput() {
  switch (selectedGate) {
    case 0: // AND
      output = inputs[0] && inputs[1];
      break;
    case 1: // OR
      output = inputs[0] || inputs[1];
      break;
    case 2: // XOR
      output = inputs[0] ^ inputs[1];
      break;
    case 3: // NAND
      output = !(inputs[0] && inputs[1]);
      break;
    case 4: // NOT (using only the first input)
      output = !inputs[0];
      break;
    case 5: // NOR
      output = !(inputs[0] || inputs[1]);
      break;
  }
}

// Function to update the output LED
void updateLED() {
  digitalWrite(outputPin, output);
}

// Function to display status on the LCD
void updateLCD() {
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Gate: ");
  switch (selectedGate) {
    case 0: lcd.print("AND"); break;
    case 1: lcd.print("OR"); break;
    case 2: lcd.print("XOR"); break;
    case 3: lcd.print("NAND"); break;
    case 4: lcd.print("NOT"); break;
    case 5: lcd.print("NOR"); break;
    
  }

  lcd.setCursor(0, 1);
  lcd.print("Inputs: ");
  lcd.print(inputs[0]);
  lcd.print(", ");
  lcd.print(inputs[1]);

  lcd.setCursor(0, 2);
  lcd.print("Output: ");
  lcd.print(output);
  delay(500);
}

// Function to update OLED with gate symbol and input/output status


// Function to reset the system
void resetSystem() {
  selectedGate = 0;
  inputs[0] = 0;
  inputs[1] = 0;
  output = 0;
  updateLED();
  updateLCD();
}

// Function to check gate selection and play buzzer on change
void checkGateSelection() {
  for (int i = 0; i < 6; i++) {
    if (digitalRead(gateSelectPins[i]) == LOW) {
      selectedGate = i;
      
   //  Tone(buzzerPin, 1000, 100); // Short beep when a gate button is pressed
      //digitalWrite(buzzerPin, HIGH);
      playTone(440, 500); 
      delay(300);
    }
  }
}

void playTone(int frequency, int duration) {
    // Calculate the delay for each cycle (in microseconds)
    long delayTime = 1000000L / frequency / 2;  // Divide by 2 for half-cycle
    
    // Calculate the number of cycles for the specified duration
    long numCycles = frequency * duration / 1000;

    // Generate the tone by toggling the buzzer pin
    for (long i = 0; i < numCycles; i++) {
        digitalWrite(buzzerPin, HIGH);     // Set buzzer pin high
        delayMicroseconds(delayTime);      // Wait for half of the cycle

        digitalWrite(buzzerPin, LOW);      // Set buzzer pin low
        delayMicroseconds(delayTime);      // Wait for the other half
    }
}

void setup() {
  lcd.init();
  lcd.backlight();
  lcd.begin(LCD_COLUMNS, LCD_ROWS);
  lcd.print("Logic Gates Setup");

  for (int i = 0; i < 2; i++) {
    pinMode(inputPins[i], INPUT_PULLUP);
  }
  pinMode(outputPin, OUTPUT);
  
  for (int i = 0; i < 6; i++) {
    pinMode(gateSelectPins[i], INPUT_PULLUP);
  }
  pinMode(resetButtonPin, INPUT_PULLUP);
  pinMode(buzzerPin, OUTPUT);

  resetSystem();
}

void loop() {
  if (digitalRead(resetButtonPin) == LOW) {
    resetSystem();
    delay(300);
  }
  
  readInputs();
  checkGateSelection();
  
  updateOutput();
  updateLED();
  updateLCD();

  delay(10);
}
```

# Image of the project
![project](https://github.com/user-attachments/assets/cc681cf4-fd7b-4d0b-9f32-271c3bc34601)

# Demonstration Video of the project


https://github.com/user-attachments/assets/f0fb7b55-fdf2-43a8-a26f-188d911bad69

### Conclusion

The VSDSquadron Mini Logic Gate Learning Project offers an innovative, hands-on approach for beginners to explore and understand the fundamental principles of digital logic gates. By combining an interactive hardware setup, real-time visual and auditory feedback, and a versatile RISC-V based microcontroller, this project bridges the gap between theoretical concepts and practical implementation. It provides an engaging alternative to traditional training kits, fostering a deeper understanding of digital electronics through experimentation and active learning. This system is ideal for students, educators, and enthusiasts looking to strengthen their foundational knowledge in electronics and logic design in a practical, affordable, and effective way.

## Author

- [Rajashekhar Kanukuntla](https://github.com/RAJASHEKHAR-KANUKUNTLA), Bachelor of Technology in Electronics &Communication Engineering ,University College Of Engineering Kakatiya University, kothagudem,Telangana.
