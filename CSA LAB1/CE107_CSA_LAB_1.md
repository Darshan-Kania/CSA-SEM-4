# Aim

To understand about 8085 Instructions sets - Data Transfer and Arithmetic Instructions.

# Practice Assignments

1. Analyze the different Data transfer instructions by checking the usage on the 8085 simulator.

    - MOV
    - MVI
    - LDA
    - STA

- Ans:

    1. MOV

        - Syntax: `MOV DESTINATION, SOURCE`
        - Working: Copy data from source address to destination address
        - Source and Destination addresses can be of registers or memory

    2. MVI

        - Syntax: `MVI DESTINATION, VALUE`
        - Working: Move imidiate data to a register or memory location

    3. LDA

        - Syntax: `LDA SOURCE`
        - Working: Load accumulator from the given 16 bit address

    4. STA

        - Syntax: `STA DESTINATION`
        - Working: Set the value of the given memory location with the value of the accumulator

---

1. Analyze the different Arithmetic instructions by checking the usage on the 8085 simulator.

    - ADD
    - ADC
    - ADI
    - ACI
    - SUB
    - SBB
    - SUI
    - SBI

- Ans:

    - **Note:** All these store the answer to the accumulator register

    1. ADD

        - Syntax: `ADD SOURCE`
        - Working: Simple addition

    2. ADC

        - Syntax: `ADC SOURCE`
        - Working: Addition with carry

    3. ADI

        - Syntax: `ADI SOURCE`
        - Working: Addition with imidiate value

    4. ACI

        - Syntax: `ACI SOURCE`
        - Working: Addition with imidiate value, carry edition

    5. SUB

        - Syntax: `SUB SOURCE`
        - Working: Simple subtraction

    6. SBB

        - Syntax: `SBB SOURCE`
        - Working: Subraction with borrow

    7. SUI

        - Syntax: `SUI SOURCE`
        - Working: Subtraction with immidiate value

    8. SBI

        - Syntax: `SBI SOURCE`
        - Working: Subtraction with immidiate value, borrow edition

# LAB ASSIGNMENT

### QUE-1

- Write an Assembly language program to perform addition of two 8 bit numbers.
  Constraint: The numbers should be such that the result is limited to 8 bits.

1. Both numbers are stored at Memory Locations.

```assembly
MVI B , 20H
MVI C , 00H
MVI H , 40H
MVI L , 00H
MVI M , 10
ADD M
MOV H , B
MOV L , C
MVI M , 10
ADC M
HLT
```

2. First number has to be present in Register and second number has to be present at memory location (2000H).

```assembly
MVI B , 10
MVI H , 20H
MVI L , 00H
MVI M , 10
ADD B
ADC M
HLT
```

---

### QUE-2

- Write an Assembly language program to perform the subtraction of two 8-bit numbers.

```assembly
MVI B , 20
MVI C , 10
ADD B
SUB C
HLT
```
---
> END OF DOCUMENT