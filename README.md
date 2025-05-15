# Assembly-Macro-Stack-Routines

This repository contains my work for Lab 2 of the "Introduction to Computers" course, focusing on stack operations and parameter passing in MSP430 assembly language.

## Repository Contents

### Code Files
- [Pre-lab Assignment (pre2.s43)](./code/pre2.s43): Implements a stack-based function to compute the XOR sum of two ID arrays.
- [Lab Task (task2.s43)](./code/task2.s43): Implements a function that computes modulo 4 for each element in ID arrays.

### Documentation
- [Pre-lab Report (pre_lab2.pdf)](./docs/lab2_pre_assignment.pdf): Initial preparation and analysis for the lab.
- [Preparation Report (Preparation report LAB2.pdf)](./docs/lab2_preparation_report.pdf): Detailed documentation of lab preparation.
- [Final Lab Report (final_lab2.pdf)](./docs/lab2_final_report.pdf): Complete analysis and results of the lab work.

## Code Explanation

### Pre-lab Assignment (pre2.s43)

This program demonstrates stack-based parameter passing and function implementation:

```assembly
Main     MOV   #SFE(CSTACK),SP  ; Initialize Stack Pointer
         
         ; Push function arguments onto the stack
         PUSH  #avivID          ; Address of first ID array
         PUSH  #asafID          ; Address of second ID array
         PUSH  #IDsize          ; Address of array size
         PUSH  #num             ; Address of result variable
         
         CALL  #Func            ; Call the XOR function
```

The function `Func` pops parameters from the stack, computes the XOR sum of elements from two ID arrays, and stores the result in the `num` variable.

### Lab Task (task2.s43)

This program demonstrates accessing parameters from the stack without popping them:

```assembly
Main     MOV #SFE(CSTACK),SP    ; Initialize Stack Pointer

         ; First function call
         PUSH #id1              ; Address of first ID array
         PUSH size              ; Array size value
         PUSH #mod4_ID1         ; Address of result array
         CALL #Func             ; Call modulo 4 function
         
         ; Second function call with different arrays
         PUSH #id2
         PUSH size
         PUSH #mod4_ID2
         CALL #Func
```

The function `Func` accesses parameters directly from the stack using offsets:
```assembly
Func     MOV 2(SP), R4      ; Result array address
         MOV 4(SP), R5      ; Array size
         MOV 6(SP), R6      ; Source array address
```

It then computes modulo 4 for each element in the source array and stores the results in the result array.

## Stack Operations in MSP430 Assembly

This lab focuses on important stack concepts:

- **Parameter Passing**: Using the stack to pass arguments to functions
- **Stack Frame Navigation**: Accessing parameters with stack pointer offsets
- **Return Address Management**: Saving and restoring the return address
- **Stack-Based Functions**: Implementing complete functions that use the stack

The MSP430 uses register R1 (SP) as the stack pointer. The stack grows downward in memory, and common stack operations include:
- `PUSH` - Push a value onto the stack
- `POP` - Pop a value from the stack
- `CALL` - Push return address and jump to subroutine
- `RET` - Pop return address and jump back

## Author

Created by Asaf Kamber and Aviv Primor

## Course Information

- Course: Introduction to Computers
- Lab: Stack Operations (Lab 2)

