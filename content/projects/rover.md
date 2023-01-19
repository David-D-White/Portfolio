+++
date = "2022-03-31"
title = "Autonomous All Terrain Rover"
+++
# Project in Action
{{< video library="1" src="video/rover.mp4" width="50%">}}

# About the Project
As an assignment in preperation for 4th year design projects, I created an all-terain autonomous rover with 4 of my friends over the course of a month. The rover is designed to accurately and autonomously navigate an obstacle course containing sandy and rocky terrain, as well as pit traps. The rover is equipped to assess it's position and orientation within the course, and make adjustments accordingly.

The robot was designed around an Arduino Uno, which was programmed in C and handles the sensor input, processing, and control. The robot uses 2 Time of Flight sensors which read distances to the walls of the course, and an IMU which measures angular velocity and linear acceleration to determine the robots orientation and track it's movement through the course. Fusing the data from each of these sensors provides real time tracking of the robots absolute position within the course. The robot is equipped with custom 3D-Printed compliant wheels which feature large notches to help the robot traverse large ledges on the course. The rover features a dual motor gearbox controlled by the microcontroller using an H-bridge IC, and timing belts to couple the rotation of the front and back wheels. This provides the rover with 4WD and tank-like steering, allowing it to turn in place and navigate rough terain more easily.

Throughout this project I was primarily responsible for the mechaical design, including the design of the compliant wheels, as well as sharing responsibility for the navigation code. I also shared responsibility for the overall system design, including sensor selection and high level electrical design.