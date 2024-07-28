ASIC DESIGN CLASS LABS


LAB 1a - Create a C program and compile it using GCC and then verify the output.

Steps to be followed -

1] Open a text editor with a name sum1ton with use of the command mentioned below.
![1](https://github.com/user-attachments/assets/35037a36-036f-4039-a1c4-ba22a6dd7e1c)

2] Write a code to get sum of n numbers in the text editor.
![2](https://github.com/user-attachments/assets/5811c714-ff40-4b18-a8c6-b126d7fdd580)

3] Now compile the written code with help of gcc compiler
![3](https://github.com/user-attachments/assets/5759c133-0bb1-4248-96f5-0f89c930a49a)

4] Now run the executable code to check the final output
![4](https://github.com/user-attachments/assets/80d2507d-0549-4b86-9c9b-628f88a05c20)

Conclusion - Hence after succesfully executing c code we get sum of first 100 numbers as 5050.


LAB 1b - Compiling a C code on  RISC_V compiler using O1 and Ofast.

Steps to be followed -

1] Write a c program to get sum of n numbers
![Screenshot (740)](https://github.com/user-attachments/assets/3944499f-a22c-425f-bd20-75998bb96126)

2]Compile the c code using risc-v compiler with -O1 switch
![Screenshot (744)](https://github.com/user-attachments/assets/3c9961db-5692-4fa2-92f3-758fbd3c0c7a)

3] After creating an object file use the command to see the assembly code
![Screenshot (745)](https://github.com/user-attachments/assets/94aa641d-eb09-428a-8933-69975a713d0e)

4] As in the assembly code we just need to check inside the main so use | less.
![Screenshot (754)](https://github.com/user-attachments/assets/ba0bfb90-3e69-45d8-af8a-a6d1e353497f)

5] 15 lines of opcode are observed
![Screenshot (749)](https://github.com/user-attachments/assets/5e627bf6-fd02-4750-9f95-1191dda29b99)

6] Now use Ofast switch while compiling and repeat 3rd and 4th steps
![Screenshot (753)](https://github.com/user-attachments/assets/17ca7950-b63a-431d-ac5d-cf65c58455dd)

7] After generating the assembly code we obtain 12 lines of opcode.
![Screenshot (756)](https://github.com/user-attachments/assets/21362011-f28d-42a8-9955-641c2fd3ed27)

Conclusion - Hence the compilation is successfully performed.

LAB 2 - Compiling the C code with RISC-V compiler using spike simulator and debugging it.

Steps to be followed -

1] After compiling the sum1ton.c file using gcc compiler we got result as 5050. Now for verifying for same result using risc-v compiler use spike simulator and to get result use the command spike pk sum1ton.o 

![1](https://github.com/user-attachments/assets/c890e1e3-2060-4ab7-bfc8-bcac285c685d)

We get same result as 5050

2] Now to open debugger use "spike -d pk" command and to execute from 0 to first address of main section use "until pc 0 100b0 " where 0 is the initial and 100b0 is the first address under main section.

![2](https://github.com/user-attachments/assets/64e492dc-c68a-4898-bddc-7387e59d88ed)


3] TO check content of a2 register use "reg 0 a2" command. After executing it's content will be displayed. To go to the next instruction just press enter.

![3](https://github.com/user-attachments/assets/29fb83c7-4a7a-46c5-a2d9-fb5db9b953db)

4] As we can see the next instruction is "lui" which is used to load immediate. After executing it use "reg 0 a2" command and here we can observe that it's content is changed

![4](https://github.com/user-attachments/assets/7a7800da-a458-4ccc-a603-7a80c4c05d22)


5] Now moving to next instruction i.e "sp" stack pointer; after executing it we can observe hexadecimal 10 got subtracted i.e from 50 to 40.

![Screenshot (793)](https://github.com/user-attachments/assets/f7e12f2b-f0d5-4c51-85dc-419c7de18fb6)

Hence in similar way we can perform succeeding instructions.


LAB 3

LAB-3A] Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions


### Instructions Table

| Instruction          | Type | Opcode  | funct7 | rs2  | rs1  | funct3 | rd   | Imm   | 32-bit Instruction Code             |
|----------------------|------|---------|--------|------|------|--------|------|-------|-------------------------------------|
| `ADD r8, r9, r10`    | R    | 0110011 | 0000000| 01010| 01001| 000    | 01000|       | 0000000 01010 01001 000 01000 0110011 |
| `SUB r10, r8, r9`    | R    | 0110011 | 0100000| 01001| 01000| 000    | 01010|       | 0100000 01001 01000 000 01010 0110011 |
| `AND r9, r8, r10`    | R    | 0110011 | 0000000| 01010| 01000| 111    | 01001|       | 0000000 01010 01000 111 01001 0110011 |
| `OR r8, r9, r5`      | R    | 0110011 | 0000000| 00101| 01001| 110    | 01000|       | 0000000 00101 01001 110 01000 0110011 |
| `XOR r8, r8, r4`     | R    | 0110011 | 0000000| 00100| 01000| 100    | 01000|       | 0000000 00100 01000 100 01000 0110011 |
| `SLT r0, r1, r4`     | R    | 0110011 | 0000000| 00100| 00001| 010    | 00000|       | 0000000 00100 00001 010 00000 0110011 |
| `ADDI r2, r2, 5`     | I    | 0010011 |        |      | 00010| 000    | 00010| 000000000101 | 000000000101 00010 000 00010 0010011 |
| `SW r2, r0, 4`       | S    | 0100011 |        | 00010| 00000| 010    |      | 0000000 0100  | 0000000 00100 00000 010 00010 0100011 |
| `SRL r6, r1, r1`     | R    | 0110011 | 0000000| 00001| 00001| 101    | 00110|       | 0000000 00001 00001 101 00110 0110011 |
| `BNE r0, r0, 20`     | B    | 1100011 |        | 00000| 00000| 001    |      | 0000000 10100 | 0000000 10100 00000 001 00000 1100011 |
| `BEQ r0, r0, 15`     | B    | 1100011 |        | 00000| 00000| 000    |      | 0000000 01111 | 0000000 01111 00000 000 00000 1100011 |
| `LW r3, r1, 2`       | I    | 0000011 |        |      | 00001| 010    | 00011| 000000000010 | 000000000010 00001 010 00011 0000011 |
| `SLL r5, r1, r1`     | R    | 0110011 | 0000000| 00001| 00001| 001    | 00101|       | 0000000 00001 00001 001 00101 0110011 |

RISC-V instructions and their corresponding hexadecimal representations:

|Instruction       |Hexadecimal|
|-------------------|-------------------|
|ADD r8, r9, r10    | 0x00A4A033|
|SUB r10, r8, r9    | 0x40A4A533|
|AND r9, r8, r10    | 0x00A4A233|
|OR r8, r9, r5      | 0x0054A033|
|XOR r8, r8, r4     | 0x0044A033|
|SLT r00, r1, r4    | 0x00408033|
|ADDI r02, r2, 5    | 0x00510113|
|SW r2, r0, 4       | 0x00412023|
|SRL r06, r01, r1   | 0x00129233|
|BNE r0, r0, 20     | 0x01400063|
|BEQ r0, r0, 15     | 0x00F00063|
|LW r03, r01, 2     | 0x00212083|
|SLL r05, r01, r1   | 0x00129133|
