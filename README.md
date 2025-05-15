# Assembly-Macro-Stack-Routines

This repository contains my work for Lab 2 of the "Introduction to Computers" course, focusing on macros, routines, stack operations, and project organization in MSP430 assembly language.

## Repository Contents

### Code Files
- [Pre-lab Assignment (pre2.s43)](./code/pre2.s43): Implements a stack-based function to compute the XOR sum of two ID arrays.
- [Lab Task (task2.s43)](./code/task2.s43): Implements a function that computes modulo 4 for each element in ID arrays.

### Documentation
- [Pre-lab Report (pre_lab2.pdf)](./docs/lab2_pre_assignment.pdf): Initial preparation and analysis for the lab.
- [Preparation Report (Preparation report LAB2.pdf)](./docs/lab2_preparation_report.pdf): Detailed documentation of lab preparation.
- [Final Lab Report (final_lab2.pdf)](./docs/lab2_final_report.pdf): Complete analysis and results of the lab work.

## Lab Focus Areas

This lab covers four key areas of assembly programming:

### 1. Macros
Although not explicitly implemented in the provided code, macros are reusable blocks of assembly code that get expanded inline during assembly. They improve code readability and maintainability by allowing complex operations to be defined once and used multiple times.

### 2. Routines (Functions)
Both code files implement functions that:
- Take parameters
- Process data
- Return results
- Can be called multiple times with different inputs

### 3. Stack Operations
The code demonstrates different stack usage patterns:
```assembly
; Stack parameter pushing in pre2.s43
PUSH  #avivID          ; Push address of first ID array
PUSH  #asafID          ; Push address of second ID array
PUSH  #IDsize          ; Push address of array size
PUSH  #num             ; Push address of result variable

; Stack parameter access in task2.s43
MOV 2(SP), R4      ; Access parameter directly from stack
MOV 4(SP), R5      ; without popping it
MOV 6(SP), R6
```

### 4. Project Organization
The lab demonstrates proper code organization techniques:
- Structured data and code sections
- Clear separation of functions
- Systematic parameter passing
- Consistent coding conventions

## Code Explanation

### Pre-lab Assignment (pre2.s43)

This program demonstrates stack-based parameter passing and function implementation. It computes the XOR sum of elements from two ID arrays and stores the result in a variable.

The function retrieves parameters by popping them from the stack:
```assembly
Func     POP   R4           ; Pop and save return address
         POP   R5           ; Pop address of result variable
         POP   R6           ; Pop address of array size
         POP   R7           ; Pop address of second ID array
         POP   R8           ; Pop address of first ID array
```

### Lab Task (task2.s43)

This program computes the modulo 4 of each element in an array and stores the results in another array. It demonstrates accessing parameters directly from the stack without popping them:

```assembly
Func     MOV 2(SP), R4      ; Result array address
         MOV 4(SP), R5      ; Array size
         MOV 6(SP), R6      ; Source array address
```

The function is called twice with different source and destination arrays, showing function reusability.

## Author

Created by Asaf Kamber and Aviv Primor

## Course Information

- Course: Introduction to Computers
- Lab: Macro, Routines, Stack and Project Organization (Lab 2)

