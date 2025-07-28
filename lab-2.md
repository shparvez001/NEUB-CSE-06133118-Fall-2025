# NEUB CSE-06133118 Fall 2025 Lab 2

## Task 1
Uppercase to lowercase

```asm
.MODEL small
.STACK 100H
.DATA  
msg db 'Enter a charater in uppercase: $'  
msg2 db 'In lowercase it is  $'  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9     
    lea dx, msg 
    int 21h
    
    mov ah, 1
    int 21h
    mov bl, al  
    add bl, 20h
                 
    mov ah, 9     
    lea dx, crlf
    int 21h
    lea dx, msg2
    int 21h
                    
    mov ah, 2
    mov dl, bl
    int 21h
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```

## Task 2
Lowercase to uppercase

```asm
.MODEL small
.STACK 100H
.DATA  
msg db 'Enter a charater in lowercase: $'  
msg2 db 'In Uppercase it is  $'  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9     
    lea dx, msg 
    int 21h
    
    mov ah, 1
    int 21h
    mov bl, al  
    sub bl, 20h
                 
    mov ah, 9     
    lea dx, crlf
    int 21h
    lea dx, msg2
    int 21h
                    
    mov ah, 2
    mov dl, bl
    int 21h
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN
```

## Task 3
Write a program to (a) prompt the user, (b) read first, middle, and last initials of a person's name, and (c) display them down the left margin.

Sample execution:
```
ENTER THREE INITIALS: SHP
S
H
P
```
```asm
.MODEL small
.STACK 100H
.DATA  
msg db 'Enter three initials: $'  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9     
    lea dx, msg 
    int 21h
    
    mov ah, 1
    int 21h    
    mov bl, al
    
    int 21h
    mov bh, al
    
    int 21h
    mov cl, al       
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, bl
    int 21h     
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, bh
    int 21h   
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, cl
    int 21h
    
   
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN        
```

## Task 4
Take 6 characters as input and print them in new lines.

```asm
.MODEL small
.STACK 100H
.DATA  
msg db 'Enter six characters: $'
a db ?,'$'                            
b db ?,'$'  
c db ?,'$'  
d db ?,'$'  
e db ?,'$'  
f db ?,'$'  
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9     
    lea dx, msg 
    int 21h
    
    mov ah, 1
    int 21h    
    mov a, al         
    int 21h
    mov b, al         
    int 21h
    mov c, al    
    int 21h
    mov d, al   
    int 21h
    mov e, al  
    int 21h
    mov f, al 
    
    mov ah, 2    
    
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, a
    int 21h     
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, b
    int 21h   
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, c
    int 21h       
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, d
    int 21h       
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, e
    int 21h      
    
    mov ah, 2
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h      
    mov dl, f
    int 21h
    
   
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN        
```

## Task 5
Write a program to draw a 10*10 solid box of star.

Sample Execution:
```
**********
**********
**********
**********
**********
**********
**********
**********
**********
**********
```
```asm
.MODEL small
.STACK 100H
.DATA  
msg db '**********',0dh,0ah,'$'
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov ah, 9
    lea dx, msg
    int 21h   
    int 21h   
    int 21h   
    int 21h   
    int 21h         
    int 21h   
    int 21h   
    int 21h   
    int 21h   
    int 21h             
   
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN     
```

## Task 6
Write a program to draw a 10*10 hollow box of stars

Sample Execution:
```
**********
*        *
*        *
*        *
*        *
*        *
*        *
*        *
*        *
**********
```
```asm
.MODEL small
.STACK 100H
.DATA   
msg db '**********', 0dh, 0ah, '$'   
msg2 db '*        *', 0dh, 0ah, '$'
crlf db 0dh, 0ah, '$'
.CODE
MAIN PROC
    mov ax, @data  
    mov ds, ax  

    mov ah, 9
    lea dx, msg      
    int 21h    
    lea dx, msg2           
    int 21h       
    int 21h       
    int 21h       
    int 21h       
    int 21h       
    int 21h       
    int 21h       
    int 21h   
    lea dx, msg       
    int 21h       


    MOV AH, 4CH
    INT 21H

ENDP MAIN
END MAIN   
```

## Task 7
Write a count-controlled loop to display a row of 80 stars

```asm
.MODEL small
.STACK 100H
.DATA  
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov cx, 80 
    mov ah, 2
    mov dl, '*'
    
label1:
    int 21h
    loop label1         
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 8
Write a program to draw a 10*10 solid box of star using loop.

```asm
.MODEL small
.STACK 100H
.DATA         
msg db '**********',0dh,0ah,'$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov cx, 10 
    mov ah, 9
    lea dx, msg
    
label1:
    int 21h
    loop label1         
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 9
A basic `while (1)` loop

```asm
.MODEL small
.STACK 100H
.DATA         
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
                       
label1:
    mov ah,1
    int 21h
    mov bl, al
    add bl, 20h
    mov ah,2
    mov dl, '-'
    int 21h
    mov dl, bl
    int 21h
    mov dl,0dh
    int 21h
    mov dl, 0ah
    int 21h
    jmp label1       
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 10
Loop without use of `loop` instructions.
```asm
.MODEL small
.STACK 100H
.DATA         
msg db '**********',0dh,0ah,'$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
    
    mov bl, 10     
    mov ah, 2
    mov dl, '*'
                       
label1:
    int 21h  
    sub bl, 1   ;dec bl will also work
    jnz label1       
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 11
Write a program to take a hexadecimal, A-F as input and print its equivalent decimal in the next line.

Sample Execution:
```
A-10
B-11
C-12
E-13
```
```asm
.MODEL small
.STACK 100H
.DATA         
msg db '**********',0dh,0ah,'$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
                       
label1:
    mov ah, 1
    int 21h  
    mov bl, al
    mov ah, 2
    mov dl, '-'
    int 21h
    mov dl, '1'
    int 21h
    mov dl, bl
    sub dl, 'A'
    add dl, '0'
    int 21h  
    mov dl, 0dh
    int 21h
    mov dl, 0ah
    int 21h
    jmp label1
    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 12 (Example 6.1) [If-else structure]
suppose AX and BX contain signed numbers. Write some code to put the biggest one in cx.

```asm
.MODEL small
.STACK 100H
.DATA         
msg db '**********',0dh,0ah,'$'
.CODE
MAIN PROC   
    mov ax, @data
    mov ds, ax
                       
    mov ax, 47h
    mov bx, 46h
    cmp ax, bx
    jge l1    
    jl l2
l1:
    mov cx, ax  
    jmp exit     
l2:
    mov cx, bx
exit:    
    MOV AH, 4CH
    INT 21h    
    
ENDP MAIN
END MAIN 
```

## Task 13(Example 6.2) [If-then structure]
Replace the number in AX by its absolute value.

```asm
.MODEL small
.STACK 100H
.DATA     
.CODE
MAIN PROC
    mov ax, @data  
    mov ds, ax

    mov ax, -10
    cmp ax, 0
    jg  l1   ; If positive do nothing

    ; else negate the number
    neg ax

l1:    
    mov bx, ax

exit:
    MOV AH, 4CH
    INT 21H

ENDP MAIN
END MAIN   
```

## Task 14
Write a program to (a) display "?", (b) read three initials,(c) display them in the middle of an 11 x 11 box of asterisks.

Sample Execution
```
?ABC
***********
***********
***********
***********
*****A*****
*****B*****
*****C*****
***********
***********
***********
***********
```
```asm
Solution to be done by students
```

## Task 15
Draw a 10*10 box of stars without using any string. Use only flow control instructions and loop to draw the box.

Sample Execution
```
**********
**********
**********
**********
**********
**********
**********
**********
**********
**********
```
```asm
Solution to be done by students
```

## Task 16
Take 2 input numbers from 0-4 and print the sum of the numbers in new line.

```asm
Solution to be done by students
```

## Tasks to be done by students
1. Task 14: Write a program to (a) display "?", (b) read three initials,(c) display them in the middle of an 11 x 11 box of asterisks.
2. Task 15: Draw a 10*10 box of stars without using any string. Use only flow control instructions and loop to draw the box.
3. Task 16: Take 2 input numbers from 0-4 and print the sum of the numbers in new line.