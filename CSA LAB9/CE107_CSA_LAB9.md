# Lab9

> Aim :- Sessional Programs

## Q1

- Assembly code to perform binary to gray conversion.

```assembly
MVI A,ABH;
MOV B,A;
STC;
CMC;
RAR;
XRA B;
STA 8050H;
HLT;
```

---

## Q2

- Count no of set and reset bits in a byte.

```assembly
MVI A,10111001B;
MVI B,0H
LOOP:
	INR B;
	MOV C,A;
	MOV A,B;
	CPI 9H
	JZ END;
	MOV A,C;
	RLC;
	JC COUNTSET;
	JNC COUNTUNSET;
	JMP LOOP;
COUNTSET:
	INR E;
	JMP LOOP;
COUNTUNSET:
	INR D;
	JMP LOOP;
END:
MOV A,E;
STA 3001H;
MOV A,D;
STA 3002H;
HLT;
```

---

## Q3

- Swap Content of 2 Memory Location using minimum number of registers.

```assembly
LXI H,3412;
SHLD 2050H;
LXI H,2050H;
MOV A,M;
INX H;
MOV C,A;
MOV A,M;
STA 2050;
MOV A,C;
STA 2051;
HLT;
```

---

## Q4

- Palindrome Checker

```assembly
    MVI A,11111111B;
    MOV B,A
    MVI C, 08H
    MVI D, 00H

REVERSE_LOOP:
    RAR
    RLC
    MOV A,D
    MOV D,A
    MOV A,B
    DCR C
    JNZ REVERSE_LOOP

    CMP B
    JZ PALINDROME
MVI A,3
    HLT

PALINDROME:
MVI A,2
    HLT

```
