# stm32-programmable-digital-clock
STM32-based programmable digital clock using external interrupts, ADC, RTC and multiplexed 7-segment displays.
The project was designed to display hours, minutes, and seconds while allowing the user to configure the time through an interrupt-driven interface and an analog potentiometer.

## Project Overview

The objective of this project was to design and implement a programmable digital clock using embedded C and an STM32 microcontroller.

The system uses two 4-digit common-anode 7-segment displays to represent time in an HH:MM:SS format.

A potentiometer connected to the ADC allows the user to modify the time, while an external interrupt is used to select whether the ADC value modifies:

- Seconds
- Minutes
- Hours

The selected value is then stored in the STM32 Real-Time Clock (RTC).

## Features

- Real-time clock implementation using STM32 RTC
- External interrupt-based user control
- Analog-to-Digital Converter (ADC) input
- ADC value scaling for time configuration
- 8-digit 7-segment display
- Display multiplexing
- GPIO control
- Embedded C firmware
- Hardware prototype implementation

## System Architecture

```text
                   Potentiometer
                        │
                        ▼
                       ADC
                        │
                        ▼
Push Button ──► External Interrupt
                        │
                        ▼
                 ┌─────────────┐
                 │    STM32    │
                 │             │
                 │     RTC     │
                 │     ADC     │
                 │    GPIO     │
                 └──────┬──────┘
                        │
              ┌─────────┴─────────┐
              │                   │
              ▼                   ▼
          BCD Decoder        Digit Decoder
            7447                74238
              │                   │
              └─────────┬─────────┘
                        ▼
              8-Digit 7-Segment Display
                     HH:MM:SS
