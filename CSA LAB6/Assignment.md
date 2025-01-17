```assembly
	   MVI A,41	;Load 02H into A (the number to check)
	   MVI H,05	; Load 05H into H (upper bound)
	   MVI L,01	; Load 00H into L (lower bound)
CHECKZERO:
	CPI 0H;
	JNZ CHECKNUMBER
	ADI 30H;
	STA 2000
	HLT;
CHECKNUMBER:
	   CMP L	; Compare A with the lower bound(L)
	   JC NOTINNUMBER	; Jump if A < L
	   CMP H	; Compare A with the upper bound (H)
	   JNC NOTINNUMBER	;Jump if A >= H
	   ADI 30	; Add 30H to A (for ASCII conversion, if needed)
	   STA 2000	; Store the result in memory location 2000H
	   HLT	; Halt the program

NOTINNUMBER:
	SUI 0AH;
	ADI 41H
	STA 2000
   HLT	; Halt the program (out of range case)
```
