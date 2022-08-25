---
title: "CircuitBrains Basic"
date: 2020-02-10T16:10:00-05:00
description: CircuitPython on an ARM Cortex M0 in 1 square inch!
draft: false
hideToc: false
enableToc: false
enableTocContent: false
author: Kevin Neubauer
tags:
- CircuitPython
- project
- electronics
- hardware
pinned: false
image: images/CBBasic/CB_Basic_Diagonal_150x150.png
---
![CircuitBrains Basic](/images/CBBasic/CB_Basic_Diagonal_800x800.png)
### Summary:
CircuitPython on an ARM Cortex M0 in 1 square inch! This “Just Add Solder” castellated module is perfect for incorporating into your own project. The CircuitBrains Basic board footprint is small enough to fit into narrow spaces and wearable projects.

Rolling your own microcontroller board is time consuming. You have to make sure your design has proper power, decoupling, flash storage, and clock. Then you source all of the parts. After that you lay out the PCB and have it fabricated. When the PCB and parts arrive, you have to deal with finicky small-pitch surface mount assembly. Finally, you need to download the sources for the UF2 bootloader and CircuitPython and define your board, compile, and flash. CircuitBrains Deluxe aims to save makers and hackers some time & frustration. Using it in your project is as simple as importing the footprint libraries, adding those libraries to your schematic and layout (along with your USB port of choice), and soldering it on once your board arrives.

### Project Status:
Version 1.2 tested good for CircuitPython. Retired product.

### Goals:
Reduce barriers to entry for custom CircuitPython-based boards & badges
Package CircuitPython into a small form-factor module that will add minimal dimensions to a parent project

### Specs:
 * Dimensions: 25 x 25 x 3.5 millimeters / 1 x 1 x 0.15 inches
 * Atmel ATSAMD21E18 Microcontroller (32-bit ARM Cortex M0)
 * 48 MHz
 * 32 KB SRAM
 * 256 KB Flash
 * 4 MB SPI Flash
 * Onboard 3.3V LDO Regulator
 * Power and Status LEDs
 * Breakouts for SPI and I2C
 * Breakouts for 4 Analog and 8 Digital Inputs/Outputs

### Links:
https://github.com/neubauek/CircuitBrains

### Additional Photos:
![CircuitBrains Basic](/images/CBBasic/CB_Basic_Top_800x800.png)
![CircuitBrains Basic Pinout](/images/CBBasic/CB_Basic_v1.2_Pinout.png)