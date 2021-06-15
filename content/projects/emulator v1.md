+++
date = "2020-02-20"
title = "Handheld Console Emulator"
+++
# Project in Action
{{< video library="1" src="/video/emulator.mp4" width="100%">}}

# About the Project
As an introduction to **Schematic Capture**, **PCB Design**, and **Circuit Design**, I decided to build a custom handheld emulator based around the **Raspberry PI**. For this project, I wanted to create a handheld emulator capable of emulating consoles from the PS1 era and before. I wanted to include analog joysticks for input, a reusable battery and charging circuit, as well as a touch screen for use with Nintendo DS emulation.

The project uses **Emulation Station** on the **Raspberry PI**, **SPI** for analog to digital conversion, includes a LiPo battery and **charging circuit**, and has a headphone jack and micro USB charging port. Analog to digital conversion, input was done in **C++** using the **WiringPi** library and linux **libevdev** to convert the GPIO inputs into OS readable input events.

The entire project, including circuit design, PCB design, mechanical design, programming, and assembly was done over the course of 2 months. The project even includes a custom **3D printed** enclosure with custom buttons.

This project is one of my favourite projects to date, and I have plans to create an improved version based around the Raspberry Pi CM4, making it thinner and adding new features.