# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 11

## Task 1
Reading analong value using built-in ADC.

Circuit:
![Lab 11 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-11/CSE-06133118-2502-lab11-task-1CKT_bb.png)

Code:
```c
int sensorPin=A0;
int ledPin=13;
int sensorValue;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  sensorValue=analogRead(sensorPin);
  Serial.println(sensorValue);
  //Turning on and off LED with delay equal to sensorValue
  digitalWrite(ledPin, HIGH);
  delay(sensorValue);
  digitalWrite(ledPin, LOW);
  delay(sensorValue);
}
```

## Task 2
Reading voltage using built-in ADC and showing it in serial monitor.

Circuit:
![Lab 7 Task 2 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-11/CSE-06133118-2502-lab11-task-2CKT_bb.png)

Code:
```c
int sensorPin=A0;
int sensorValue;
float volt;
float vref=5;

void setup() {
  Serial.begin(115200);
}

void loop() {
  sensorValue=analogRead(sensorPin);
  volt=(vref*(float)sensorValue)/1023;
  Serial.println(volt);
}
```

## Task 3
Using LDR as sensor.

Circuit:
![Lab 7 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-11/CSE-06133118-2502-lab11-task-3CKT_bb.png)

Code:
```c
int sensorPin=A0;
int sensorValue;
float volt;
float vref=5;
int ledPin=13;
float threshold=0.7;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  sensorValue=analogRead(sensorPin);
  volt=(vref*(float)sensorValue)/1023;
  Serial.print(sensorValue);
  Serial.print(" ");
  Serial.println(volt);
  if(volt<threshold)
  {
    digitalWrite(ledPin, HIGH);
    delay(100);
  }
  else{
    digitalWrite(ledPin, LOW);
    delay(100);
  }
}
```

## Task 4
Write an arduino code change the status of LED (on or off) based on switch input.

Circuit:
![Lab 7 Task 4 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-11/CSE-06133118-2502-lab11-task-4CKT_bb.png)

Code:
```c
int switchPin=4;
int switchStatus=0;
int ledPin=13;
bool ledStatus=false;

void setup() {
  pinMode(ledPin, OUTPUT);
  pinMode(switchPin, INPUT);
  Serial.begin(115200);
}

void loop() {
  switchStatus=digitalRead(switchPin);
  if(switchStatus)
  {
    ledStatus!=ledStatus;
  }
  digitalWrite(ledPin,ledStatus);
  delay(100);
}
```

