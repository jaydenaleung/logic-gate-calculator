Logic Gate Calculator
=====

A custom calculator on a printed circuit board (PCB), made entirely from logic gates. The calculator takes in any number of inputs from 0-9 and can output their sum (up to 9).
-----

**GitHub Link:** [https://github.com/jaydenaleung/logic-gate-calculator](github.com/jaydenaleung/logic-gate-calculator). Included: KiCad project file/gerbers, pictures of schematic and PCB layout/render, bill of materials, README, and .step CAD file.

**Demo Link:** 

**Hours Spent:** 20

## Overview

*Logic Gate Calculator (LGC)* is a PCB that employs multiple buttons, each mapped to a digit 0-9, and sums them when pressed. This sum is shown by lighting up an LED mapped to a specific output 0-9. The PCB is powered by a 5-12V and a ground pin, regulated to 5V. I hand-soldered all the through-hole components myself!

[PCB IRL picture]

[PCB render in KiCad]

## Why I Did This Project

This project began as an assignment for the prerequisite course to the **2026 MIT BeaverWorks Basics of ASICs** program. Since I did also that course the year before, I wanted to go further with the assignments. I took our material on logic gates to the max and decided to build a simple calculator from scratch, for which I did some extra research on adders/half-adders. This was just a fun little project! I really learned a lot about the fine complexities of computing.

## Background

To lock in the theory, I first built every logic gate from bare transistors. I used those logic gates to build the adders and the binary/decimal encoders/decoders for the calculator. 

[Picture of schematic theory]

In the end, I came up with a pipeline that: 
1. **Takes in** inputs from push-buttons (corresponding to digits 0-9)
2. **Encodes** them into binary using the Texas Instruments xxxx IC
3. **Inverts** the numbers (0 -> 1, 1 -> 0) due to the encoder's active-low nature, using the TI xxxx IC
4. **Adds** the binary values using the TI xxxx 4-bit adder
5. **Decodes** the binary values into decimal outputs (up to 9) using the TI xxxx IC
6. **Activates** LEDs corresponding to the output digit (0-9)

[Picture of schematic build]

## Key Lessons

Initially, after soldering the components onto the entire PCB, I could not figure out why the voltage fluctuated randomly where it was supposed to be 5V. I suspected that an **unconnected ground was picking up electrical noise** or the **voltage regulator was fried from an accidental short**, I resoldered the entire board - only to find out that the issue was **electrostatic discharge (ESD)**. (This is why I am wearing rubber gloves in the demo.) I learned that the L392N and other widely-used ICs are **generally resilient** to low-voltage, quick shorts and that ESD is a larger issue when **handling PCBs**.