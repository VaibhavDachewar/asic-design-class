ASIC DESIGN CLASS LABS


***LAB 1a - Create a C program and compile it using GCC and then verify the output.***

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


***LAB 1b - Compiling a C code on  RISC_V compiler using O1 and Ofast.***

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

***LAB 2 - Compiling the C code with RISC-V compiler using spike simulator and debugging it.***

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


***LAB 3***

***LAB-3A] Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions***


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


***LAB-3B] By making use of RISCV Core: Verilog Netlist and Testbench, perform an experiment of Functional Simulation.***




From below we can see all instructions are Hardcoded. 



![9](https://github.com/user-attachments/assets/d8d022bc-67a7-4795-83d4-e19007f7a0fd)


To compile and to get gtkwave of the iiitb_rv32i.v file and it's testbench iiitb_rv32i_tb.v file use below commands : 


![10](https://github.com/user-attachments/assets/c2183c7e-c878-4267-a506-04cf026595a8)


Table to show standard risc-v isa and Hardcore isa for each operation :


| Operation          | Standard RISCV ISA | Hardcoded ISA |
|--------------------|---------------------|---------------|
| ADD R6, R2, R1     | 32'h00110333        | 32'h02208300  |
| SUB R7, R1, R2     | 32'h402083b3        | 32'h02209380  |
| AND R8, R1, R3     | 32'h0030f433        | 32'h0230a400  |
| OR R9, R2, R5      | 32'h005164b3        | 32'h02513480  |
| XOR R10, R1, R4    | 32'h0040c533        | 32'h0240c500  |
| SLT R1, R2, R4     | 32'h0045a0b3        | 32'h02415580  |
| ADDI R12, R4, 5    | 32'h004120b3        | 32'h00520600  |
| BEQ R0, R0, 15     | 32'h00000f63        | 32'h00f00002  |
| SW R3, R1, 2       | 32'h0030a123        | 32'h00209181  |
| LW R13, R1, 2      | 32'h0020a683        | 32'h00208681  |
| SRL R16, R14, R2   | 32'h0030a123        | 32'h00271803  |
| SLL R15, R1, R2    | 32'h002097b3        | 32'h00208783  |


Output waveforms for each instruction -

1] ADD R6, R2, R1  : here addition is performed as R2+R1 and stored in R1 

from below image we can see output of ADD : 00000001 + 00000002 = 00000003

![1](https://github.com/user-attachments/assets/0f3f8435-da39-4420-bb3a-8462f0d65b56)


Similarly all instructions are executed and their respective waveforms are recorded


2] SUB R7, R1, R2

![2](https://github.com/user-attachments/assets/0b45855b-bf87-43a2-ab9d-86fdcf211f98)

3] AND R8, R1, R3

![3](https://github.com/user-attachments/assets/ff7b5e6c-2a6b-47ff-a766-56dd5cba9d9f)

4] OR R9, R2, R5

![4](https://github.com/user-attachments/assets/d920063c-d861-449b-98c6-f3842716b6ef)

5] XOR R10, R1, R4

![5](https://github.com/user-attachments/assets/72648356-f4fe-45ba-9d04-1ee9f1106071)

6] SLT R1, R2, R4

![6](https://github.com/user-attachments/assets/e163b617-7689-4dba-8d8a-09c410385e6e)

7] ADDI R12, R4, 5

![7](https://github.com/user-attachments/assets/f8871143-418f-45fa-beb7-d2b9c554dcba)

8] BEQ R0, R0, 15

![8](https://github.com/user-attachments/assets/6bf61cab-2f26-4b64-98db-259339a51666)



***LAB-4] Create a "TO-DO LIST APPLICATION" in C and compile with gcc and Risc-V architecture compilers and verify the output.***


C program for "TO-DO-LIST APPLICATION":

```c
#include <stdio.h>
#include <string.h>

#define MAX_TASKS 100
#define TASK_LENGTH 100

typedef struct {
    char task[TASK_LENGTH];
    int is_done;
} Todo;

Todo todo_list[MAX_TASKS];
int task_count = 0;

void add_task() {
    if (task_count < MAX_TASKS) {
        printf("Enter the task: ");
        getchar(); // To consume the newline character from the previous input
        fgets(todo_list[task_count].task, TASK_LENGTH, stdin);
        todo_list[task_count].task[strcspn(todo_list[task_count].task, "\n")] = 0; // Remove newline character
        todo_list[task_count].is_done = 0;
        task_count++;
        printf("Task added successfully!\n");
    } else {
        printf("Task list is full!\n");
    }
}

void view_tasks() {
    if (task_count == 0) {
        printf("No tasks to display.\n");
        return;
    }
    for (int i = 0; i < task_count; i++) {
        printf("%d. [%c] %s\n", i + 1, todo_list[i].is_done ? 'x' : ' ', todo_list[i].task);
    }
}

void mark_task_done() {
    int task_num;
    printf("Enter the task number to mark as done: ");
    scanf("%d", &task_num);
    if (task_num > 0 && task_num <= task_count) {
        todo_list[task_num - 1].is_done = 1;
        printf("Task marked as done.\n");
    } else {
        printf("Invalid task number.\n");
    }
}

int main() {
    int choice;
    while (1) {
        printf("\nTo-Do List Application\n");
        printf("1. Add Task\n");
        printf("2. View Tasks\n");
        printf("3. Mark Task as Done\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                add_task();
                break;
            case 2:
                view_tasks();
                break;
            case 3:
                mark_task_done();
                break;
            case 4:
                printf("Exiting the application.\n");
                return 0;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }
}
```


Compilation with gcc -


![1](https://github.com/user-attachments/assets/bddcc84d-03eb-4979-b091-72a4ae171ec8)


Output can be observed as -

![2 (2)](https://github.com/user-attachments/assets/4ff6582c-3602-4a06-b800-7bb2dadb215f)

![Screenshot 2024-08-14 100416](https://github.com/user-attachments/assets/b295809e-e020-4021-b446-a1707f8dbd82)

![4](https://github.com/user-attachments/assets/f7f9cb89-f68d-41c8-9144-45238147aed3)


**Compiling the C code in RISC-V architecture with O1 and Ofast switches -**


A] Executing the C code with O1 switch with below command in terminal -


![5](https://github.com/user-attachments/assets/8893df1d-a763-4e3f-a4d3-c51457e29b1e)


The assembly line code for the O1 switch can be observed as below -


![6](https://github.com/user-attachments/assets/625df460-7a1d-457a-92c7-e77f62cf88c0)


B] Executing the C code with with Ofast switch -


![7](https://github.com/user-attachments/assets/a590b975-b548-49a4-bc79-8b4a32f33ce1)


The assembly line code, after executing the C code with Ofast switch can be observed as below-


![8](https://github.com/user-attachments/assets/a0731e9a-bec5-47bc-b43a-4fd44867a7d2)


For verifying for same result using risc-v architecture use spike simulator -

``spike pk todolist.o ``


![9](https://github.com/user-attachments/assets/71d46768-c6ca-4670-a9a1-b91ba738ebaf)


Now to open debugger use ``spike -d pk todolist.c`` command and to execute from 0 to first address of main section use ``until pc 0 103cc`` where 0 is the initial and 103cc is the first address under main section.


![10](https://github.com/user-attachments/assets/dc5e357e-3abc-4bee-96aa-9c9358a9bb84)



Observation - After compiling the "TO-DO-LIST APPLICATION" C program with gcc compiler and RISC-V architecture uising O1 and Ofast switches; same output is observed.


![11](https://github.com/user-attachments/assets/177f81b3-a8d2-4eee-ac07-9d6ebf148c1b)


