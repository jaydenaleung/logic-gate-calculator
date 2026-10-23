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

## Why I Did This Project

This project began as an assignment for the prerequisite course to the **2026 MIT BeaverWorks Basics of ASICs** program. Since I did also that course the year before, I wanted to go further with the assignments. I took our material on logic gates to the max and decided to build a simple calculator from scratch, for which I did some extra research on adders/half-adders. This was just a fun little project! I really learned a lot about the fine complexities of computing.

## Background

To lock in the theory, I first built every logic gate from bare transistors. I used those logic gates to build the adders and the binary/decimal encoders/decoders for the calculator. 

<img width="2000" height="855" alt="Screenshot_2026-03-28_at_6 36 09_PM" src="https://github.com/user-attachments/assets/71f401ff-4553-48c2-96e2-bd65b4c56420" />

<img width="1190" height="1101" alt="Screenshot_2026-03-28_at_6 36 26_PM" src="https://github.com/user-attachments/assets/61fca96f-e937-4ed2-8604-282b5e6fdac9" />

In the end, I came up with a pipeline that: 
1. **Takes in** inputs from push-buttons (corresponding to digits 0-9)
2. **Encodes** them into binary using the Texas Instruments 74HC147 denary to binary IC
3. **Inverts** the numbers (0 -> 1, 1 -> 0) due to the encoder's active-low nature, using the TI 74HC04 inverter IC
4. **Adds** the binary values using the TI 74HC283 adder 4-bit adder
5. **Decodes** the binary values into decimal outputs (up to 9) using the TI 74HC42 binary to denary IC
6. **Activates** LEDs corresponding to the output digit (0-9)

<img width="1267" height="1159" alt="Screenshot_2026-03-28_at_6 36 48_PM" src="https://github.com/user-attachments/assets/795fc328-81f5-4a5c-9c1a-10073d40263a" />

<img width="500" alt="Screenshot_2026-03-28_at_6 37 48_PM" src="https://github.com/user-attachments/assets/fb35ae64-c970-46ed-a1d8-ff6f56650032" />
<img width="500" alt="Screenshot_2026-03-28_at_6 24 48_PM" src="https://github.com/user-attachments/assets/4074bba1-6c35-4b86-beec-4d1f679a0a53" />

## Key Lessons

Initially, after soldering the components onto the entire PCB, I could not figure out why the voltage fluctuated randomly where it was supposed to be 5V. I suspected that an **unconnected ground was picking up electrical noise** or the **voltage regulator was fried from an accidental short**, I resoldered the entire board - only to find out that the issue was **electrostatic discharge (ESD)**. (This is why I am wearing rubber gloves in the demo.) I learned that the L7805 linear regulator and other widely-used ICs can be **generally resilient** to low-voltage, quick shorts and that ESD is a larger issue when **handling PCBs**.
