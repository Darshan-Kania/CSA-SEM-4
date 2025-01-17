# Lab 5

## Lab Assignments

1. Write an assembly language program in a 8085 microprocessor for the conversion of BCD to HEX or BCD to BINARY or DECIMAL to HEX or DECIMAL to BINARY.

   - Input: $25_{10}$
   - Output: $19H$

   **Ans:**

   ```asm
    ; Memory initialization
    LXI H, 3000H
    MVI A, 25H       ; Load the input number into the accumulator
    MOV M, A         ; Move the input number to the memory location

    ; Initialization
    LXI H, 3000H     ; Initialize the HL pair to point at the input address
    MOV A, M         ; Load BCD number from 3000H into accumulator
    MOV B, A         ; Copy BCD value to register B

    ; Extract and process the higher bit
    ANI 0F0H         ; Do and with F0 to get the higher bit
    RRC              ; Rotate accumulator 4 bits right
    RRC
    RRC
    RRC              ; Now, higher bit is shifted to lower bit position
    MOV C, A         ; Store higher bit in register C

    ; Multiply higher bit by 10 using repetitive addition
    MVI D, 0AH       ; Load register D with multipler as counter
    MVI A, 00H       ; Clear accumulator for result of multiplication

    MULTIPLY:
            ADD C            ; Add high bit repeatedly
            DCR D            ; Decrement multiplier counter
            JNZ MULTIPLY     ; Repeat until counter becomes 0

    MOV C, A         ; Store result (high bit × 10) in C

    ; Add the lower bit
    MOV A, B         ; Reload original BCD value
    ANI 0FH          ; Mask high bit to get low bit (A & 0FH)
    ADD C            ; Add intermediate result (high bit × 10)
                    ; Result is now complete in accumulator

    ; Store result
    LXI H, 3010H     ; Load HL with output address 3010H
    MOV M, A         ; Store the binary result in memory 3010H

    HLT              ; Halt the program
   ```

2. Write an assembly language program in a 8085 microprocessor for the conversion of HEX to BCD.

   - Input: $(2200H) - 34H$
   - Output: $(2210H) - 52H$

   **Ans:**

   ```asm
    MEMORY_INITIALIZATION:
            LXI H, 2200H    ; Point the HL pair to the memory location
            MVI A, 34H      ; Insert the input value in accumulator
            MOV M, A        ; Move the value to the memory

    INITIALIZATION:
            LXI H, 2200H    ; Point the HL pair to the memory location
            MOV A, M        ; Move the input value into accumulator
            MOV B, A        ; Store the value in register B for future reference
            MVI C, 00H      ; Clear the register C to store Quotient
            MVI D, 0AH      ; Set the

    DIVISION:
            CMP D           ; Compare accumulator with 10
            JC BCD_CALCULATION ; If value in accumulator is < 10 then do BCD calculation
            SUB D           ; Subtract 10 from accumulator
            INR C           ; Increment the Quotient
            JMP DIVIDE      ; Continue division

    BCD_CALCULATION:
            MOV E, A        ; Store the Remainder in E
            MOV A, C        ; Get the Quotient in accumulator
            RLC             ; Left shift 4 times
            RLC
            RLC
            RLC             ; To get the Quotient in 10s place
            MOV C, A        ; Store the value of accumulator in C

    MOV A, E                ; Take the Remainder in accumulator
    ADD C                   ; Add value of C in it

    STORE_ANSWER:
            LXI H, 2210H    ; Point the HL pair to memory location
            MOV M, A        ; Store value of accumulator in the memory

    HLT                     ; Stop the execution
   ```
