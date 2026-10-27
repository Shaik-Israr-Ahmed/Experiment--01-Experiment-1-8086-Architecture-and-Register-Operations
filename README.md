# Experiment--01-Experiment-1-8086-Architecture-and-Register-Operations
 
## Aim

To study the architecture of the 8086 microprocessor and write assembly
language programs for register-to-register data transfer, memory
storage, and exchanging two 16-bit memory values.

## Learning Outcomes

After completing this experiment, students will be able to: - Explain
the main functional units of the 8086 microprocessor. - Describe the
roles of the Bus Interface Unit (BIU) and Execution Unit (EU). - Write
8086 assembly instructions for 16-bit data transfer. - Exchange data
between two memory locations using registers.

## Software Required

-   An 8086 assembly emulator, such as emu8086 or an equivalent
    8086-compatible emulator.
-   A text editor for writing the assembly programs.

------------------------------------------------------------------------

## Part (a): 8086 Architecture and Functional Units

### Question

Explain the architecture of the 8086 microprocessor with a neat block
diagram, describing the functions of the BIU and EU.

### Theory

The 8086 microprocessor is a 16-bit microprocessor developed by Intel. It has a 16-bit data bus and a 20-bit address bus, allowing it to access up to 1 MB of memory. The architecture of the 8086 microprocessor is divided into two main units: the Bus Interface Unit (BIU) and the Execution Unit (EU).

The Bus Interface Unit (BIU) is responsible for communication between the microprocessor and memory or input/output devices. It fetches instructions from memory, reads and writes data, generates the 20-bit physical address, and contains the segment registers CS, DS, SS and ES, along with the Instruction Pointer (IP). It also contains a 6-byte instruction queue to store prefetched instructions.

The Execution Unit (EU) is responsible for decoding and executing instructions. It performs arithmetic and logical operations using the Arithmetic Logic Unit (ALU). It contains general-purpose registers AX, BX, CX and DX, pointer and index registers SP, BP, SI and DI, and a flag register that stores the status of operations.

The BIU fetches instructions and stores them in the instruction queue, while the EU takes these instructions, decodes them and executes them. Both units can work in parallel, allowing the BIU to fetch the next instructions while the EU executes the current ones. This improves the overall processing speed and efficiency of the 8086 microprocessor.

### Simplified Block Diagram

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/2b6730ba-0659-4aad-a339-6f951ac92b72" />

### Working Principle

The 8086 microprocessor works using two main units: the Bus Interface Unit (BIU) and the Execution Unit (EU). The BIU fetches instructions from memory and stores them in a 6-byte instruction queue. It also generates the physical address and handles data transfer between the processor, memory and input/output devices.

The EU takes instructions from the queue, decodes them and executes them using the Arithmetic Logic Unit (ALU) and registers. The ALU performs arithmetic and logical operations, while the flag register stores the status of the results.

While the EU executes the current instructions, the BIU can fetch the next instructions simultaneously. This overlapping of instruction fetching and execution improves the speed and efficiency of the microprocessor. If a jump or branch instruction occurs, the instruction queue is updated with instructions from the new address.

------------------------------------------------------------------------

## Part (b): Transfer a 16-bit Value Between Registers and Store It in Memory

### Question

Write an 8086 assembly language program to transfer a 16-bit data value
from one register to another and store the result in memory.

### Algorithm

1. Start the program.
2. Initialize the data segment register (DS).
3. Load the 16-bit data value 1234H into register AX.
4. Transfer the contents of AX to register BX.
5. Store the contents of BX in the memory variable RESULT.
6. Terminate the program using INT 21H.
7. Stop.

### Assembly Program

.MODEL SMALL
.STACK 100H
.DATA
RESULT DW ?

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AX, 1234H
    MOV BX, AX
    MOV RESULT, BX

    MOV AH, 4CH
    INT 21H
MAIN ENDP
END MAIN

### Expected Result

AX = 1234H
BX = 1234H
RESULT = 1234H (stored in memory)

### Explanation

The program starts by initializing the data segment using MOV AX, @DATA and MOV DS, AX. The instruction MOV AX, 1234H loads the 16-bit hexadecimal value 1234H into register AX. Then, MOV BX, AX transfers the value from AX to BX, and MOV RESULT, BX stores the value of BX in the memory variable RESULT. Finally, MOV AH, 4CH and INT 21H terminate the program. Thus, the value 1234H is successfully transferred from AX to BX and stored in memory.
------------------------------------------------------------------------

## Part (c): Exchange Two 16-bit Memory Locations Using Registers

### Question

Write an 8086 assembly language program to exchange the contents of two
16-bit memory locations using registers.

### Algorithm

1. Start the program.
2. Initialize the data segment register (DS).
3. Load the contents of the first memory location NUM1 into register AX.
4. Load the contents of the second memory location NUM2 into register BX.
5. Transfer the contents of BX to NUM1.
6. Transfer the contents of AX to NUM2.
7. Terminate the program using INT 21H.
8. Stop.

### Assembly Program
.MODEL SMALL
.STACK 100H
.DATA
NUM1 DW 1234H
NUM2 DW 5678H

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV AX, NUM1
    MOV BX, NUM2

    MOV NUM1, BX
    MOV NUM2, AX

    MOV AH, 4CH
    INT 21H
MAIN ENDP
END MAIN
 

### Expected Result
Memory location	             Before swapping	            After swapping
NUM1	                             1234H	                     5678H
NUM2	                             5678H	                     1234H

### Explanation
The program starts by initializing the data segment using MOV AX, @DATA and MOV DS, AX. The instruction MOV AX, NUM1 loads the contents of the first memory location into register AX, and MOV BX, NUM2 loads the contents of the second memory location into register BX. Then, MOV NUM1, BX stores the value of BX in NUM1, and MOV NUM2, AX stores the value of AX in NUM2, thereby exchanging their contents. Finally, MOV AH, 4CH and INT 21H terminate the program. Thus, the contents of the two 16-bit memory locations are successfully exchanged using registers AX and BX.
  
------------------------------------------------------------------------

## Procedure

1.  Open an 8086-compatible assembler or emulator.
2.  Create a new assembly source file.
3.  Enter and assemble the program for the selected part.
4.  Correct any syntax or assembler-specific errors.
5.  Execute the program step by step or run it.
6.  Inspect the registers and memory variables.
7.  Record the observed results and compare them with the expected
    results.
## Screenshot of the results 



## Result

The 8086 architecture and the functions of the BIU and EU were studied.
The assembly programs demonstrate 16-bit register transfer with memory
storage and the exchange of two 16-bit memory values.


## Viva Voce Questions

1.  What is the function of the BIU in the 8086?
2.  What is the role of the EU?
3.  Why does the 8086 use a 6-byte instruction queue?
4.  What is the maximum physical memory address space of the 8086?
5.  What is the difference between a register and a memory variable?
6.  Does the `MOV` instruction change the source operand?
7.  Why are registers used when exchanging two memory values?
8.  What is the purpose of the DS segment register?

 
` 
