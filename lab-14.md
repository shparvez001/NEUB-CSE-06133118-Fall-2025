# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 14

## Task 1
Driving a Servo motor.

Circuit:
![Lab 14 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-14/CSE-06133118-2502-lab14-task-1CKT_bb.png)


Code:
```c
#include<Servo.h>

Servo servo1;
int servo1pin=9;
int value;

void setup()
{
  servo1.attach(servo1pin);
  Serial.begin(115200);
}

void loop()
{
  if(Serial.available()>0)
  {
    value=Serial.read(); //Expecting value of 0 - 9
    value=value-48;
    if(value<=9&&value>=0)
    {
      value=value*20;
      servo1.write(value);
      Serial.print("Angle is ");
      Serial.println(value);
    }
    else{
      Serial.println("Angle out of bound");
    }
  }
}
```

## Task 2
Design a Light Follower Robot with 3 LDR.


Code:
```c
//To be done by students
```
