# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 14

## Task 1
Design a line following car that can follow a black line on white background.

![Line Follower Robot Structure](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-15/line%20Follower.png)
Line follower robot is a type of autonomous robot that uses infrared sensors to detect the presence of a line on the ground and follow it. The robot typically has three or more infrared sensors placed on the front bottom, which allows it to determine whether it is on the line or off the line. Based on the readings from these sensors, the robot can adjust its movement to stay on the line.
The IR sensors are used to detect the line by emitting infrared light and measuring the reflection. When the robot is on the line, the sensors will detect a strong reflection, while when it is off the line, the reflection will be weak or absent.
The circuit for the IR sensors typically consists of an IR LED and a photodiode or phototransistor. The IR LED emits infrared light, which is reflected by the surface below. The photodiode or phototransistor detects the reflected light and sends a signal to the microcontroller, which can then determine whether the robot is on the line or off the line.
IR sensor connection
![IR sensor connection](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-15/IR%20Sensor%20Circuit.png)


Circuit:

//To be done by students



Code
```c
//To be done by students
```

## Home Task (For Advanced Learners)
### Obstacle Avoidance Robot:

Obstacle avoidance robot is a type of autonomous robot that uses ultrasonic sensors or even IR sensors to detect obstacles in its path and avoid them. The robot typically has one or more ultrasonic sensors placed on the front, which allows it to measure the distance to the nearest obstacle. Based on the readings from these sensors, the robot can adjust its movement to avoid collisions.
For short distances, IR sensors can be used. The IR sensors work by emitting infrared light and measuring the reflection. When the robot is close to an obstacle, the reflection will be strong, indicating that the robot should stop or change direction.
For moderate distances, instead of IR sensors, ultrasonic sensors are used. Ultrasonic sensors work by emitting a high-frequency sound wave and measuring the time it takes for the sound wave to bounce back after hitting an obstacle. The distance to the obstacle can be calculated based on the speed of sound and the time taken for the sound wave to return.
For long distances, LIDAR sensors can be used. LIDAR (Light Detection and Ranging) sensors work by emitting laser beams and measuring the time it takes for the light to bounce back after hitting an obstacle. The distance to the obstacle can be calculated based on the speed of light and the time taken for the light to return.

Circuit:

//To be done by students

Code:
```c
//To be done by students
```
