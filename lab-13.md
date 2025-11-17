# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 13

## Task 1
Write a code to drive differential drive robot with two dc motors using L298 motor driver.

Circuit:
![Lab 13 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-13/CSE-06133118-2502-lab13-task-1-3CKT_bb.png)


Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;

void setup() {
  pinMode(mls1,OUTPUT);
  pinMode(mls2,OUTPUT);
  pinMode(mrs1,OUTPUT);
  pinMode(mrs2,OUTPUT);
  pinMode(mlen,OUTPUT);
  pinMode(mren,OUTPUT);
  Serial.begin(115200);
  //Without PWM at first
  digitalWrite(mlen,HIGH);
  digitalWrite(mren,HIGH);
}

void loop() {
  //Moving forward
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
  delay(1000);


  //Moving backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,HIGH);
  //Right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,HIGH);
  delay(1000);

  //Stop
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
  delay(1000);

  //Moving right
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
  delay(1000);

  //Moving left
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
  delay(1000);
  
}
```

## Task 2
Write a code to drive differential drive robot with two dc motors using L298 motor driver. Different movement should be incorporated using individual functions.

Circuit:
![Lab 13 Task 2 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-13/CSE-06133118-2502-lab13-task-1-3CKT_bb.png)

Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;

void setup() {
  pinMode(mls1,OUTPUT);
  pinMode(mls2,OUTPUT);
  pinMode(mrs1,OUTPUT);
  pinMode(mrs2,OUTPUT);
  pinMode(mlen,OUTPUT);
  pinMode(mren,OUTPUT);
  Serial.begin(115200);
  //Without PWM at first
  digitalWrite(mlen,HIGH);
  digitalWrite(mren,HIGH);
}

void loop() {
  moveForward();
  delay(1000);
  moveBackward();
  delay(1000);
  stopCar();  
  delay(1000);
  moveForwardRight();
  delay(1000);
  moveForwardLeft();
  delay(1000);  
  moveForward();
  delay(1000);
  moveForwardRight();
  delay(1000);
}

void moveForward(){
  //Moving forward
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
}

void moveBackward(){
  //Moving backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,HIGH);
  //Right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,HIGH);
}

void stopCar(){
  //Stop
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveForwardRight(){
  //Moving right
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveForwardLeft(){
  //Moving left
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
}

void moveBackwardRight(){
  //Moving right
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,HIGH);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveBackwardLeft(){
  //Moving left
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,HIGH);
}
```

## Task 3
Write a code to drive a differential drive robot with two dc motors with variable speed using L298 motor driver. Different movement should be incorporated using individual functions.

Circuit:
![Lab 13 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-13/CSE-06133118-2502-lab13-task-1-3CKT_bb.png)

Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;

void setup() {
  pinMode(mls1,OUTPUT);
  pinMode(mls2,OUTPUT);
  pinMode(mrs1,OUTPUT);
  pinMode(mrs2,OUTPUT);
  pinMode(mlen,OUTPUT);
  pinMode(mren,OUTPUT);
  Serial.begin(115200);
}

void loop() {
  moveForward(50);
  delay(1000);
  moveBackward(50);
  delay(1000);
  stopCar();  
  delay(1000);
  moveForwardRight(50);
  delay(1000);
  moveForwardLeft(50);
  delay(1000);  
  moveForward(100);
  delay(1000);
  moveForwardRight(100);
  delay(1000);
}

void moveForward(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving forward
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
}

void moveBackward(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,HIGH);
  //Right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,HIGH);
}

void stopCar(){
  //Stop
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveForwardRight(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving right
  //Left motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2,LOW);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveForwardLeft(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving left
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2,LOW);
}

void moveBackwardRight(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving right
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,HIGH);
  //Right motor stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,LOW);
}

void moveBackwardLeft(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen, pwmVal);
  analogWrite(mren, pwmVal);
  //Moving left
  //Left motor stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2,LOW);
  //Right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2,HIGH);
}
```


## Home Task
1. Complete the codes shown in lab and capture video to show in next class
2. Make a frame of car using 2 motors and a cator wheel. This will be needed in next lab. 
![Light Follower Robot Structure](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/light%20Follower.png)

## Things to bring in next lab
1. Car with 2 motor made for home task
2. LDR 3pc
3. Servo motor
