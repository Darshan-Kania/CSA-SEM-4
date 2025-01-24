# Lab7

> Aim :- DEMONSTRATE THE USE OF LOOPING, COMPARISON, AND BRANCHING INSTRUCTIONS IN 8085 ASSEMBLY LANGUAGE TO MANIPULATE DATA AND PERFORM MATHEMATICAL OPERATIONS.

## Lab Assignment

1. Write an 8085 assembly language program to find the largest number in an array of data.

```text
INPUT:
(2201H) = 08 (Array Size)
(2202H) = 45
(2203H) = 67
(2204H) = 15
(2205H) = 07
(2206H) = FE
(2207H) = 78
(2208H) = 21
(2209H) = 63
OUTPUT:
(220AH) = FE
```

> Code

```asm
MVI A,08H;
STA 2201H;
MVI A,45;
STA 2202H;
MVI A,67
STA 2203H;
MVI A,15;
STA 2204H;
MVI A,07H;
STA 2205H;
MVI A,FEH;
STA 2206H;
MVI A,78H;
STA 2207H;
MVI A,21H;
STA 2208H;
MVI A,63H;
STA 2209H;
LXI H,2200H;
MVI A,10H;
LXI B,2200H;
MOV D,A;
LOOP:
	INX B;
	CMP C;
	JZ END;
	MOV E,A;
	LDAX B;
	CMP D;
	JNC SWAP;
	MOV A,E;
	LOOP:

SWAP:

	MOV D,A
	JMP LOOP;
END:
	HLT;
HLT;
```

---

2. Write an 8085 assembly language program to find the smallest number in an array of data.

```text
INPUT: (Take the above data).
OUTPUT: (220AH) = 07
```

> Code

```asm
MVI A,08H;
STA 2201H;
MVI A,45;
STA 2202H;
MVI A,67
STA 2203H;
MVI A,15;
STA 2204H;
MVI A,07H;
STA 2205H;
MVI A,FEH;
STA 2206H;
MVI A,78H;
STA 2207H;
MVI A,21H;
STA 2208H;
MVI A,63H;
STA 2209H;
LXI H,2200H;
MVI A,10H;
LXI B,2200H;
MOV D,A;
LOOP:
	INX B;
	CMP C;
	JZ END;
	MOV E,A;
	LDAX B;
	CMP D;
	JC SWAP;
	MOV A,E;
	LOOP:

SWAP:

	MOV D,A
	JMP LOOP;
END:
	HLT;
HLT;
```

---

3. Write an 8085 assembly language program to sort the data in ascending order.

```text
Data(H): 63, 41, 56, 62, 48, 5A, 4F, 4C, 56, 56
```

> Code

```asm

START:	   MVI D,10	// Counter

W:	   LXI H,2201
	   MVI C,10	// Counter

X:	   MOV A,M
	   INX H
	   MOV B,M
	   CMP B
	   JC Y
	   MOV M,A
	   DCX H
	   MOV M,B
	   INX H

Y:	   DCR C
	   JNZ X
	   DCR D
	   JNZ W
	   HLT

# ORG 2201
# DB 63,41,56,62,48,5A,4F,4C,56,56

```
---
4. Write an 8085 assembly language program to sort an array containing the set of marks scored by 10 students in a Computer system course in descending order. 
```text
Data(H): Take the above data
```
> Code
```asm

START:	   MVI D,10	// Counter

W:	   LXI H,2201
	   MVI C,10	// Counter

X:	   MOV A,M
	   INX H
	   MOV B,M
	   CMP B
	   JNC Y
	   MOV M,A
	   DCX H
	   MOV M,B
	   INX H

Y:	   DCR C
	   JNZ X
	   DCR D
	   JNZ W
	   HLT

# ORG 2201
# DB 63,41,56,62,48,5A,4F,4C,56,56
```
---

5.  The following block of Data is stored starting from the memory location XX50H to XX5AH. Write an 8085 Assembly Language Program to transfer the data to a new location XX00H to XX05H in reverse order.

```text
DATA(H): 22,A5,B2,99,7F,37
```
> Code

```asm
MVI A,10H;
STA 1000H;
MVI A,20H
STA 1001H
MVI A,30H
STA 1002H
MVI A,40H
STA 1003H
MVI A,50H
STA 1004H
MVI H,5;

LXI B,1004H;
LXI D,2000H;
LOOP:
	LDAX B;
	STAX D;
	INX D
	DCX B
	DCR H;
	JZ END
	JMP LOOP;
END:
	HLT;
HLT;
```