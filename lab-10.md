# NEUB CSE-06133118 Microprocessor and Interfacing Lab Fall 2025 Lab 10

## Task 1
EEPROM read and write code.

Circuit:
In either of the following circuits, you can use 4 or 8 LEDs. The circuit is the same, just the number of LEDs and the pins used are different. Use Resistance value of 220 ohm for each LED.
To use with 4 LEDs, use the following circuit:
![Lab 10 Task 1 Circuit in breadboard with 4 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-1-2-variant1CKT_bb.png)

To use with 8 LEDs, use the following circuit:
![Lab 10 Task 1 Circuit in breadboard with 8 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-1-2-variant2CKT_bb.png)

Code:
```c
const int ledPins[8]={A0,A1,A2,A3,A4,A5,2,3};

void setup() {
  Serial.begin(115200);
  for(int i=0;i<8;i++)
  {
    pinMode(ledPins[i],OUTPUT);
  }

  for(int i=0;i<15;i++)
  {
    EEPROM.write(i,i*i);
  }

  for(int i=0;i<15;i++)
  {
    byte value=EEPROM.read(i);
    displayByteOnLED(value);
    Serial.println(value);
    delay(1000);
  }

}

void loop() {
  // Nothing
  Serial.println("Entered VOID LOOP");
  delay(10000);

}

void displayByteOnLED(byte value)
{
  for (int i=0;i<8;i++)
  {
    digitalWrite(ledPins[i],value>>i&1);
  }
}
```

## Task 2
Using EEPROM to store a pattern of LED and pulsing through the pattern.

Circuit:
In either of the following circuits, you can use 4 or 8 LEDs. The circuit is the same, just the number of LEDs and the pins used are different. Use Resistance value of 220 ohm for each LED.
To use with 4 LEDs, use the following circuit:
![Lab 10 Task 2 Circuit in breadboard with 4 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-1-2-variant1CKT_bb.png)

To use with 8 LEDs, use the following circuit:
![Lab 10 Task 2 Circuit in breadboard with 8 LEDs](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-1-2-variant2CKT_bb.png)

Code:
```c
#include<EEPROM.h>
const int ledPins[8]={A0,A1,A2,A3,A4,A5,2,3};
byte ledStates[8]={0,1,2,4,8,12,14,15};
//0000 =>0
//0001 =>1
//0010 =>2
//0100=>4
//1000=>8
//1100=>12
//1110=>14
//1111=>15

void setup() {
  Serial.begin(115200);
  for(int i=0;i<8;i++)
  {
    pinMode(ledPins[i],OUTPUT);
  }

  for(int i=0;i<8;i++)
  {
    EEPROM.write(i,ledStates[i]);
  }
}

void loop() {
  for(int i=0;i<15;i++)
  {
    byte value=EEPROM.read(i);
    displayByteOnLED(value);
    Serial.println(value);
    delay(1000);
  }
}

void displayByteOnLED(byte value)
{
  for (int i=0;i<8;i++)
  {
    digitalWrite(ledPins[i],value>>i&1);
  }
}
```

## Task 3
Create a function to output PWM with a specified duty cycle to any given pin. eg: pwm(pinName, dutyCycle);.

Circuit:
![Lab 10 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-3CKT_bb.png)

Code:
```c
int pwmPin=7;
void setup() {
  Serial.begin(115200);
  pinMode(pwmPin, OUTPUT)
}

void loop() {
  pwm(pwmPin, 20);
}

void pwm(int pin, int duty)
{
  int t_on=5;
  float x= (t_on*100/duty)-t_on;
  int t_off=(int)x;
  digitalWrite(pin, HIGH);
  delay(t_on);
  digitalWrite(pin, LOW);
  delay(t_off);
}
```

## Task 4
PWM using analogWrite() function.
This task is to use the `analogWrite()` function to output PWM signals. The `analogWrite()` function takes two parameters: the pin number and the duty cycle (0-255).

Circuit:
![Lab 10 Task 4 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-4-5CKT_bb.png)

Code:
```c
int pwmPin=6;

void setup() {
  pinMode(pwmPin,OUTPUT);
}

void loop() {
  analogWrite(pwmPin,127);
  delay(1000);
  analogWrite(pwmPin,255);
  delay(1000);  
  analogWrite(pwmPin,0);
  delay(1000);

}  
```

## Task 5
Use `analogWrite()` to create a fading LED effect.
This task is to use the `analogWrite()` along with `map()` function to output PWM signals by providing duty cycle as percentage. 

Circuit:
![Lab 10 Task 5 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-06133118-Fall-2025/main/lab-10/CSE-06133118-2502-lab10-task-4-5CKT_bb.png)

Code:
```c
int pwmPin=6;

void setup() {
  pinMode(pwmPin,OUTPUT);
}

void loop() {
  for(int i=0;i<11;i++)
  {
    analogWrite(pwmPin,map(i*10,0,100,0,255));
    delay(1000);
  }
}
```



## [Watch previous semester class video Here](https://www.youtube.com/watch?v=FBq0LM6HCyM)
