# ESP32 Binary Adder & Subtractor

A 1-bit Full Adder and Full Subtractor implemented using an ESP32.

The project uses push buttons as binary inputs and LEDs to display the input states and calculated outputs.

## Project Overview

This project combines a Full Adder and Full Subtractor into a single ESP32-based circuit.

A mode input determines which operation is performed:

- M = 0 → Full Adder
- M = 1 → Full Subtractor

The ESP32 reads the binary inputs from push buttons, performs the required Boolean logic, and displays the result using LEDs.

## Features

- 1-bit Full Adder
- 1-bit Full Subtractor
- Push-button binary inputs
- LED-based input indicators
- LED-based output indicators
- Mode selection between addition and subtraction
- Implemented using ESP32

## Inputs

| Input | GPIO | Description |
|---|---:|---|
| M | GPIO 23 | Mode selection |
| A | GPIO 19 | First binary input |
| B | GPIO 18 | Second binary input |
| Cin / Bin | GPIO 17 | Carry-in / Borrow-in |

### Mode

| M | Operation |
|---|---|
| 0 | Full Adder |
| 1 | Full Subtractor |

## Outputs

| Output | GPIO | Description |
|---|---:|---|
| Sum / Difference | GPIO 2 | Result output |
| Carry / Borrow | GPIO 15 | Carry or borrow output |

## LED Indicators

| LED | GPIO | Function |
|---|---:|---|
| LED1 | GPIO 22 | Mode |
| LED2 | GPIO 21 | A |
| LED3 | GPIO 5 | B |
| LED4 | GPIO 16 | Cin / Bin |
| LED5 | GPIO 2 | Sum / Difference |
| LED6 | GPIO 15 | Carry / Borrow |

## Full Adder

The Full Adder performs:

    A + B + Cin

Boolean expressions:

    Sum = A ⊕ B ⊕ Cin

    Carry = AB + Cin(A ⊕ B)

### Full Adder Truth Table

| A | B | Cin | Sum | Carry |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## Full Subtractor

The Full Subtractor performs:

    A - B - Bin

Boolean expressions:

    Difference = A ⊕ B ⊕ Bin

    Borrow = A'B + Bin(A ⊕ B)'

### Full Subtractor Truth Table

| A | B | Bin | Difference | Borrow |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

## Components Required

- ESP32 development board
- Breadboard
- 4 push buttons
- 6 LEDs
- 6 × 220Ω/330Ω resistors for LEDs
- 4 × 10kΩ resistors if external pull-downs are used
- Jumper wires
- USB cable

## Working

The four push buttons represent:

    M, A, B, Cin/Bin

Each button toggles between logic 0 and logic 1.

The ESP32 reads these states and performs either addition or subtraction depending on the mode.

### Example

For:

    M = 0
    A = 1
    B = 1
    Cin = 0

The circuit performs:

    1 + 1 + 0 = 10

Therefore:

    Sum = 0
    Carry = 1

For:

    M = 1
    A = 1
    B = 1
    Bin = 0

The circuit performs:

    1 - 1 - 0 = 0

Therefore:

    Difference = 0
    Borrow = 0
