# NEUB CSE-06133118 Fall 2025 Lab 1

General Discussion on lab and finalizing tools to be used.

Part 1: Assembly Language
Part 2: Arduino (Work to be done by group of 2)

## Hardware needed for lab
* Breadboard
* Arduino UNO / ESP 32 (any model)
* Resistor (220, 1K, 10K)
* LED (Red, Green, Blue, White)
* Push button (https://www.techshopbd.com/detail?product_id=543)
* Light Dependent Resistor (LDR) (https://www.techshopbd.com/detail/162/LDR_5mm_techshop_bangladesh)
* Thermistor (10k -> https://www.techshopbd.com/detail/33/Thermistor_10K_techshop_bangladesh)
* Potentiometer (Variable Resistor Pot 10K (103) Flat Multi-turn - https://www.techshopbd.com/detail?product_id=970)
* DC Gear Motor with Wheel 2pcs with Caster
* Motor driver (https://www.techshopbd.com/detail/1635/L298N_Motor_Driver_(Red)_techshop_bangladesh)
* Servo motor (SG90)

## Grading Policy for Lab
|Item       |Mark   |
|-----------|-------|
|Attendance | 10    |
|Lab Performance | 20    |
|Lab Test | 40    |
|Project + Viva | 30    |


## Project
* Project group will be of at most 2 persons
* Project must not be any works done in lab
* Project must be completed in lab

#### Project Group Members (updated 27-07-2025)
|Group | Members|
|---------|--------|
|1||
|2||


## Task 1
Basic Structure of 8086 Assembly code.

```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC 
    ;MOV instruction is used to store value in a register
    MOV AL, 10 ; Decimal Value 10 is stored in AL
    MOV AL, 10h ; Hexadecimal Value 10 is stored in AL
    MOV AL, 00100001b  ; Binary value of 21 is stored in AL
    
    MOV BL, AL ;  Store the value of AL into BL
    
    
ENDP MAIN
END MAIN
```

## Task 2
Printing characters in 8086 Assembly code.

```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC     
    MOV AH, 2 ; For Outputting character  in  comMAINd window
    ;MOV DL, 41H
    MOV DL, 'A'
    INT 21h   
    
    ;Printing a NEw line
    MOV DL, 0AH    ;ASCI of New Line
    INT 21h
    MOV DL, 0DH    ; ASCII of Carriage Return
    INT 21h        
    
    MOV DL, 42h
    INT 21h   
    
    ;Printing a NEw line
    MOV DL, 0AH    ;ASCI of New Line
    INT 21h
    MOV DL, 0DH    ; ASCII of Carriage Return
    INT 21h   
    
    MOV DL, 43H
    INT 21h 
    
    MOV AH, 4CH
    INT 21h    
    
    
ENDP MAIN
END MAIN
```

## Task 3
Input and output of characters

```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC  
    MOV AH, 1   
    INT 21h  
    
    MOV BL, AL    
    
    MOV AH, 2
    MOV DL, 0Ah
    INT 21h
    MOV DL, 0Dh
    INT 21h
    
    MOV DL, BL
    INT 21H

    
    MOV AH, 4CH
    INT 21h    
    
    
ENDP MAIN
END MAIN
```


## Task 4
Printing a string (HELLO THERE) the hard way

```asm
.MODEL small
.STACK 100H
.DATA
.CODE
MAIN PROC    
     
    MOV AH, 2
    
    MOV DL, 'H'
    INT 21H   
    MOV DL, 'E'
    INT 21H  
    MOV DL, 'L'
    INT 21H   
    MOV DL, 'L'
    INT 21H   
    MOV DL, 'O'
    INT 21H     
    MOV DL, ' '
    INT 21H     
    MOV DL, 'T'
    INT 21H   
    MOV DL, 'H'
    INT 21H  
    MOV DL, 'E'
    INT 21H   
    MOV DL, 'R'
    INT 21H   
    MOV DL, 'E'
    INT 21H    


    
    MOV AH, 4CH
    INT 21h    
    
    
ENDP MAIN
END MAIN
```

## Task 5
Printing a string the easy way

```asm
.MODEL small
.STACK 100H
.DATA  
msg db 'HELLO THERE!$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9
    lea dx, msg 
    int 21h
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```
