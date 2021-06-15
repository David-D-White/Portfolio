+++
date = "2018-12-05"
title = "Autonomous Chess Playing robot"
+++
# Project in Action
{{< video library="1" src="/video/lego-robot.mp4" width="50%">}}

# About the Project
As a first year project, I created a chess playing robot with two of my friends over the course of a month. The robot can accurately navigate the board, pick up pieces, and perform any legal chess move (including castling and en-passant). The robot can asses the current state of the board, make an informed decision, and execute a chosen move **autonomously**.

The robot was designed using the LEGO NXT robotics kit, and used custom laser cut gears and tracks in the assembly. The movement and control of the NXT robot was programmed in RobotC, communicating with an external phone via **bluetooth** to handle the **computer vision** and decision making. The phone app used to control the robot was programmed in **Java** and compiled using **Android Studio**. The app used **OpenCV** to determine the board state using special colour combinations painted on each piece. The board state was then passed into a **custom neural network** trained to choose the best move from a list of possible moves. This move was then converted to a unique string command, and sent to the NXT via bluetooth, after which the command would be parsed, and the move executed.

During this project, I designed the custom neural network, designed and laser cut the custom gears and gear tracks, designed the claw mechanism and carriage, programmed the movements, and aided in other parts of the design when needed.