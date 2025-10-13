# NEUB CSE Microprocessor and Interfacing Lab Fall 2025 Lab 9

## Task 1
LED blinking code in AVR.

Circuit:

![Lab 9 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-9/CSE-06133118-2502-lab9-task-1CKT_bb.png)

Code:
```c
int ledPin=13;
void setup() {
  // put your setup code here, to run once:
  pinMode(ledPin, OUTPUT);
  Serial.begin(115200);

}

void loop() {
  // put your main code here, to run repeatedly:
  digitalWrite(ledPin, HIGH);
  delay(1000);
  Serial.println("LED ON");
  digitalWrite(ledPin, LOW);
  delay(500);
  Serial.println("LED OFF");
}

```

## Task 2
Basic Input and output code for AVR.

Circuit:

![Lab 9 Task 2 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-9/CSE-06133118-2502-lab9-task-2CKT_bb.png)

Code:
```c
int ledPin=12;
int switchPin=4;
int switchStatus=0;
void setup() {
  // put your setup code here, to run once:
  pinMode(ledPin, OUTPUT);
  pinMode(switchPin,INPUT);
  Serial.begin(115200);

}

void loop() {
  switchStatus=digitalRead(switchPin);
  digitalWrite(ledPin,switchStatus);
  delay(100);
  // Naive way to read switch status and turn on/off led using if else statement
  // if(switchStatus==1){
  //   Serial.println("Switch On");
  //   digitalWrite(ledPin,HIGH);
  //   delay(1000);
  // }
  // else
  // {
  //   Serial.println("Switch Off");
  //   digitalWrite(ledPin, LOW);
  //   delay(1000);
  // }
  
}

```



## [Watch previous semester class video Here](https://www.youtube.com/watch?v=B4UmzWCzt7M)
