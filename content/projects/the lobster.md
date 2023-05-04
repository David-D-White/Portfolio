+++
date = "2023-03-24"
title = "The Lobster PCB Mill"
+++
# Project in Action
{{<video library="1" src="video/FYDP.mp4" width="100%">}}

# About the Project
### Machine Capabilities
{{<gallery-slider dir="image/lobster_mill/capabilities" width="48em" height="27em" auto-slide="5000" 
captions="0.1mm trace width;Passives: 1210 to 0201;SOP and MSOP footprints;SOT footprints">}}

[The Lobster PCB Mill](https://thelobsterteam.github.io) is a fully automated PCB prototyping solution which aims to do for PCB design what 3D printing did for mechanical design. This project was designed and developed as my capstone project for the Mechatronics Engineering program at University of Waterloo. The machine is capable of producing 2-layer prototype PCBs with 0.1mm trace spacing, 0.5mm component size (0402), and 0.5mm vias without any user interaction. The project code is fully [open source](https://github.com/orgs/TheLobsterTeam/repositories)

### Mechanical
{{<gallery-slider dir="image/lobster_mill/mechanical" width="48em" height="27em" auto-slide="5000"
captions="3 Independent Toolheads;Automatic Flipping Mechanism;Wire Feeding Head;Vaccuum for Dust Collection">}}

The mechanical design of the mill is fully custom, featuring 3 individually controlled toolheads for milling/drilling, a PCB flipping mechanism, a mechanical press, and a wire extrusion head. The XY motion carriage uses linear rails and 2mm pitch lead screws with anti-backlash nuts for precise motion. Other components such as the wire feeding head, press, and milling heads use lead screws with a higher pitch and linear rods to save cost where precise motion is less important. BLDC motors and drone ESCs are used to power the drilling/milling heads, and a single servo motor actuates the wire cutters used on the wire feeding head. 

The machine produces PCBs by first drilling holes for vias and through-hole components with 2 of the 3 toolheads. Wire is fed into each of the via holes, cut to length, and pressed to form an electrical connection between the top and bottom layers. An engraving head then mills out any copper where it isn't needed, forming the final board (similarly to chemical PCB etching). 

### Computer Vision
{{<gallery-slider id="1" dir="image/lobster_mill/cv" width="48em" height="27em" auto-slide="5000"
captions="Wire Overlay;Wire Curvature Compensation;Image Masks">}}

Computer Vision is used during the wire alignment process to account for any bends or variations in the wire as it is fed, as well as to deal with skew issues that arise from the PCB flipping mechanism. Cameras and LEDs mounted on the wire head provide a view of the clippers, via hole, and wire in one shot. The computer vision algorithm isolates the via hole and wire with seperate masks, tracking the position of the wire tip relative to the via hole. By moving proportionally to the detected displacement, the machine can converge on the hole location to reliably feed wire into the hole.


### Firmware
The machine is controlled using a Raspberry Pi, and two control boards (BTT octopus and arduino RAMPS). The machine uses a modified version of Klipper Firmware to communicate with both control boards to handle sensor input, servo control, ESC control, and stepper motor control. The use of klipper allows the machine to take advantage of a multicore 32 bit arm processor and Linux USB camera drivers for computer vision, while offloading the real time motor and sensor processing to the 16 bit control boards.

The modified firmware adds support for multiple toolheads as well as each of the custom motions added (wire cutting, pressing, flipping). The firmware uses microstepping on all axes to increase motion resolution, and additionally implements closed-loop position control using encoders on the x-y axis to compensate for the nonlinearities typical when using the microstepping feature on any stepper driver. 

The modified firmware adds conductive probing on each of the 3 toolheads, and uses it to build a heightmap of the raw material before each PCB is milled. The firmware uses this information and bilinear interpolation to compensate for warping in the PCB material during milling, ensuring a constant cutting depth and width. Skew correction and position offsets were added to the firmware as well to compensate for the distance between toolheads, and misalignment in the pcb flipping mechanism.

The firmware presents a web interface via Octoprint allowing the machine to be controlled with a web browser, and allowing gcode files to be uploaded the same way.

### Shortcomings
{{<gallery-slider dir="image/lobster_mill/failures" width="48em" height="27em" auto-slide="5000" 
captions="0.5mm Via Hole misalignment;QFP package pads too thin">}}
QFP packages are currently not producable since 2 passes are needed to produce enough trace seperation. With further tunining of cutting depth and speed, only 1 pass should be necessary which would make QFP package milling is achievable. Alignment between toolheads is also not perfect since these distances were calibrated manually, implementation of automatic calibration would make this alignment more reliable.

<!-- As a first year project, I created a chess playing robot with two of my friends over the course of a month. The robot can accurately navigate the board, pick up pieces, and perform any legal chess move (including castling and en-passant). The robot can asses the current state of the board, make an informed decision, and execute a chosen move **autonomously**.

The robot was designed using the LEGO NXT robotics kit, and used custom laser cut gears and tracks in the assembly. The movement and control of the NXT robot was programmed in RobotC, communicating with an external phone via **bluetooth** to handle the **computer vision** and decision making. The phone app used to control the robot was programmed in **Java** and compiled using **Android Studio**. The app used **OpenCV** to determine the board state using special colour combinations painted on each piece. The board state was then passed into a **custom neural network** trained to choose the best move from a list of possible moves. This move was then converted to a unique string command, and sent to the NXT via bluetooth, after which the command would be parsed, and the move executed.

During this project, I designed the custom neural network, designed and laser cut the custom gears and gear tracks, designed the claw mechanism and carriage, programmed the movements, and aided in other parts of the design when needed. -->

### **[Project Website](https://thelobsterteam.github.io)**
### **[Project Github](https://github.com/orgs/TheLobsterTeam/repositories)**