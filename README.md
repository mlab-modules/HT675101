
# HT675101A - Small Power H-Bridge

![HT675101A](/doc/img/HT675101A_big_top.jpg)

## Description
The HT675101A module features two HOLTEK HT6751B integrated circuits, each implementing a low-power H-bridge suitable for driving small DC motors. It is optimized for applications such as miniature mobile robots or toy motors, handling up to 500 mA per channel with motor supply voltages between 1.8 V and 6 V.

## Features
- Dual independent H-bridge drivers
- Up to 2× 500 mA output current
- Logic supply voltage: 2 V to 6 V
- Motor supply voltage: 1.8 V to 6 V
- N-FET output stages with ~0.4 Ω total on-resistance
- Fast switching: 10 µs ON / 5 µs OFF (at 5 V)
- Built-in thermal shutdown
- Reverse polarity protection and overvoltage suppression
- Compact size: 41×31×16 mm

## Circuit Description

### HT6751 IC
Each HT6751 integrates four switching FETs and internal logic including a charge pump. It supports full H-bridge motor control and includes thermal protection. The logic levels and behavior differ between HT6751A and HT6751B:

#### Logic Table (HT6751B)
| IN1 | IN2 | IN3 | Function       |
|-----|-----|-----|----------------|
| 1   | 0   | 0   | Forward        |
| 0   | 1   | 0   | Reverse        |
| 1   | 1   | 0   | Brake (short)  |
| 0   | 0   | 0   | All off        |
| 1   | 0   | 1   | One transistor |
| 0   | 1   | 1   | One transistor |
| 1   | 1   | 1   | One transistor |

> **Note:** This module uses HT6751B by default. If HT6751A is used instead, pull-up resistors must be installed instead of pull-downs on inputs.

### Assembly Variants
To use HT6751A instead of HT6751B:
- Replace input pull-down resistors (R1–R3, R7–R9) with pull-ups (R4–R6, R10–R12).

## Commissioning
- Use a current-limited or regulated power supply during testing.
- Verify function of both bridges according to the logic table using jumper wires or test harness.

## Notes
- Always ensure motor supply voltage does not exceed 6 V during operation. Absolute maximum is 7 V.
- Ensure proper heat dissipation if running at high currents.
