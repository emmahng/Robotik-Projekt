# measuring robot "Hubbi"

Measuring robot, which measures the surface area of a room.

Bild


# What it is

Our robot is able to follow a line and register the distance traveled. This data is then used to calculate the surface area of a room.
The line the robot follows has to be installed by the user. It only detects the line, if it´s black. Because it can only turn right in 90 degree angle, the robot is only able to measure square and rectangular rooms. The code will be explained later on. 

# Our ides and its development

At the beginning our motivation was making measuring a big room easier. The first prototype we have built, consisted of two big wheels, one ball bearing, two motors and two distance sensors. We had one sensor in the front to stop as soon as we reach the wall. We installed the second sensor on the left side to keep a continous distance to the wall. The problem was, that the distance sensor wasn´t precise enough to keep a contious distance to the side.  

![image](https://github.com/user-attachments/assets/22ca01b9-d8a9-4d6e-97c8-eaeb77d88511)



As we recognized, that our measurig idea is not realizeable with the use of these two distance sensors, we decided to move on with using three color sensores. Two of them are supposed to recognize a line, which is taped by the user on the outline of the room. A third one is able to detects a transverse line of the next side of the room. This initiates a 90 degree turn to the right.

In the following we will guide you through the process of building and programming your own measuring robot.


# Installation & Prerequisites

1. Get the [LEGO® Education SPIKE™ Prime-Set](https://education.lego.com/de-de/products/lego-education-spike-prime-set/45678/) to build your roboter. 
2. Download the [LEGO® Education SPIKE™ App](https://education.lego.com/de-de/downloads/spike-app/software/) to your computer.


# Building our measuring robot "Hubbi"

We wanted our robot to be compact, robust, efficient and convenient to carry around. 


