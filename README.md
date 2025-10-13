# NEUB-CSE-06133118-Fall-2025
NEUB CSE Microprocessor and Interfacing Lab Fall 2025
## List of Labs
1. [Lab 1](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-1.md).
	  1. Basic Structure of 8086 Assembly code and printing characters.
      2. Printing characters in 8086 Assembly code.
	  3. Input and output of characters
	  4. Printing a string (`HELLO THERE`) the hard way
	  5. Printing a string the easy way
2. [Lab 2](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-2.md).
	  1. Uppercase to lowercase
      2. Lowercase to uppercase
      3. Write a program to (a) prompt the user, (b) read first, middle, and last initials of a person's name, and (c) display them down the left margin.
      4. Take 6 characters as input and print them in new lines.
      5. Write a program to draw a 10*10 solid box of star.
      6. Write a program to draw a 10*10 hollow box of stars
      7. Write a count-controlled loop to display a row of 80 stars
      8. Write a program to draw a 10*10 solid box of star using loop.
      9. A basic `while (1)` loop
      10. Loop without use of `loop` instructions.
      11. Write a program to take a hexadecimal, A-F as input and print its equivalent decimal in the next line.
      12. Suppose AX and BX contain signed numbers. Write some code to put the biggest one in cx.
      13. Replace the number in AX by its absolute value.
      14. Write a program to (a) display "?", (b) read three initials,(c) display them in the middle of an 11 x 11 box of asterisks.
      15. Draw a 10*10 box of stars without using any string. Use only flow control instructions and loop to draw the box.
      16. Take 2 input numbers from 0-4 and print the sum of the numbers in new line.
3. [Lab 3](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-3.md).
	  1. Suppose AL and BL contain extended ASCII characters. Display the one that comes first in the character sequence.
	  2. If AX contains a negative number, put -1 In BX; if AX contains 0, put 0 In BX; if AX contains a positive number, put 1 In BX.
	  3. If AL contains 1 or 3, display "o"; if AL contains 2 or 4,display "e".
	  4. Take a number from 0-9 as input and print if it is odd or even.
	  5. Read a character, and if it's an uppercase letter, display it.
	  6. Read a character. If it's "y" or "Y", display it; otherwise, terminate the program.
	  7. Write some code to count the number of characters In an input line.
	  8. Write some code to read characters until a blank is read.
	  9. Write a program to display the extended ASCII characters (ASCII codes 80h to FFh). Display 10 characters per line, separated by blanks. Stop after the extended characters have been displayed once.
	  10. Write a program that will prompt the user to enter a hex digit character ("0"·... "9" or "A" ... "F"), display it on in decimal. If the user enters an illegal character, display 'i' to indicate invalid input and allow to enter new hex number.
	  11. Do task 10 but if three invalid input is given, terminate the program
	  12. Write a program to display a "?", read two capital letters, and display them on the next line in alphabetical order.
	  13. Write a code to take a string input and print the first and last capital letters in the string as appeared in the string
4. [Lab 4](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-4.md).
	1. Introduction to logical instructions
      2. Use TEST instruction to check if the register AX has a value 0 or not and print the status
      3. Use logical instructions to check if an input number is odd or even. Also print if the number is odd or even
      4. Use only logical instruction to convert characters from uppercase to lowercase
      5. Use only logical instruction to convert characters from lowercase to uppercase
      6. Use logical instructions to do a case flip. If the input is uppercase convert to lowescase and if input is lowercase convert to uppercase
      7. Rotate and shift instructions
      8. Introduction to Stack
      9. Write a code to take an input string and print the string in reverse
      10. Introduction to procedure
      11. Write a code with a multiply procedure.
      12. Multiplication procedure by addition
      13. Multiply and division instruction

5. [Lab 5](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-5.md).
	1. Decimal Input Procedure
      2. Decimal input output procedure 
      3. Write a procedure to find the factorial of a number stored in cx.
      4. Take 2 decimal numbers greater than 10 as inputs and print their sum,  difference, and product afterwards.
      5. Sum of 10 elements in array
      6. Sum of elements in array ending with $
      7. Array (Each element is 16 bit) Reverse Procedure
      8. Finding the average of different tests
6. [Lab 6](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-6.md).
	1. Basic XLAT usage
      2. Encoding and decoding message using XLAT
      3. Introduction to MOVSB instruction and REP prefix
      4. Write instructions to copy STRING 1 of the preceding task into STRING2 In reverse order.
      5. String read and print
      6. String reverse print using stosb and lodsb
      7. Use of SCASB instruction and REPNZ prefix.
      8. Counting vowels and consonants using scan string instruction
7. Lab 7: Midterm Lab exam
8. Lab 8: Introduction to hardware
9. [Lab 9](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-9.md).
	1. LED blinking code in AVR.
      2. Basic Input and output code for AVR.
10. [Lab 10](https://github.com/shparvez001/NEUB-CSE-06133118-Fall-2025/tree/main/lab-10.md).
	1. EEPROM read and write code.
      2. Using EEPROM to store a pattern of LED and pulsing through the pattern.
      3. Create a function to output PWM with a specified duty cycle to any given pin. eg: pwm(pinName, dutyCycle);.
      4. PWM using `analogWrite()` function.
      5. Use `analogWrite()` to create a fading LED effect.