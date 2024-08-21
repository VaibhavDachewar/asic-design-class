# ASIC DESIGN CLASS LABS

<details>
 <summary>LAB-1 </summary>

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

</details>



<details>
 <summary>LAB-2 </summary>

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

</details>





<details>
 <summary>LAB-3 </summary>
 
    
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


</details>


<details>
 <summary>LAB-4 </summary>

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


</details>


<details>
 <summary>LAB-5 </summary>

***LAB 5] Build a 5-stage pipelined RISC-V processor using TL verilog and Makerchip***


Enabeling the Visualisation for the pipelined cpu in makerchip - 


![1](https://github.com/user-attachments/assets/ff0ba0a6-c788-4495-bb6f-fb4676e52bd5)

![2](https://github.com/user-attachments/assets/68c0bf00-3dc1-4b26-b2ee-0659cc255a8e)


Appending the Fetch using PC Logic and Adding the instruction memory - 

![3](https://github.com/user-attachments/assets/eccfa195-6e20-4216-af66-a51439a5faab)

Decoding I,R,S,U,B,J type of instructions based on opcode [6:0]
Only [6:2] is used here because this implementation is for RV64I which does not use [1:0] - 


![4](https://github.com/user-attachments/assets/bd2e98f5-03bd-467f-92ba-442d8813a1ac)


Adding a unique name to the clock with ```$clk_vai = *clk``` - 


![5](https://github.com/user-attachments/assets/49fcd8cb-4339-4de9-afad-fbcf0e109f6a)


Instruction immediate value decode - 


![8](https://github.com/user-attachments/assets/d49f42ea-f2f1-45f2-8e84-ff24a2125e1b)


Decoding other fields of instruction (source and destination registers, funct, opcode) using valid -


![9](https://github.com/user-attachments/assets/4203ad52-f6a3-404d-a4f7-dafa5344d40f)


Decode instruction in subset of base instruction set based on RISC-V 32I 

Use the command to decode - ```$dec_bits[10:0] = {$funct7[5],$funct3,$opcode}```

Decoding individual branch instructions - 


![10](https://github.com/user-attachments/assets/3f665bc6-bfbe-4326-b3b2-9a052e274fc2)

To quite down warnings - ``` `BOGUS_USE($is_beq $is_bne $is_blt $is_bge $is_bltu $is_bgeu $is_addi $is_add)``` is added to the TLV code

**Register file Read and Write**

Here the Register file is 2 read, 1 write which means 2 read and 1 write operation can happen simultanously.

For changes on Register File Read assign ``$scr1/2_value[31:0]`` to register file outputs.


![11](https://github.com/user-attachments/assets/78fa9d26-3d74-4644-b52d-83434f3edee5)

**ALU**

During the execute stage at ALU, both the operands perform the operation based on opcode. The output of ALU can be observed at `Sresult` .

Below is snapshot from Makerchip IDE after performing the execute stage.

![12](https://github.com/user-attachments/assets/02237119-43f9-4d15-bad1-68a612577f76)

**Register File Write** can be performed as below and it's waveform can be observed -


![13](https://github.com/user-attachments/assets/9ae8ddca-a593-410a-8cd0-12692157a3dd)

**Implementing Branch Instructions**

The next stage in the building of the RISC-V microarchitecture, is the addition of branches.


![14](https://github.com/user-attachments/assets/0cafd8be-d2cb-4fdf-97ea-a6a0612d0294)


For complementing branch instructions use ``$br_target_pc[31:0] = $pc +$imm;`` 

![15](https://github.com/user-attachments/assets/0322dd3f-adc4-482a-b261-8a23c28a9b9e)

**Testbench**

To pass the testbench use - ``*passed = |cpu/xreg[10]>>5$value == (1+2+3+4+5+6+7+8+9+10);``

From the below snapshot from makerchip, we can observe that the Testbench is successfullt implemented, and we can verify it from the LOG terminal


![16](https://github.com/user-attachments/assets/c1ce8a67-3e74-4bbd-b348-db4d618dea14)


**Pipelining the RISC-V CPU**

After applying pipeling to the cpu core and including the load,store and data memory option, we can observe the pipelined output at the **visualization** terminal 

![17](https://github.com/user-attachments/assets/31a95dc6-4a69-4904-9602-4d0a3533b6f3)

On the viz tab we can observe execution of various insturents and their results on differnt registers

For the risc-v cpu code , it takes 59 cycles for execution after adding the load,store and jump instructions.


![18](https://github.com/user-attachments/assets/c87b2b4f-d2cb-4516-b943-42ae175e2df2)

Below is snapshot of pipelined CPU with a test case of assembly program which does summation from 1 to 9 then stores to r14 of register file. In snapshot r14 = 45.

![Screenshot 2024-08-21 225050](https://github.com/user-attachments/assets/14ef33c4-d231-4483-9590-50c15230ab0a)


![Screenshot 2024-08-21 225234](https://github.com/user-attachments/assets/b6c445e1-2491-4784-ad81-92badebe5d99)



The gradual output of add instruction at 56th cycle  stored in the r10 register can be observed as 


![Screenshot 2024-08-21 212517](https://github.com/user-attachments/assets/241221eb-6e2b-43b0-9c92-915e4f1e1bb8)


Hence in similar pattern output for other instructions can be analized.


***Block diagram of the designed RISC-V CPU***


![20](https://github.com/user-attachments/assets/08a9b81d-6e87-4acb-8614-3b586a65d3ee)


***Output waveform with clock signal appended with name ``clk_vai``***

![21](https://github.com/user-attachments/assets/2bb47755-9727-446f-91a1-88e105068d65)


**Reset signal**


![22](https://github.com/user-attachments/assets/776d7794-c8ea-4810-910f-a45190913b6a)


Gradual addition of 1 to 9 stored in r14 register


![Screenshot 2024-08-21 225234](https://github.com/user-attachments/assets/fd7c300d-8db5-4c34-8134-402a9493e71a)



***Code***

```
\m4_TLV_version 1d: tl-x.org
\SV
   // Template code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   m4_asm(SW, r0, r10, 10000)           // Store r10 result in dmem
   m4_asm(LW, r17, r0, 10000)           // Load contents of dmem to r17
   m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         
         //PC fetch - branch, jumps and loads introduce 2 cycle bubbles in this pipeline
         $pc[31:0] = >>1$reset ? '0 : (>>3$valid_taken_br ? >>3$br_tgt_pc :
                                       >>3$valid_load     ? >>3$inc_pc[31:0] :
                                       >>3$jal_valid      ? >>3$br_tgt_pc :
                                       >>3$jalr_valid     ? >>3$jalr_tgt_pc :
                                                     (>>1$inc_pc[31:0]));
         // Access instruction memory using PC
         $imem_rd_en = ~ $reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         
         
      @1
         //Getting instruction from IMem
         $instr[31:0] = $imem_rd_data[31:0];
         
         //Increment PC
         $inc_pc[31:0] = $pc[31:0] + 32'h4;
         
         //Decoding I,R,S,U,B,J type of instructions based on opcode [6:0]
         //Only [6:2] is used here because this implementation is for RV64I which does not use [1:0]
         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] == 5'b11001;
         
         $is_r_instr = $instr[6:2] == 5'b01011 ||
                       $instr[6:2] ==? 5'b011x0 ||
                       $instr[6:2] == 5'b10100;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
         
         $is_b_instr = $instr[6:2] == 5'b11000;
         
         $is_j_instr = $instr[6:2] == 5'b11011;
         
         //Immediate value decode
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}} , $instr[30:20]} :
                      $is_s_instr ? { {21{$instr[31]}} , $instr[30:25] , $instr[11:8] , $instr[7]} :
                      $is_b_instr ? { {20{$instr[31]}} , $instr[7] , $instr[30:25] , $instr[11:8] , 1'b0} :
                      $is_u_instr ? { $instr[31] , $instr[30:12] , { 12{1'b0}} } :
                      $is_j_instr ? { {12{$instr[31]}} , $instr[19:12] , $instr[20] , $instr[30:21] , 1'b0} :
                      >>1$imm[31:0];
         
         //Generate valid signals for each instruction fields
         $rs1_or_funct3_valid    = $is_r_instr || $is_i_instr || $is_s_instr || $is_b_instr;
         $rs2_valid              = $is_r_instr || $is_s_instr || $is_b_instr;
         $rd_valid               = $is_r_instr || $is_i_instr || $is_u_instr || $is_j_instr;
         $funct7_valid           = $is_r_instr;
         
         //Decode other fields of instruction - source and destination registers, funct, opcode
         ?$rs1_or_funct3_valid
            $rs1[4:0]    = $instr[19:15];
            $funct3[2:0] = $instr[14:12];
         
         ?$rs2_valid
            $rs2[4:0]    = $instr[24:20];
         
         ?$rd_valid
            $rd[4:0]     = $instr[11:7];
         
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
         
         $opcode[6:0] = $instr[6:0];
         
         //Decode instruction in subset of base instruction set based on RISC-V 32I
         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};
         
         //Branch instructions
         $is_beq   = $dec_bits ==? 11'bx_000_1100011;
         $is_bne   = $dec_bits ==? 11'bx_001_1100011;
         $is_blt   = $dec_bits ==? 11'bx_100_1100011;
         $is_bge   = $dec_bits ==? 11'bx_101_1100011;
         $is_bltu  = $dec_bits ==? 11'bx_110_1100011;
         $is_bgeu  = $dec_bits ==? 11'bx_111_1100011;
         
         //Jump instructions
         $is_auipc = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal   = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalr  = $dec_bits ==? 11'bx_000_1100111;
         
         //Arithmetic instructions
         $is_addi  = $dec_bits ==? 11'bx_000_0010011;
         $is_add   = $dec_bits ==  11'b0_000_0110011;
         $is_lui   = $dec_bits ==? 11'bx_xxx_0110111;
         $is_slti  = $dec_bits ==? 11'bx_010_0010011;
         $is_sltiu = $dec_bits ==? 11'bx_011_0010011;
         $is_xori  = $dec_bits ==? 11'bx_100_0010011;
         $is_ori   = $dec_bits ==? 11'bx_110_0010011;
         $is_andi  = $dec_bits ==? 11'bx_111_0010011;
         $is_slli  = $dec_bits ==? 11'b0_001_0010011;
         $is_srli  = $dec_bits ==? 11'b0_101_0010011;
         $is_srai  = $dec_bits ==? 11'b1_101_0010011;
         $is_sub   = $dec_bits ==? 11'b1_000_0110011;
         $is_sll   = $dec_bits ==? 11'b0_001_0110011;
         $is_slt   = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu  = $dec_bits ==? 11'b0_011_0110011;
         $is_xor   = $dec_bits ==? 11'b0_100_0110011;
         $is_srl   = $dec_bits ==? 11'b0_101_0110011;
         $is_sra   = $dec_bits ==? 11'b1_101_0110011;
         $is_or    = $dec_bits ==? 11'b0_110_0110011;
         $is_and   = $dec_bits ==? 11'b0_111_0110011;
         
         //Store instructions
         $is_sb    = $dec_bits ==? 11'bx_000_0100011;
         $is_sh    = $dec_bits ==? 11'bx_001_0100011;
         $is_sw    = $dec_bits ==? 11'bx_010_0100011;
         
         //Load instructions - support only 4 byte load
         $is_load  = $dec_bits ==? 11'bx_xxx_0000011;
         
         $is_jump = $is_jal || $is_jalr;
         
      @2
         //Get Source register values from reg file
         $rf_rd_en1 = $rs1_or_funct3_valid;
         $rf_rd_en2 = $rs2_valid;
         
         $rf_rd_index1[4:0] = $rs1[4:0];
         $rf_rd_index2[4:0] = $rs2[4:0];
         
         //Register file bypass logic - data forwarding from ALU to resolve RAW dependence
         $src1_value[31:0] = $rs1_bypass ? >>1$result[31:0] : $rf_rd_data1[31:0];
         $src2_value[31:0] = $rs2_bypass ? >>1$result[31:0] : $rf_rd_data2[31:0];
         
         //Branch target PC computation for branches and JAL
         $br_tgt_pc[31:0] = $imm[31:0] + $pc[31:0];
         
         //RAW dependence check for ALU data forwarding
         //If previous instruction was writing to reg file, and current instruction is reading from same register
         $rs1_bypass = >>1$rf_wr_en && (>>1$rd == $rs1);
         $rs2_bypass = >>1$rf_wr_en && (>>1$rd == $rs2);
         
      @3
         //ALU
         $result[31:0] = $is_addi  ? $src1_value +  $imm :
                         $is_add   ? $src1_value +  $src2_value :
                         $is_andi  ? $src1_value &  $imm :
                         $is_ori   ? $src1_value |  $imm :
                         $is_xori  ? $src1_value ^  $imm :
                         $is_slli  ? $src1_value << $imm[5:0]:
                         $is_srli  ? $src1_value >> $imm[5:0]:
                         $is_and   ? $src1_value &  $src2_value:
                         $is_or    ? $src1_value |  $src2_value:
                         $is_xor   ? $src1_value ^  $src2_value:
                         $is_sub   ? $src1_value -  $src2_value:
                         $is_sll   ? $src1_value << $src2_value:
                         $is_srl   ? $src1_value >> $src2_value:
                         $is_sltu  ? $sltu_rslt[31:0]:
                         $is_sltiu ? $sltiu_rslt[31:0]:
                         $is_lui   ? {$imm[31:12], 12'b0}:
                         $is_auipc ? $pc + $imm:
                         $is_jal   ? $pc + 4:
                         $is_jalr  ? $pc + 4:
                         $is_srai  ? ({ {32{$src1_value[31]}} , $src1_value} >> $imm[4:0]) :
                         $is_slt   ? (($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]}):
                         $is_slti  ? (($src1_value[31] == $imm[31]) ? $sltiu_rslt : {31'b0, $src1_value[31]}) :
                         $is_sra   ? ({ {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0]) :
                         $is_load  ? $src1_value +  $imm :
                         $is_s_instr ? $src1_value + $imm :
                                    32'bx;
         
         $sltu_rslt[31:0]  = $src1_value <  $src2_value;
         $sltiu_rslt[31:0] = $src1_value <  $imm;
         
         //Jump instruction target PC computation
         $jalr_tgt_pc[31:0] = $imm[31:0] + $src1_value[31:0]; 
         
         //Branch resolution
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ? ($src1_value != $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bge ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bltu ? ($src1_value < $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     1'b0;
         
         //Current instruction is valid if one of the previous 2 instructions were not (taken_branch or load or jump)
         $valid = ~(>>1$valid_taken_br || >>2$valid_taken_br || >>1$is_load || >>2$is_load || >>2$jump_valid || >>1$jump_valid);
         
         //Current instruction is valid & is a taken branch
         $valid_taken_br = $valid && $taken_br;
         
         //Current instruction is valid & is a load
         $valid_load = $valid && $is_load;
         
         //Current instruction is valid & is jump
         $jump_valid = $valid && $is_jump;
         $jal_valid  = $valid && $is_jal;
         $jalr_valid = $valid && $is_jalr;
         
         //Destination register update - ALU result or load result depending on instruction
         $rf_wr_en = (($rd != '0) && $rd_valid && $valid) || >>2$valid_load;
         $rf_wr_index[4:0] = $valid ? $rd[4:0] : >>2$rd[4:0];
         $rf_wr_data[31:0] = $valid ? $result[31:0] : >>2$ld_data[31:0];
         
      @4
         //Data memory access for load, store
         $dmem_addr[3:0]     =  $result[5:2];
         $dmem_wr_en         =  $valid && $is_s_instr;
         $dmem_wr_data[31:0] =  $src2_value[31:0];
         $dmem_rd_en         =  $valid_load;
         
      
         //Write back data read from load instruction to register
         $ld_data[31:0]      =  $dmem_rd_data[31:0];
         
      
      

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   //Checks if sum of numbers from 1 to 9 is obtained in reg[17] and runs 10 cycles extra after this is met
   *passed = |cpu/xreg[17]>>10$value == (1+2+3+4+5+6+7+8+9);
   //Run for 200 cycles without any checks
   //*passed = *cyc_cnt > 200;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)
   
   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic
                       // @4 would work for all labs
\SV
   endmodule
```

</details>






























































