# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 12

## Task 1
Write an arduino code change the status of LED (on or off) based on switch input with a debounce delay of 100ms. 

Circuit:
![Lab 12 Task 1 Circuit in breadboard]((https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-12/CSE-06133118-2502-lab12-task-1CKT_bb.png)

Code:
```c
int switchPin=4;
int switchStatus=LOW;
int lastSwitchStatus= LOW;
int ledPin=13;
bool ledStatus=LOW;
long lastDebounceTime=0;
long debounceDelay=50;

void setup() {
  pinMode(ledPin, OUTPUT);
  pinMode(switchPin, INPUT);
}

void loop() {
  int reading=digitalRead(switchPin);
  if(reading!=lastSwitchStatus)
  {
    lastDebounceTime=millis();
  }
  if((millis()-lastDebounceTime)>debounceDelay){
    if(reading!=switchStatus){
      switchStatus=reading;
    }
    if(switchStatus==HIGH){
      ledStatus=!ledStatus;
    }   
  }

  digitalWrite(ledPin,ledStatus);
  lastSwitchStatus= reading;
}
```

## Task 2
Using switch with interrupt.

Circuit:
![Lab 12 Task 2 Circuit in breadboard]((https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-12/CSE-06133118-2502-lab12-task-2CKT_bb.png)

```c
int ledPin=13;
bool ledStatus=LOW;

void setup() {
  pinMode(ledPin, OUTPUT);
  attachInterrupt(0, ledToggle, FALLING);
}

void loop() {
}

void ledToggle()
{
  ledStatus=!ledStatus;
  digitalWrite(ledPin, ledStatus);
}

```

## Task 3
Driving DC motor using L298 motor driver module.

Circuit:
![L298 Motor Driver Module pinout](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-12/l298n-module-pinout.jpg)
![Lab 12 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-12/CSE-06133118-2502-lab12-task-3-4CKT_bb.png)


Code:
```c
int in1=3;
int in2=4;
int enA=5;
void setup() {
  pinMode(in1,OUTPUT);
  pinMode(in2,OUTPUT);
  pinMode(enA,OUTPUT);
  Serial.begin(115200);
}

void loop() {
  digitalWrite(enA, HIGH); //output is enabled
//  digitalWrite(enA, LOW); //output is disabled
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  Serial.println("Rotate in one direction");
  delay(1000);
  
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  Serial.println("Rotate in opposite direction");
  delay(1000);
}
```

## Task 4
Varying Speed of DC motor using L298 motor driver module.

Circuit:
![Lab 12 Task 4 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-12/CSE-06133118-2502-lab12-task-3-4CKT_bb.png)

Code:
```c
int in1=3;
int in2=4;
int enA=5;
void setup() {
  pinMode(in1,OUTPUT);
  pinMode(in2,OUTPUT);
  pinMode(enA,OUTPUT);
  Serial.begin(115200);
}

void loop() {
  analogWrite(enA, 125); //Varying the speed by providing a vaue from 0-255
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  Serial.println("Rotate in one direction");
  delay(1000);
  
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  Serial.println("Rotate in opposite direction");
  delay(1000);
}
```
