# Measuring Robot "Hubbi"

![image](https://github.com/emmahng/Robotik-Projekt/blob/main/%22Hubbi%22.jpeg)


# What it is

Our robot is able to follow a line and register the distance traveled. This data is then used to calculate the surface area of a room.
The line the robot follows has to be installed by the user. Because of its simple design, the robot is only able to measure square and rectangular rooms. The code will be explained later on. 

# Our ideas and its development

At the beginning our motivation was making measuring a big room easier. The first prototype we have built, consisted of two big wheels, one ball bearing, two motors and two distance sensors. We had one sensor in the front to stop as soon as we reached a wall. The second sensor was installed on the left side of "Hubbi" in order to keep a continous distance to the wall. Unfortunately this version didn't work because of the insufficient precision of the distance sensor.  

![image](https://github.com/user-attachments/assets/22ca01b9-d8a9-4d6e-97c8-eaeb77d88511)

As we recognized, that our measurig idea is not realizeable with the use of these two distance sensors, we decided to move on with using three color sensors. Two of them are supposed to recognize a line, which is taped by the user on the outline of the room. A third one is able to detect a transverse line in order to initiate a 90 degree turn to the right.

In the following we will guide you through the process of building and programming your own measuring robot.


# Installation & Prerequisites

1. Get the [LEGO® Education SPIKE™ Prime-Set](https://education.lego.com/de-de/products/lego-education-spike-prime-set/45678/) to build your roboter (plus 2 color sensors). 
2. Download the [LEGO® Education SPIKE™ App](https://education.lego.com/de-de/downloads/spike-app/software/) to your computer.

# "Hubbi's" construction

The build of "Hubbi" went through trial and error stages. Eventually - through several iterations - we developed the final design of 'Hubbi'. 

## Design Considerations

We aimed to create a design that was:
Small and robust – to ensure durability while measuring different room layouts.
Easy to assemble – using standard LEGO® Spike Prime components.
Optimized for the given task – with sensors and motors for navigation.

## Building the Robot
![Hubby](https://github.com/emmahng/Robotik-Projekt/blob/main/%22Hubbi%22%20Build%20Process.gif)

### To build your own version of Hubbi, follow these steps:
Gather all necessary components from the LEGO® Spike Prime set.
![image](https://github.com/user-attachments/assets/efb47114-b4c2-4e37-b8c8-0be303b0abd7)
![image](https://github.com/user-attachments/assets/4c99fb6f-3e6c-41e5-8b93-99fdb2591dd2)

Follow the digital building instructions provided by us using BrickLink Studios.  
Ensure proper sensor alignment – the color sensors should be positioned correctly to detect the guiding line.  
Check motor connections – for smooth movement and precise turns.  
Secure all structural elements – to avoid instability while the robot is operating.

![image](https://github.com/user-attachments/assets/9cc233f3-87e1-400f-b00b-2c90a220b91b)
![image](https://github.com/user-attachments/assets/70a4e8ec-d53b-439b-b34a-f79f3a66d3de)  

## Additional Resources
We have provided digital building files in .io format from BrickLink Studio, which you can use to view or modify the design.
If you prefer, you can also create exploded views of the robot to understand how different parts fit together.
For further customization, feel free to experiment with different wheel sizes, sensor placements, or frame modifications.
By following these guidelines, you can build a reliable and effective measuring robot just like "Hubbi"!


# Programming our measuring robot "Hubbi"

To program our measuring robot "Hubbi", we used the LEGO Spike App and its simple programming interface. Don't worry: The app comes with several tutorials and sample projects. So go ahead and try it out for yourself. If you are new to the environment, we recommend the First Steps tutorial to familiarise yourself with the interface and key components.  
To start your own project, open the Spike App and click on "New Project." Name your project and choose the programming language. For this guide, we used text bricks, which allows for easy drag-and-drop coding.
![image](https://github.com/emmahng/Robotik-Projekt/blob/main/Code%20Overview.jpeg)

## Line Following and Detecting Turns

First, we programmed "Hubbi" to detect and follow a coloured line using color sensors. Two sensors on the front continuously check if the robot is on track. If one sensor no longer detects the line, the robot slightly adjusts its course to correct its path.
To move forward both motors drive the wheels at a steady speed of 20%. This ensures smooth and controlled movement.  
Since Hubbi can only turn 90 degrees to the right, we implemented a function that detects a transverse line marking the end of a segment. When the third color sensor detects this line, the robot stops and executes a right turn by rotating one wheel while keeping the other stationary.
![image](https://github.com/emmahng/Robotik-Projekt/blob/main/Code%20Line%20Following%20and%20Turns.jpg)

## Measuring the Room
### Variables used
![image](https://github.com/emmahng/Robotik-Projekt/blob/main/Variablen2.jpeg)

To calculate the surface area, Hubbi tracks the wheel position (in degrees) and stores the traveled distance in the variable "Radumdrehungen". To make the measurement more accurate, we split the wheel position detection into 1/8ths of a full wheel turn, so that every 45° adds 0.125 wheel turns to the "Radumdrehungen" variable.  
After each side of the room the distance (Calculation: "Raddurchmesser" * "Radumdrehungen" * pi) is saved in the variable "Seitenlänge1". "Seitenlänge1" is then saved in "Seitenlänge". Afterwards "Seitenlänge1" and "Radumdrehungen" are set to 0 to measure the next side of the room. Only two sides of the room are necessary to calculate the area of a rectangular room.  
  
The formula used to calculate the area of the room:  
"Fläche" = (("Element 1" of "Seitenlänge" + 24) * ("Element 2" of "Seitenlänge" + 10)) / 1000  
We add the constant 24 to compensate for the length of "Hubbi" from end to the very front.  
We add the constant 10 to compensate for the distance to the wall.  

![image](https://github.com/emmahng/Robotik-Projekt/blob/main/Code%20Measuring.jpg)  

To measure the perimeter of the room "Radumdrehungen(Strecke)" - which is not set to 0 after every turn! - counts the wheel rotations until "Hubbi" detects a blue tape which we defined as "Hubbis" endmark (color can be changed by you).  

The formula used for the perimeter of the room is:  
"Gesamtstrecke" = "Raddurchmesser" * "Radumdrehungen(Strecke)" * pi + 15  
We add the constant 15 to compensate for the length of "Hubbi".  

![image](https://github.com/emmahng/Robotik-Projekt/blob/main/Code%20Radumdrehungen.jpg)



Each time "Hubbi" completes a full circuit around the room, it multiplies the length and width to determine the total area. The formula used is:

Area = Length × Width

We store the wheel rotations in a variable and convert them into centimeters using a predefined conversion factor. This ensures accurate measurements.


## Main Program Structure

Line Following: Moves along the taped outline using two front color sensors.
Right Turn Detection: Uses a third sensor to detect the transverse line and trigger a 90-degree turn.
Distance Measurement: Counts wheel rotations and converts them into room dimensions.
Completion Check: Stops when it detects that it has returned to the starting point.


## Testing and Adjustments

During testing, we fine-tuned the speed, turning angles, and sensor thresholds to improve accuracy. We also ensured that the robot stops precisely at the final position before displaying the calculated area on its screen.
With this setup, Hubbi efficiently measures rectangular and square rooms, providing an automated alternative to manual measurements.


# Lessons Learned and Future Work

During the development of our measuring robot "Hubbi," we gained valuable insights into working with LEGO® Education SPIKE™ Prime components. We learned the importance of precise sensor placement and calibration, especially for the color sensors detecting the black line. The robot's current limitation of only turning right in 90-degree angles taught us about design constraints and sparked ideas for future improvements.

For future iterations of Hubbi, we envision several enhancements:
Implementing a gyroscope for more precise turns and measuring irregular room shapes.
Adding a small LCD screen for real-time feedback on measurements.
Incorporating wireless connectivity for remote control and data transfer.
Exploring ultrasonic sensors to potentially eliminate the need for a pre-taped line.
Integrating basic machine learning to adapt to different floor textures and lighting conditions.

While our current version of Hubbi successfully measures rectangular rooms, these improvements could transform it into a more versatile and user-friendly device. We're excited about the possibilities and look forward to continuing our journey in robotics and automation.





