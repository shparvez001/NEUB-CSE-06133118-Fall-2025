# NEUB CSE-06133118 Fall 2025 Lab 4

## Task 1
Introduction to logical instructions

```asm
.MODEL small
.STACK 100H
.DATA  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax        
    
    mov al, 01010101b
    mov bl, 10101010b
    
    mov cl, al
    and cl, bl      
    
    mov cl, al
    or cl, bl   
    
    mov cl, 01111101b
    xor cl, bl    
    
    mov cl, al
    not cl        
    
    mov cl, al
    test cl, bl  ;Same as logical AND operation. But the value of destination register doesnot change
    
    mov al, 00001111b
    and al, 11111100b   ;ANDing a bit with 0 resets/clears the bit
    or al, 11000000b    ;ORing a bit with 1 sets the bit
    XOR al, 10001001b   ;XORing a bit with 1 flips the bit
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 2
Use TEST instruction to check if the register AX has a value 0 or not and print the status. 

```asm
.MODEL small
.STACK 100H
.DATA       
str db 'AX contains 0$'   
str2 db 'AX does not contains 0$'
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax  
    
    mov ax, 0        
    ;test ax, 111111111111111b
    test ax 0ffffh   
    jz zero      
    jmp notzero

zero:   
    lea dx, str
    mov ah, 9
    int 21h
 
 notzero:     
    lea dx, str2
    mov ah, 9
    int 21h
    
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 3 [Odd Even Checker]
Use logical instructions to check if an input number is odd or even. Also print if the number is odd or even.

```asm
.MODEL small
.STACK 100H
.DATA       
odd db 'The number is odd', 0dh, 0ah,'$'   
even db 'The number is even', 0dh, 0ah,'$'  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax  
l1:
    mov ah, 1
    int 21h
    
    test al, 1   
    jz evenprint
    
    mov ah, 9
    lea dx, odd
    int 21h  
    jmp l1

evenprint:
    mov ah, 9
    lea dx, even
    int 21h 
    
    jmp l1                
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 4 [Case conversion]
Use only logical instruction to convert characters from uppercase to lowercase

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax  
l1:    
    mov ah, 1
    int 21h
    
    mov bl, al
    or bl, 00100000b    
    
    mov ah, 2
    mov dl, '-'
    int 21h
    mov dl, bl
    int 21h  
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h
    jmp l1

    
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 5 [Case conversion]
Use only logical instruction to convert characters from lowercase to uppercase

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax  
l1:    
    mov ah, 1
    int 21h
    
    mov bl, al
    and bl, 11011111b    
    
    mov ah, 2
    mov dl, '-'
    int 21h
    mov dl, bl
    int 21h  
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h
    jmp l1

    
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 6 [Case conversion]
Use logical instructions to do a case flip. If the input is uppercase convert to lowescase and if input is lowercase convert to uppercase.

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax  
l1:    
    mov ah, 1
    int 21h
    
    mov bl, al
    xor bl, 00100000b    
    
    mov ah, 2
    mov dl, '-'
    int 21h
    mov dl, bl
    int 21h  
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h
    jmp l1

    
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 7
Rotate and shift instructions

```asm
use of
    SHL
    SAL
    SHR
    SAR

    ROL
    RCL
    ROR
    RCR
```


## Task 8
Introduction to Stack

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ax, 1234h
    mov bx, 5678h
    push ax    
    push bx
    inc ax
    push ax
    inc bx
    push bx     
    
    pop cx
    pop cx
    pop cx
    pop cx       
    
    pushf ;used to store the value of flag register in stack
    popf ;used to retrive the fag register value             
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 9
Write a code to take an input string and print the string in reverse.

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ah, 2
    mov dl, '?'
    int 21h
    mov ah, 1
    mov cx, 0
 l1:    
    int 21h
    cmp al, 0dh
    je l2
    push ax
    inc cx
    jmp l1
    
l2:
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h
 
 l3:
    pop dx
    int 21h
    loop l3                 
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```


## Task 10
Introduction to procedure

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ax, 50
    mov bx, 30 
    call a         
    call b
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN  

a proc
    add ax, bx
    ret
endp a  

b proc
    sub ax, bx
    ret
endp b  

END MAIN
```


## Task 11
Write a code with a multiply procedure.

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ax, 5
    mov bx, 3 
    call multiply
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN  

multiply proc  ;Multiply the values of ax and bx and store it in dx
    push ax
    push bx   
    xor dx, dx ; resets dx
    
 l1:
    test bx, 1
    jz endif   
    add dx, ax  
endif:
    shl ax, 1
    shl bx, 1     
    jnz l1
    
    pop bx
    pop ax
    ret    
endp multiply    

END MAIN
```


## Task 12
Multiplication procedure by addition

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ax, 50
    mov bx, 30 
    call multiply
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN  

multiply proc  ;Multiply the values of ax and bx and store it in dx
    push ax
    push bx   
    push cx    
    mov cx, bx
    xor dx, dx
l1:
    add dx, ax
    loop l1    

    pop cx
    pop bx
    pop ax
    ret    
endp multiply    

END MAIN
```


## Task 13
Multiply and division instruction

```asm
.MODEL small
.STACK 100H
.DATA       
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax     
    
    mov ax, 8
    mov bx, 3  
    mul bx   ;mutiply bx with ax and store the result in ax
    mov bx,  3
    imul bx ;Signed multiplication

    mov ax, 2
    mov bx, 5
    div bx  ;unsigned division
    mov ax, 2
    idiv bx ;signed division
    
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN  
END MAIN
```



## Tasks to be done by students
1. Marut example 7.1-7.13
2. Marut Section 7.4: Binary and HEX input output [Total 4 codes]
3. Marut Chapter 7 Exercise 8
4. Marut Chapter 7 Exercise 9
5. Marut Chapter 7 Exercise 10
6. Marut Chapter 7 Exercise 11
7. Marut Chapter 7 Exercise 12
8. Marut Chapter 7 Exercise 13
9. Marut Chapter 7 Exercise 14