# Experiment--02-Experiment-1-8086-Architecture-and-Register-Operations
 
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

8086 Microprocessor

The Intel 8086 is a 16-bit microprocessor developed by Intel. It has a 16-bit data bus and a 20-bit address bus, which allows it to access up to 1 MB of memory.

The 8086 microprocessor is divided into two major functional units:
1. Bus Interface Unit (BIU)
2. Execution Unit (EU)
3. BUS INTERFACE UNIT (BIU)
The BIU is responsible for communication between the microprocessor and memory or input/output devices.

Functions of BIU:
1. Generates the 20-bit physical address.
2. Fetches instructions from memory.
3. Reads data from memory and writes data into memory.
4. Communicates with input/output devices.
5. Contains segment registers CS, DS, SS and ES.
6. Contains the Instruction Pointer (IP).
7. Has a 6-byte instruction prefetch queue.
4. EXECUTION UNIT (EU)
The EU is responsible for decoding and executing instructions fetched by the BIU.

Functions of EU:
1. Decodes the instructions received from the BIU.
2. Executes arithmetic and logical operations.
3. Contains the Arithmetic Logic Unit (ALU).
4. Contains general-purpose registers AX, BX, CX and DX.
5. Contains pointer and index registers SP, BP, SI and DI.
6. Contains the Flag Register to store status and control flags.
7. Requests the BIU for memory and I/O operations.

### Simplified Block Diagram

<img width="2048" height="1536" alt="image" src="https://github.com/user-attachments/assets/2ec6a809-4f91-41a6-ae5d-37f225c06785" />

### Working Principle

1. The BIU fetches instructions from memory.
2. The fetched instructions are stored in the 6-byte instruction queue.
3. The EU takes instructions from the queue.
4. The EU decodes and executes the instructions.
5. If memory or I/O access is required, the EU requests the BIU.
6. The BIU performs the required data transfer.
This process allows instruction fetching and execution to overlap, improving the performance of the microprocessor. This technique is called pipelining.

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

MOV AX, 1234H
MOV BX, AX
MOV [0000H], BX
HLT

### Expected Result

AX = 1234H
BX = 1234H
RESULT = 1234H (stored in memory)

### Explanation

1. MOV AX, 1234H – Loads the 16-bit hexadecimal value 1234H into the AX register.

2. MOV BX, AX – Copies the contents of AX into the BX register.

3. MOV [0000H], BX – Stores the 16-bit value from BX into the memory location DS:0000H.

4. HLT – Stops the execution of the program.

Result: The value 1234H is successfully transferred from AX to BX and stored in memory.
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

; Initialize two memory locations

MOV AX, 1111H
MOV [0000H], AX

MOV AX, 2222H
MOV [0002H], AX

; Exchange the values

MOV AX, [0000H]
MOV BX, [0002H]

MOV [0000H], BX
MOV [0002H], AX

HLT

 

### Expected Result
Memory location	             Before swapping	            After swapping
NUM1	                             1234H	                     5678H
NUM2	                             5678H	                     1234H

### Explanation
1. MOV AX, 1111H – Loads the first 16-bit value into AX.
2. MOV [0000H], AX – Stores the value in the first memory location.
3. MOV AX, 2222H – Loads the second 16-bit value into AX.
4. MOV [0002H], AX – Stores the value in the second memory location.
5. MOV AX, [0000H] – Loads the first memory value into AX.
6. MOV BX, [0002H] – Loads the second memory value into BX.
7. MOV [0000H], BX – Stores the second value in the first memory location.
8. MOV [0002H], AX – Stores the first value in the second memory location.
9. HLT – Stops program execution.
  
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

part (b)
<img width="1920" height="1080" alt="Screenshot 2026-11-17 182012" src="https://github.com/user-attachments/assets/cf8b76ad-b55c-41e8-989c-57687c6f0e3e" />

part (c)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/44ad2568-354b-4a00-9a1b-0e0d6083eabd" />



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
