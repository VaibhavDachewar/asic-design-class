# ASIC DESIGN CLASS LABS

<details>
 <summary> TASK-1 </summary>

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
 <summary>TASK-2 </summary>

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
 <summary>TASK-3 </summary>
 
    
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
 <summary>TASK-4 </summary>

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
 <summary>TASK-5 </summary>

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
         $clk_vai = *clk;
         
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


<details>
 <summary>TASK-6 </summary>
 

***LAB 6 - Comparision of generated RISC-V processor outputs using Iverilog GTKwave and Makerchip***

***Steps to be followed -***

1] Execute the below commands on the terminal window for the buildup to converting the tlv file to the required verilog files

```
 sudo apt install make python python3 python3-pip git iverilog gtkwave

 cd ~

 sudo apt-get install python3-venv

 python3 -m venv .venv

 source ~/.venv/bin/activate

 pip3 install pyyaml click sandpiper-saas
```

![Screenshot 2024-08-26 222633](https://github.com/user-attachments/assets/499c08ad-0b72-4828-8c8d-c19852704878)



2] Use of Sandpiper to convert the TL-Verilog file to Verilog file 

![2](https://github.com/user-attachments/assets/ac001acc-9292-4ed9-a0ab-57849a8e6fdc)

3] Now to compile and simulate the generated verilog code for RISC-V design  run the following commands.

```
 iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module

 cd output

 ./pre_synth_sim.out
```

![4](https://github.com/user-attachments/assets/b21e1941-e23b-4d90-ae72-b461de361323)

4] Now to open the .vcd simulation file through GTKWave use below command 

```
$ gtkwave pre_synth_sim.vcd
```

![5](https://github.com/user-attachments/assets/0dcb0f6d-b653-4390-9cac-7e6b25352067)



5] The generated output waveform is as shown below which includes -
   (i) Clock signal appended with name - CPU_clk_vai_a0.
   (ii) reset signal.
   (iii) 10-bit output showing gradual addition of 1 to 9.


  
![6](https://github.com/user-attachments/assets/ec109a35-ba92-4299-9bb9-3344982e2fdc)


  

  6] For comparison we can see the below plot of gradual addition of 1 to 9 which was obtained in the makerchip using TL-verilog code.

![Screenshot 2024-08-26 233637](https://github.com/user-attachments/assets/a5d68ad0-8ede-4044-8c37-c64e82bda863)
  

</details>
   


<details>
 <summary>TASK-7 </summary>

***LAB 7 - Addition of Peripherals to convert the Digital output to analog output using DAC and PLL.***

PLL (Phase-Locked Loop): A PLL is used to generate stable clock signals from a reference clock. It can also be used to adjust the frequency of the system clock to meet the requirements of the DAC or other peripherals.

DAC (Digital-to-Analog Converter): A DAC converts digital signals into an analog voltage. It requires a clock signal to control the conversion rate. 

***Commands used to run the rvmyth.v file -***

``
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
``


![Screenshot from 2024-09-02 10-40-01](https://github.com/user-attachments/assets/5ee6b9a6-e543-4e23-9996-791e627784aa)


After this we dump the ./pre_synth_sim.out file to create the .vcd file using the following command

``
./pre_synth_sim.out
``

![Screenshot from 2024-09-02 10-40-24](https://github.com/user-attachments/assets/05c2f587-bdfb-4c8c-bdd3-31ac2a83bb5a)


We then run this .vcd file on gtkwave to observe the output

``
gtkwave pre_synth_sim.vcd
``


![Screenshot from 2024-09-02 10-40-37](https://github.com/user-attachments/assets/19031eba-11ba-4907-be3b-1b0591893f0a)


Below is the output for the waveforms:


![Screenshot from 2024-09-02 10-38-26](https://github.com/user-attachments/assets/91df9dab-9ea2-4bb7-9f02-fc3b49160ca1)



![Screenshot from 2024-09-03 19-26-11](https://github.com/user-attachments/assets/35a36548-89b8-42aa-9453-1a80c85d2f6f)



![Screenshot from 2024-09-03 19-24-10](https://github.com/user-attachments/assets/79dfc06c-352a-4ea6-b647-da7c317e4ecc)



![Screenshot from 2024-09-03 19-23-45](https://github.com/user-attachments/assets/11f5160f-8667-49f0-9457-fce42345237b)


</details>


<details>
 <summary>TASK-8 </summary>

***TASK-8 - RTL design using Verilog with SKY130 Technology .***

<details>
 <summary>Day-1</summary>


**Lab-1**

To setup the installation clone the github repo ```https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git```

![Screenshot from 2024-10-17 22-35-08](https://github.com/user-attachments/assets/802db657-3b57-41cc-bd84-66fff31d022e)




**Lab-2 : Iverilog and GTKWave**

After cloning the github repo we can list the below verilog files along with respective testbench files under verilog_files directory

![Screenshot from 2024-10-17 22-35-15](https://github.com/user-attachments/assets/f09953ee-2a1b-489a-a006-bfc781e1e33b)

![Screenshot from 2024-10-17 22-35-18](https://github.com/user-attachments/assets/47699719-2ae6-4b79-9f5a-b43aa85e073e)

Simulation of ```good_mux.v``` using iverilog and observing waveform using GTKwave

![Screenshot from 2024-10-17 22-41-49](https://github.com/user-attachments/assets/718a4218-7902-40dd-8834-c1deaf34a9fe)

![Screenshot from 2024-10-17 22-42-07](https://github.com/user-attachments/assets/e82b2ab7-eef1-4cc6-94a6-036297def25a)


![Screenshot from 2024-10-17 23-34-16](https://github.com/user-attachments/assets/a9295397-b90b-45bf-bc01-9046389ca0fd)


**Lab- 3 : YOSYS**

YOSYS is basically a synthesizer which is used to convert RTL to netlist.


After invoking the yosys on terminal we can see the yosys command prompt as-

![Screenshot from 2024-10-19 16-53-50](https://github.com/user-attachments/assets/0e404e32-8d10-4491-99b4-5b135bf7b8af)


Now to read the library use the command ``read_liberty -lib`` and to read the good_mux.v verilog file use the command ``read_verilog good_mux.v``

![Screenshot from 2024-10-19 17-32-48](https://github.com/user-attachments/assets/d9ebc649-c4a3-449b-af5d-52d6896db7e0)

In the library file name - ``sky130_fd_sc_hd__tt_025C_1v80.lib``  "tt" indicates typical process, "025c" indicates temperature and "1v80" indicates voltage.   
After reading the verilog file we need to perform synthesis on the good_mux.v verilog file.
To do so use the command  - ``synth -top good_mux``

After executing SYNTH on good_mux we can observe the following as result-


![Screenshot from 2024-10-19 17-39-01](https://github.com/user-attachments/assets/c731ed33-fb8b-47d1-8642-9f504e44e0cd)

![Screenshot from 2024-10-19 17-39-15](https://github.com/user-attachments/assets/fe726e57-3813-4a22-a897-bf7c42e99117)

![Screenshot from 2024-10-19 17-39-24](https://github.com/user-attachments/assets/93f9389d-e475-4f72-a09b-7102ddd83c8f)


![Screenshot from 2024-10-19 17-39-39](https://github.com/user-attachments/assets/111ba700-42fb-42d3-b2a1-5992303ddb04)


![Screenshot from 2024-10-19 17-39-52](https://github.com/user-attachments/assets/59cbabbe-e4a7-4e6c-a7fd-5e5f385445f5)

![Screenshot from 2024-10-19 17-40-01](https://github.com/user-attachments/assets/ee1b1616-3482-44e4-a323-5ff3b5e3fb16)

![Screenshot from 2024-10-19 17-40-11](https://github.com/user-attachments/assets/96855d13-7e4e-4201-bed0-c81de414eb3d)

![Screenshot from 2024-10-19 17-40-22](https://github.com/user-attachments/assets/e6d651da-64d3-447a-aef3-c02b20d183e6)

![Screenshot from 2024-10-19 17-40-34](https://github.com/user-attachments/assets/3484e05b-b958-402f-ab06-9514397f9693)

![Screenshot from 2024-10-19 17-40-43](https://github.com/user-attachments/assets/d71d8939-5a73-4f74-8896-af71144d95c1)

![Screenshot from 2024-10-19 17-40-52](https://github.com/user-attachments/assets/78bd7ee8-0213-46bb-8348-ca01ba017953)

![Screenshot from 2024-10-19 17-41-12](https://github.com/user-attachments/assets/cfcf42de-5799-4460-8858-f3fc423da1ca)


Hence we have successfully read the liberty file (.lib) and the verilog file(.v)

Now to generate the netlist us the command ``abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib``

Output on terminal can be observed as -

![Screenshot from 2024-10-19 18-13-34](https://github.com/user-attachments/assets/6591881b-5987-4f8e-bcda-91dced9f53e7)

![Screenshot from 2024-10-19 18-13-48](https://github.com/user-attachments/assets/b936c8ea-30fb-4338-a80f-302cea059322)

After analyzing the ABC results we can observe that it has identified 0 internal signal, 3 input signals and 1 output signal.

The following result can be compared from the verilog file of good_mux

![Screenshot from 2024-10-19 18-20-08](https://github.com/user-attachments/assets/e457caef-00c3-45b0-bb93-7aa5372fba6c)
![Screenshot from 2024-10-19 18-13-48](https://github.com/user-attachments/assets/b936c8ea-30fb-4338-a80f-302cea059322)

To see the logic initialised by the synthesizer use ``show`` command 


![Screenshot from 2024-10-19 18-24-29](https://github.com/user-attachments/assets/2478ffe0-952c-4025-bb30-cd7cc196745f)

![Screenshot from 2024-10-19 18-23-14](https://github.com/user-attachments/assets/6f9aa7db-c067-48d7-84a3-991a7b3fa5c4)


After seeing the logic used, we need to write the netlist and to write the netlist use the command ``write_verilog good_mux_netlist.v
`` 

![Screenshot from 2024-10-19 18-35-21](https://github.com/user-attachments/assets/e4d201ad-0f81-4072-abd7-dba911332225)

We can see the generated netlist verilog file as below 


![Screenshot from 2024-10-19 18-33-24](https://github.com/user-attachments/assets/f568de9c-dfe8-4216-93e3-cd4aa7ba051e)


![Screenshot from 2024-10-19 18-35-21](https://github.com/user-attachments/assets/9cf5ca2d-f158-4aee-aa96-6a99e2c039b6)

```
As we can see alot of information, but our requirement is a simplified netlist.
To simplify the netlist we need to modify the switch

Generated netlist -

/* Generated by Yosys 0.46+34 (git sha1 9432e972f, g++ 12.3.0-1ubuntu1~23.04 -fPIC -O3) */

(* top =  1  *)
(* src = "good_mux.v:2.1-10.10" *)
module good_mux(i0, i1, sel, y);
  (* src = "good_mux.v:2.24-2.26" *)
  wire _0_;
  (* src = "good_mux.v:2.35-2.37" *)
  wire _1_;
  (* src = "good_mux.v:2.46-2.49" *)
  wire _2_;
  (* src = "good_mux.v:2.63-2.64" *)
  wire _3_;
  (* src = "good_mux.v:2.24-2.26" *)
  input i0;
  wire i0;
  (* src = "good_mux.v:2.35-2.37" *)
  input i1;
  wire i1;
  (* src = "good_mux.v:2.46-2.49" *)
  input sel;
  wire sel;
  (* src = "good_mux.v:2.63-2.64" *)
  output y;
  wire y;
  sky130_fd_sc_hd__mux2_1 _4_ (
    .A0(_0_),
    .A1(_1_),
    .S(_2_),
    .X(_3_)
  );
  assign _0_ = i0;
  assign _1_ = i1;
  assign _2_ = sel;
  assign y = _3_;
endmodule
```

</details>

<details>
 <summary>Day-2 </summary>

**Lab-4:Hierarchiel vs Flat synthesizer**

In this task we we have to use the YOSYS synthesizer to generate netlist for the ``multiple_modules.v`` verilog file.


RTl is multiple_module.v :

```
module sub_module2 (input a, input b, output y);
	assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
	assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
	wire net1;
	sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
	sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
```

To perform the task we need to execute the listed commands step by step -

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog multiple_modules.v
4. synth -top multiple_modules
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
7. write_verilog -noattr multiple_modules_netlist.v
8. gvim multiple_modules_netlist.v
```

After executing each command we can see the terminal output as -

![Screenshot from 2024-10-19 20-10-01](https://github.com/user-attachments/assets/652a77bb-fe56-414b-8592-a8be95396233)


![Screenshot from 2024-10-19 20-11-39](https://github.com/user-attachments/assets/df627b4e-c895-4e36-b40b-6b28a8b2d33e)

![Screenshot from 2024-10-19 20-11-54](https://github.com/user-attachments/assets/3ec0319a-57c7-4db1-b66b-149f9680707d)


![Screenshot from 2024-10-19 20-12-11](https://github.com/user-attachments/assets/42a6996f-afba-400d-9ee4-346b96b3c8e5)


![Screenshot from 2024-10-19 20-13-35](https://github.com/user-attachments/assets/b07a5c33-cfb0-447e-9d32-49d2d9f21b6e)

![Screenshot from 2024-10-19 20-14-25](https://github.com/user-attachments/assets/1667c88d-a11c-44c6-9fa7-420012c55ffd)

After analyzing the ABC results we can observe that it has identified 0 internal signal, 3 input signals and 1 output signal.

Generated netlist circuit -

![Screenshot from 2024-10-19 20-17-51](https://github.com/user-attachments/assets/3d62a196-1347-47fc-bc7b-50899d0af18a)

The resultant netlist:

```
/* Generated by Yosys 0.46+34 (git sha1 9432e972f, g++ 12.3.0-1ubuntu1~23.04 -fPIC -O3) */

module multiple_modules(a, b, c, y);
  input a;
  wire a;
  input b;
  wire b;
  input c;
  wire c;
  wire net1;
  output y;
  wire y;
  sub_module1 u1 (
    .a(a),
    .b(b),
    .y(net1)
  );
  sub_module2 u2 (
    .a(net1),
    .b(c),
    .y(y)
  );
endmodule

module sub_module1(a, b, y);
  wire _0_;
  wire _1_;
  wire _2_;
  input a;
  wire a;
  input b;
  wire b;
  output y;
  wire y;
  sky130_fd_sc_hd__and2_0 _3_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  assign _1_ = b;
  assign _0_ = a;
  assign y = _2_;
endmodule

module sub_module2(a, b, y);
  wire _0_;
  wire _1_;
  wire _2_;
  input a;
  wire a;
  input b;
  wire b;
  output y;
  wire y;
  sky130_fd_sc_hd__or2_0 _3_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  assign _1_ = b;
  assign _0_ = a;
  assign y = _2_;
endmodule
```

***Flat Netlist***

The flat netlist is being generated to flatten out or avoid all the hierarchies generated in the Hierarchical netlist.

Use of ``flaten`` to write a flat netlist.

![Screenshot from 2024-10-19 20-33-23](https://github.com/user-attachments/assets/08e27578-5ea4-4673-8212-34f8b60a029a)

Generated flat netlist :

```
/* Generated by Yosys 0.46+34 (git sha1 9432e972f, g++ 12.3.0-1ubuntu1~23.04 -fPIC -O3) */

module multiple_modules(a, b, c, y);
  wire _0_;
  wire _1_;
  wire _2_;
  wire _3_;
  wire _4_;
  wire _5_;
  input a;
  wire a;
  input b;
  wire b;
  input c;
  wire c;
  wire net1;
  wire \u1.a ;
  wire \u1.b ;
  wire \u1.y ;
  wire \u2.a ;
  wire \u2.b ;
  wire \u2.y ;
  output y;
  wire y;
  sky130_fd_sc_hd__and2_0 _6_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  sky130_fd_sc_hd__or2_0 _7_ (
    .A(_4_),
    .B(_3_),
    .X(_5_)
  );
  assign _4_ = \u2.b ;
  assign _3_ = \u2.a ;
  assign \u2.y  = _5_;
  assign \u2.a  = net1;
  assign \u2.b  = c;
  assign y = \u2.y ;
  assign _1_ = \u1.b ;
  assign _0_ = \u1.a ;
  assign \u1.y  = _2_;
  assign \u1.a  = a;
  assign \u1.b  = b;
  assign net1 = \u1.y ;
endmodule
```

By comparing the flat netlist with that of Hierarchical netlist we can observe that all the sub_modules has ben flatten out in the flat netlist.
We can observe direct instatntiation of AND and OR gates.


![Screenshot from 2024-10-20 10-47-16](https://github.com/user-attachments/assets/1df8f8f0-476f-4e7c-bc1d-eca60f760b35)


Generated flatten netlist circuit - 

![Screenshot from 2024-10-20 11-04-33](https://github.com/user-attachments/assets/9cb86c42-7178-4cfe-a317-02fccb24fc1f)


***Sub-module level synthesis***

Synthesizing the sub_module1 i.e. u1 of the multiple_modules.v :

To synthesize the sub_module1 i.e. u1 use the below commands :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog multiple_modules.v
4. synth -top sub_module1
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
```

The terminal output can be observed as -

![Screenshot from 2024-10-20 11-16-08](https://github.com/user-attachments/assets/de3693c9-d615-4f4e-b175-8d0cc7299e92)

![Screenshot from 2024-10-20 11-16-57](https://github.com/user-attachments/assets/16b5f471-35f9-4287-b66e-e7ec1b29d470)

![Screenshot from 2024-10-20 11-17-11](https://github.com/user-attachments/assets/d8a377f2-eca1-4a9e-b63b-81f044a2902c)

We can observe only sub_module1 stats are obtained:

![Screenshot from 2024-10-20 11-17-20](https://github.com/user-attachments/assets/ba2cff1d-36df-442c-9217-907b473781f1)


![Screenshot from 2024-10-20 11-17-45](https://github.com/user-attachments/assets/a8212d91-1ebe-4da2-b6e6-57c69f56bc30)



![Screenshot from 2024-10-20 11-18-06](https://github.com/user-attachments/assets/033ced51-38fc-4080-b55e-dc4f81f01b14)



***LAB-5:Various flop coding styles and optimization:***

Simulating the D-FF verilog file with iverilog and observing the output waveform on gtkwave-

Note: All the required verilog files to perform simulation of d-ff are available in the verilog_files directory. 

1] Use of ``Asynchronous_reset:``

Commands to simulate d-ff file :

```
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd
```

Terminal output -

![Screenshot from 2024-10-20 11-50-05](https://github.com/user-attachments/assets/a01d5c55-858e-4adc-95d7-c25c1248b0e0)

GTK-waveform:

![Screenshot from 2024-10-20 11-50-33](https://github.com/user-attachments/assets/9a924ec5-4e5e-4e5d-95a6-91f07d972ab6)

Observation : As soon as asynchronous_reset goes high (1), the output "q" for d-ff goes low(0) independent of posedge or negedge of clock.

2] Use of ``Asynchronous_set:``

Commands to simulate d-ff file with asynchronous_set :

```
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
gtkwave tb_dff_async_set.vcd
```

Terminal output - 

![Screenshot from 2024-10-20 11-59-41](https://github.com/user-attachments/assets/0497ae9a-0778-434e-8d53-96430cab1362)

GTK-waveform:

![Screenshot from 2024-10-20 12-00-13](https://github.com/user-attachments/assets/224dbdb0-3abf-4543-82af-a1de43b3d0d7)


Observation : As long as asynchronous_set goes high (1), the output "q" for d-ff goes high(1) independent of posedge or negedge of clock and irrespective of input "d".


2] Use of ``Ssynchronous_reset:``

Commands to simulate d-ff file with synchronous_reset :

```
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
gtkwave tb_dff_syncres.vcd
```

Terminal output - 

![Screenshot from 2024-10-20 12-16-01](https://github.com/user-attachments/assets/ab1d8859-fd17-4370-ada1-45f2df49edb2)

GTK-waveform:

![Screenshot from 2024-10-20 12-16-17](https://github.com/user-attachments/assets/0d993748-7807-4227-863c-9197fd98c740)


Observation : Unlike for asynchronous_reset where output "q" goes low when asynchronous_reset goes high irrespective of clock;
              here for synchronous_reset, the output "q" doesn't immediately goes low as soon as synchronous_reset goes high instead it waits for the next posedge of clock 	      to rest the output value to low(0).


**Synthesis of D-FF verilog files( Asynchronous Reset, Asynchronous Set and Synchronous Reset. ) with use of YOSYS synthesizer**

1] Asynchronous reset:

Commands to perform synthesis on D-FF with asynchronous reset:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_asyncres.v
4. synth -top dff_asyncres
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_asyncres_netlist.v
9. !gvim dff_asyncres_netlist.v
```

Generated netlist:

![Screenshot from 2024-10-20 12-50-32](https://github.com/user-attachments/assets/bf143441-f049-4617-895b-bb5507e77f31)


Terminal output -

![Screenshot from 2024-10-20 12-48-33](https://github.com/user-attachments/assets/af9efe4f-5197-4340-b1b1-52cef2ee42b5)


  ![Screenshot from 2024-10-20 12-48-57](https://github.com/user-attachments/assets/9ebd51c6-d035-4178-bf25-0df39455ed9c)
  
   ![Screenshot from 2024-10-20 12-49-20](https://github.com/user-attachments/assets/5fbfcd13-df9e-473b-bfdd-f61ad8f84e65)


![Screenshot from 2024-10-20 12-49-35](https://github.com/user-attachments/assets/458f1965-b36f-4a19-a696-0e28254b2751)

Generated netlist circuit:


![Screenshot from 2024-10-20 12-50-46](https://github.com/user-attachments/assets/e6cfc96a-f0dd-4edc-8f1a-c0d0a035c7b9)


2] Asynchronous set:

Commands to perform synthesis on D-FF with asynchronous set:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_async_set.v
4. synth -top dff_async_set
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_async_set_netlist.v
9. !gvim dff_async_set_netlist.v

```

Generated netlist :
![Screenshot from 2024-10-20 13-03-34](https://github.com/user-attachments/assets/259e922b-63ba-4d20-ba53-02d34a93731e)


generated circuit for netlist:


![Screenshot from 2024-10-20 13-03-22](https://github.com/user-attachments/assets/3e058835-e10b-47f8-b62b-b329773e6980)


Terminal output:

![Screenshot from 2024-10-20 13-02-39](https://github.com/user-attachments/assets/2d35553d-f76d-43e8-8f06-426a7fda93e8)


![Screenshot from 2024-10-20 13-02-51](https://github.com/user-attachments/assets/44b5789e-de66-477a-aba7-ceb72c766f95)


![Screenshot from 2024-10-20 13-03-04](https://github.com/user-attachments/assets/98df7e29-5dfe-458c-adcd-9eb37a70afd2)



3] Synchronous reset:

Commands to perform synthesis on D-FF with synchronous reset:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_syncres.v
4. synth -top dff_syncres
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
8. write_verilog -noattr dff_syncres_netlist.v
9. !gvim dff_syncres_netlist.v
```

Generated netlist:

![Screenshot from 2024-10-20 13-14-44](https://github.com/user-attachments/assets/971c74e4-bb47-4008-94d2-12141489bd42)

Gcircuit for netlist:

![Screenshot from 2024-10-20 13-14-29](https://github.com/user-attachments/assets/f0fb98be-b473-40da-bc44-fef2a72c8105)

Terminal output:

![Screenshot from 2024-10-20 13-13-39](https://github.com/user-attachments/assets/e2f700e4-7671-4579-9921-4ed27094ef68)


![Screenshot from 2024-10-20 13-14-00](https://github.com/user-attachments/assets/424c6bd7-f235-4c5e-b6cd-5475191a140e)


![Screenshot from 2024-10-20 13-14-22](https://github.com/user-attachments/assets/8853e6ff-b056-4b75-bd94-57e25b2ef041)



***LAB-6: Interesting optimizations on mult_2.v and mult_9.v files ***


Note: The verilog files used are present in the verilog_files directory of sky130-workshop.


Commands to synthesize mult_2.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog mult_2.v
4. synth -top mul2
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
7. write_verilog -noattr mul2_net.v
8. !gvim mul2_net.v
```

Generated netlist:

![Screenshot from 2024-10-20 13-35-35](https://github.com/user-attachments/assets/dff299f4-d8c1-43d9-bae4-3d432b8c0cb5)


Generated netlist circuit:


![Screenshot from 2024-10-20 13-35-47](https://github.com/user-attachments/assets/b86bf676-0232-44e9-92f6-50b4a454f9af)


Terminal output:

![Screenshot from 2024-10-20 13-27-12](https://github.com/user-attachments/assets/c5484509-94f1-422e-9687-920731fc0c3f)


![Screenshot from 2024-10-20 13-27-42](https://github.com/user-attachments/assets/e9d4bdc4-16dc-45a3-b7f2-551ab4b6ace3)

![Screenshot from 2024-10-20 13-35-26](https://github.com/user-attachments/assets/902dc828-72a5-424d-a502-ea7be24086e9)


Observation : Their are 0 memories, 0 memory bits, 0 processes and 0 cells.
              As a is directly appended with 0, therefore no use of hardware here.




Commands to synthesize mult_8.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog mult_8.v
4. synth -top mult8
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. show
7. write_verilog -noattr mult8_net.v
8. gvim mult8_net.v
```

Generated netlist:

![Screenshot from 2024-10-20 13-44-27](https://github.com/user-attachments/assets/c83d49a3-d9dc-4e81-8d89-f76210adc155)


Generated netlist circuit :

![Screenshot from 2024-10-20 13-44-40](https://github.com/user-attachments/assets/2bc3eea6-4d24-4f5b-82f8-46ee116b835e)

Terminal output:

![Screenshot from 2024-10-20 13-43-40](https://github.com/user-attachments/assets/80764351-4b4b-4022-9ed7-7ac00c3a65ab)

![Screenshot from 2024-10-20 13-43-58](https://github.com/user-attachments/assets/cd0050c5-ae92-431c-80b6-e2c0b45c17f9)

![Screenshot from 2024-10-20 13-44-14](https://github.com/user-attachments/assets/73c5d78b-3dd3-4704-ab1a-90bc209a4270)

Observation : Their are 0 memories, 0 memory bits, 0 processes and 0 cells.

</details>


<details>
 <summary> Day-3 </summary>


 ***Combinational and Sequential optimization***

 **LAB-7: Combinational Logic optimization**

**1] Optimizing opt_check.v verilog file:**

Commands to perform optimization-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check.v
4. synth -top opt_check
5. opt_clean -purge
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Note - Command to do the optimization is ``opt_clean -purge``

Optimized 2-input AND gate circuit :


![Screenshot from 2024-10-20 16-01-11](https://github.com/user-attachments/assets/745c5a1d-517d-4a52-aa0c-bd8085bf4f4b)


Terminal output:

![Screenshot from 2024-10-20 15-59-45](https://github.com/user-attachments/assets/29a275d1-2f6c-46f6-b37d-64705f9746c0)


![Screenshot from 2024-10-20 16-00-11](https://github.com/user-attachments/assets/d36f3a87-f499-42ca-8762-381d5cbe8580)

![Screenshot from 2024-10-20 16-00-21](https://github.com/user-attachments/assets/ed70da98-d6e4-4512-949d-72fcff2f5339)

![Screenshot from 2024-10-20 16-00-48](https://github.com/user-attachments/assets/4c4c5162-1b0a-46bb-a778-d5602b240742)


Observation: Unused or redundant logic in the design and purges any dangling wires or gates are been Removed.


**2] Optimizing opt_check2.v verilog file:**

Commands to perform optimization-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check2.v
4. synth -top opt_check2
5. opt_clean -purge
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Optimized 2-input OR gate circuit :


![Screenshot from 2024-10-20 16-08-53](https://github.com/user-attachments/assets/734c3b95-0027-4992-bcfb-8130021b736c)

Terminal output: 

![Screenshot from 2024-10-20 16-08-19](https://github.com/user-attachments/assets/5a0aba3b-0c72-43f3-898e-b84d8d5be28f)

![Screenshot from 2024-10-20 16-08-41](https://github.com/user-attachments/assets/8f6c71c8-b45d-4622-9df4-7fbb257ea7da)


**3] Optimizing opt_check3.v verilog file:**


Commands to perform optimization-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check3.v
4. synth -top opt_check3
5. opt_clean -purge
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```


Optimized 3-input AND gate circuit :

![Screenshot from 2024-10-20 16-16-45](https://github.com/user-attachments/assets/779268c6-d4cd-4f47-8494-f55909539e61)


Terminal output:

![Screenshot from 2024-10-20 16-15-53](https://github.com/user-attachments/assets/f309ed3d-e638-4f51-a880-b33faba66e4b)


![Screenshot from 2024-10-20 16-16-10](https://github.com/user-attachments/assets/3b33a080-a2b5-4218-9a8a-c29f5531b73c)

![Screenshot from 2024-10-20 16-16-18](https://github.com/user-attachments/assets/0d02fdf4-7bf3-4b72-8000-a8fa5cac9d95)


![Screenshot from 2024-10-20 16-16-31](https://github.com/user-attachments/assets/a41c48b3-b9e0-42a7-8588-d611f09f37ba)


**4] Optimizing opt_check4.v verilog file:**

Commands to perform optimization-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog opt_check4.v
4. synth -top opt_check4
5. opt_clean -purge
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Optimized 3-input XNOR gate circuit :

![Screenshot from 2024-10-20 16-24-35](https://github.com/user-attachments/assets/5d06c5fa-893e-4074-b696-7f656f6d6bf4)

Terminal output:


![Screenshot from 2024-10-20 16-23-32](https://github.com/user-attachments/assets/3214fb25-6f5d-414c-a347-fd78ef7a47b8)

![Screenshot from 2024-10-20 16-23-49](https://github.com/user-attachments/assets/b8f58d82-2207-46d9-9d7f-b32c46de6074)

![Screenshot from 2024-10-20 16-24-03](https://github.com/user-attachments/assets/5b002e33-ae3c-4b7b-ba94-9c2a7e5bd12f)


![Screenshot from 2024-10-20 16-24-23](https://github.com/user-attachments/assets/794ed336-fdc1-4c08-83fa-e17621097142)


**5] Optimizing multiple_module_opt.v verilog file:**

Commands to perform optimization-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog multiple_module_opt.v

4. synth -top opt_check4
5. opt_clean -purge
6. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Optimized circuit:

![Screenshot from 2024-10-20 16-38-40](https://github.com/user-attachments/assets/f875960d-bfb8-47b5-bca3-97afb9b757af)


Terminal Output:

![Screenshot from 2024-10-20 16-37-47](https://github.com/user-attachments/assets/686cf35f-ac05-43d3-aaf4-4df173e0a5eb)


![Screenshot from 2024-10-20 16-38-07](https://github.com/user-attachments/assets/e5da6bb0-ba02-475e-ae5b-6f06567648eb)


![Screenshot from 2024-10-20 16-38-17](https://github.com/user-attachments/assets/bf96189f-17ad-426a-b1ea-aadfa16962a7)


![Screenshot from 2024-10-20 16-38-32](https://github.com/user-attachments/assets/39b2153b-61a5-4c27-8582-ecf848b7d894)


**LAB-7: Sequential Logic optimization**

1.1] Simulating dff_const1.v and it's testbench tb_dff_const1.v using iverilog and observing results on gtkwave


![Screenshot from 2024-10-20 16-47-40](https://github.com/user-attachments/assets/ef1bac93-a3b4-4758-9693-e5675b83a697)

![Screenshot from 2024-10-20 16-47-54](https://github.com/user-attachments/assets/7114fbe4-35a1-4f5b-bf0f-f958a8cde569)

Observation : As the reset signa goes low , the output "q" doesn't immediately goes high , instead it waits for the next positive edge of clock signal to change it's state.

1.2] Synthesizing the dff_const1.v file:

Commands to perform synthesis on dff_const1.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const1.v
4. synth -top dff_const1
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

```dfflibmap``` is used for mapping the D flip-flop.

Generated synthesized circuit for D-FF:

![Screenshot from 2024-10-20 17-51-22](https://github.com/user-attachments/assets/edd2af2a-5e5d-480f-af30-a0ca1cd56be6)

Terminal output:


![Screenshot from 2024-10-20 17-50-45](https://github.com/user-attachments/assets/59064161-220b-4e16-b0c5-a8075a2cdd22)


![Screenshot from 2024-10-20 17-50-58](https://github.com/user-attachments/assets/80c51b3b-a746-4b77-8d16-7b1a87a6fb31)

Observation - It is inferring a flop i.e D-FF. 

![Screenshot from 2024-10-20 17-51-14](https://github.com/user-attachments/assets/a765b84b-356f-40e5-a43b-83141f489c5b)



2.1] Simulating dff_const2.v and it's testbench tb_dff_const2.v using iverilog and observing results on gtkwave


![Screenshot from 2024-10-20 16-55-32](https://github.com/user-attachments/assets/3996a2f2-5df4-484c-847f-55673dadf4ae)


![Screenshot from 2024-10-20 16-56-02](https://github.com/user-attachments/assets/1ca9a97d-602f-448d-b326-8486777d4f72)


Observation : here, output "q" is always high, irrespective of the state of reset signal.

2.2] Synthesizing the dff_const2.v file:

Commands to perform synthesis on dff_const2.v :
```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const2.v
4. synth -top dff_const2
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated synthesized circuit:


![Screenshot from 2024-10-20 18-47-45](https://github.com/user-attachments/assets/d3e6cc0a-8f58-4019-89ef-f61eb86b12da)


Terminal output-

![Screenshot from 2024-10-20 17-58-52](https://github.com/user-attachments/assets/18f561e2-9e08-430f-8510-2cdc81436aab)


Observation : It is not inferring a flop here as it was doing for the dff_const1 synthesizing.


3.1] Simulating dff_const3.v and it's testbench tb_dff_const3.v using iverilog and observing results on gtkwave

![Screenshot from 2024-10-20 18-58-18](https://github.com/user-attachments/assets/597bbf3f-612d-4c40-88f1-bb76b0b191b5)


![Screenshot from 2024-10-20 18-58-30](https://github.com/user-attachments/assets/3ef14ea5-fa72-439a-acba-9c662d07eb47)

Observation: As reset signal goes low, output "q1" goes high at next positive edge of clock and simultaneously output "q" goes low and stays as active low(0) till next positive edge of clock signal and changes it's state to high(1).


3.2] Synthesizing the dff_const3.v file:

Commands to perform synthesis on dff_const3.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const3.v
4. synth -top dff_const3
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated synthesized circuit: We can observe 2 flops 1st is the reset flop and 2nd is the set flop.


![Screenshot from 2024-10-20 19-12-08](https://github.com/user-attachments/assets/8cc1d200-d916-4efc-bec3-363796893112)

Terminal output:

![Screenshot from 2024-10-20 19-10-44](https://github.com/user-attachments/assets/570c1a39-9f4a-4d28-bc24-f53f81819049)


![Screenshot from 2024-10-20 19-11-08](https://github.com/user-attachments/assets/a144a047-59f2-4a17-8cd5-c527e69e0d14)

![Screenshot from 2024-10-20 19-11-26](https://github.com/user-attachments/assets/c0e22cc0-6ffc-42b7-8951-3ee7677caf72)

![Screenshot from 2024-10-20 19-11-41](https://github.com/user-attachments/assets/6f6f0936-ff51-4361-8eaa-4f286bea43d1)


Observation : We can observe that it is inferring 2 filp-flops.

4.1] Simulating dff_const4.v and it's testbench tb_dff_const4.v using iverilog and observing results on gtkwave

![Screenshot from 2024-10-20 19-31-29](https://github.com/user-attachments/assets/3eb7e18d-a1fa-45a5-a086-0b48c57dabd9)


![Screenshot from 2024-10-20 19-31-38](https://github.com/user-attachments/assets/e51d22e1-126b-4bdf-9a4c-c5ef748c384d)

4.2] Synthesizing the dff_const4.v file:

Commands to perform synthesis on dff_const4.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const4.v
4. synth -top dff_const4
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated synthesized circuit:

![Screenshot from 2024-10-20 19-34-12](https://github.com/user-attachments/assets/741e6b46-c4a9-49ec-81fb-e109fdfa3f53)


Terminal output:

![Screenshot from 2024-10-20 19-33-20](https://github.com/user-attachments/assets/69cb6db6-435d-4b0b-9ede-4ec7c579e13c)


![Screenshot from 2024-10-20 19-33-42](https://github.com/user-attachments/assets/43ddd74d-4b84-45ae-ae07-098cf044a609)


![Screenshot from 2024-10-20 19-33-52](https://github.com/user-attachments/assets/f17d8dca-3ce0-48aa-8e08-be626c854f0b)


![Screenshot from 2024-10-20 19-34-05](https://github.com/user-attachments/assets/1881bf31-479c-44af-8188-c79ca176d05e)


5.1] Simulating dff_const5.v and it's testbench tb_dff_const5.v using iverilog and observing results on gtkwave

![Screenshot from 2024-10-20 19-40-51](https://github.com/user-attachments/assets/e85554e5-5245-4aae-b3ae-32280f25e4af)


![Screenshot from 2024-10-20 19-41-27](https://github.com/user-attachments/assets/62e86504-d2bf-4e94-aabc-20eee54a9a7a)

5.2] Synthesizing the dff_const5.v file:

Commands to perform synthesis on dff_const5.v :

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog dff_const5.v
4. synth -top dff_const5
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated synthesized circuit:

![Screenshot from 2024-10-20 19-44-38](https://github.com/user-attachments/assets/7b39438e-e50a-4c18-8f94-ec522fb1d637)

Terminal output:

![Screenshot from 2024-10-20 19-43-42](https://github.com/user-attachments/assets/e8dcedef-c1b4-4237-86c1-5ddf313b1773)

![Screenshot from 2024-10-20 19-43-53](https://github.com/user-attachments/assets/9cfd23a4-4e2a-4eb8-a539-c9f37ea83b9b)


![Screenshot from 2024-10-20 19-44-01](https://github.com/user-attachments/assets/3143fa85-0a2f-4aff-ac9f-60f1c8dd2824)


![Screenshot from 2024-10-20 19-44-13](https://github.com/user-attachments/assets/3553aebe-f8ff-4459-b375-5082214342bf)


![Screenshot from 2024-10-20 19-44-23](https://github.com/user-attachments/assets/aff8a53c-3c60-4c7c-b3f9-d81686dca158)


***Unused output optimization***


Optimizing the counter_opt.v verilog file

Command:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog counter_opt.v
4. synth -top counter_opt
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated optimized circuit:

![Screenshot from 2024-10-20 19-54-37](https://github.com/user-attachments/assets/fe58f2b6-ad8f-4f08-bb93-9f36a82ed726)


Terminal output:

![Screenshot from 2024-10-20 19-53-35](https://github.com/user-attachments/assets/0e9aa6c3-1008-496f-9574-3a1b0d3a3db7)


![Screenshot from 2024-10-20 19-53-46](https://github.com/user-attachments/assets/4da66e7a-26d3-4efa-91d2-c4ccfb123a1a)


![Screenshot from 2024-10-20 19-53-54](https://github.com/user-attachments/assets/563d077a-83b5-4cf5-81ca-8c78e4d357b6)

![Screenshot from 2024-10-20 19-54-01](https://github.com/user-attachments/assets/55fd9610-b734-4123-9808-8dd76aa236ed)


![Screenshot from 2024-10-20 19-54-09](https://github.com/user-attachments/assets/604bb636-08b5-41a3-bf3d-c16864c60992)

![Screenshot from 2024-10-20 19-54-15](https://github.com/user-attachments/assets/76a57fc2-9726-4c49-8fec-779233b2846b)



Observation : It infer only 1 D-FF

**Modifying the above RTL of counter**

Commands-

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog counter_opt2.v
4. synth -top counter_opt
5. dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
7. show
```

Generated circuit:

![image](https://github.com/user-attachments/assets/2ccad37a-0540-4615-851a-eef3ed57be2f)

Terminal output:

![Screenshot from 2024-10-20 20-28-09](https://github.com/user-attachments/assets/cb279e3a-10b4-4d87-abae-204835379f5e)

Observation - We can observe that 3 flip-flops are been inferred.

</details>


<details>
 <summary> Day-4 </summary>


 ****GLS , blocking vs non blocking and Synthesis-Simulation mismatch****

***LAB-8: GLS and synthesis-simulation Mismatch***

Verilog files used to perform this lab:


![Screenshot from 2024-10-20 20-42-54](https://github.com/user-attachments/assets/7f70b143-d666-4d4c-bf4f-439ccac22c8f)

1.1]Simulation of 2x1 Mux using Ternary operator

![Screenshot from 2024-10-20 21-02-22](https://github.com/user-attachments/assets/0b56d805-3d4b-4cc9-9f8e-2ac7b1cae8df)


![Screenshot from 2024-10-20 21-02-43](https://github.com/user-attachments/assets/1aa6a23d-486c-4c01-acd8-883ade5829c4)


1.2] Synthesis of 2x1 Mux using Ternary operator

Commands for synthesizing 2x1 Mux using Ternary operator:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog ternary_operator_mux.v
4. synth -top ternary_operator_mux
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr ternary_operator_mux_net.v
7. !gvim ternary_operator_mux_net.v
8. show
```

Generated Netlist:

![Screenshot from 2024-10-20 21-21-56](https://github.com/user-attachments/assets/e67e148d-8f58-4076-a45c-221d1940fb6c)



Generated circuit :

![Screenshot from 2024-10-20 21-15-52](https://github.com/user-attachments/assets/e0e1679a-875a-49d7-8223-9ca05304d058)

Terminal output :

![Screenshot from 2024-10-20 21-14-49](https://github.com/user-attachments/assets/62834055-520d-4598-8dfd-f540eff58360)

![Screenshot from 2024-10-20 21-15-09](https://github.com/user-attachments/assets/5352067d-15e2-4b20-86c4-c28cf8c37b5b)


![Screenshot from 2024-10-20 21-15-22](https://github.com/user-attachments/assets/0bed424c-2711-41df-b847-23c56c061acd)


![Screenshot from 2024-10-20 21-15-33](https://github.com/user-attachments/assets/8b1406c3-a1ed-430e-96dc-88413b71f86b)


Observation : One 2x1 MUX is inferred.

**1.3]Performing GLS (Gate Level Synthesis)**

Commands for GLS :

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

Terminal output:


![Screenshot from 2024-10-20 21-27-36](https://github.com/user-attachments/assets/f8bf1c9d-4dbe-4004-a2e8-ee70564239ad)

GTKwavefrom form the GLS output:

![Screenshot from 2024-10-20 21-27-49](https://github.com/user-attachments/assets/8583a100-c938-47bb-bbc4-bcecdeed1ceb)


2.1]Simulation of Bad Mux

![Screenshot from 2024-10-20 21-31-44](https://github.com/user-attachments/assets/f4f57092-935f-4424-b448-b01350437971)

![Screenshot from 2024-10-20 21-34-57](https://github.com/user-attachments/assets/0cebd7ca-91fb-4c48-80c4-f495d863f5a7)

Observation : The bad_mux is not properly working as a mux , as when select is low output "y" should follow "i0", but it fails to do so.

2.2] Synthesizing the Bad Mux verilog file.

Commands Used are:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog bad_mux.v
4. synth -top bad_mux
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr bad_mux_net.v
7. !gvim bad_mux_net.v
8. show
```

Generated Netlist:

![Screenshot from 2024-10-20 21-44-57](https://github.com/user-attachments/assets/920c4250-1c7d-4083-8261-571e609ea663)


Generated circuit:

![Screenshot from 2024-10-20 21-44-42](https://github.com/user-attachments/assets/b0e13e8c-4f6b-4afd-b3ea-1dd696db9d0d)


Terminal output:

![Screenshot from 2024-10-20 21-43-39](https://github.com/user-attachments/assets/1822bfc2-c035-4e99-8dff-3a2d5bf5a1f5)

![Screenshot from 2024-10-20 21-43-59](https://github.com/user-attachments/assets/7a1f4a82-d137-4f89-a79e-70585acaf698)

![Screenshot from 2024-10-20 21-44-15](https://github.com/user-attachments/assets/a8998c46-73d3-4605-8cb0-bdf08281aa13)

![Screenshot from 2024-10-20 21-44-32](https://github.com/user-attachments/assets/3f4fd81c-c830-4834-a3d0-ae66ac0a200b)

**2.3]Performing GLS (Gate Level Synthesis)**

Commands for GLS :

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```

Terminal output:


![Screenshot from 2024-10-20 21-49-09](https://github.com/user-attachments/assets/ecabc01a-f64e-4f7f-8491-298dbb41fbd2)

GTKWaveform for GLS for Bad Mux:

![Screenshot from 2024-10-20 21-51-41](https://github.com/user-attachments/assets/6d356252-8ead-45e0-bf77-e8ba4e94cb67)


Observation : After doing GLS, drawbacks of bad_mux are overcomed as now when select is low output "y" follows input "i0".


***LAB-9: Synthesis-simulation Mismatch Blocking statement***

Note: Verilog file used to perform this task is blocking_caveat.v

![Screenshot from 2024-10-20 22-01-40](https://github.com/user-attachments/assets/5a35841e-7139-4c85-9637-1d8f3b6f4bac)



1.1]Simulation of blocking_caveat.v


![Screenshot from 2024-10-20 22-01-51](https://github.com/user-attachments/assets/f2230b40-0d53-4d55-8d1e-06263b21fc7c)

![Screenshot from 2024-10-20 22-09-08](https://github.com/user-attachments/assets/aac0464f-68b9-4fc7-b1fb-1cd745088643)


Observation : At a particular point, when a=0 , b=0 , c=1 ; output of a|b should be = 0 ; hench the resultant d ie {a|b}&c should be 0 but instead we can observe it to be 1. 
	      This occurs due to usage of blocking statement(logic is x=a&b , d = x|c where x is intermidiate variable)


1.2]Synthesizing of blocking_caveat.v

Commands used for synthesizing:

```
1. yosys
2. read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
3. read_verilog blocking_caveat.v
4. synth -top blocking_caveat
5. abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
6. write_verilog -noattr blocking_caveat_net.v
7. !gvim blocking_caveat_net.v
8. show
```

Generated netlist:

![Screenshot from 2024-10-20 22-18-43](https://github.com/user-attachments/assets/aa7ddbe1-91c3-41a6-917f-ce04d58451fb)


Generated circuit :


![Screenshot from 2024-10-20 22-18-51](https://github.com/user-attachments/assets/5e4ebc5a-791f-44fc-b30b-04bf96757fbf)

Terminal output:

![Screenshot from 2024-10-20 22-17-55](https://github.com/user-attachments/assets/69de6cbd-e7e0-4daa-bdf3-d4b5be8ed7f5)


![Screenshot from 2024-10-20 22-18-03](https://github.com/user-attachments/assets/9472df63-fae2-4684-9b0c-ab61599a75ab)

![Screenshot from 2024-10-20 22-18-25](https://github.com/user-attachments/assets/d4274e96-fb17-468d-bb6f-9f673ae960a5)


**1.3]Performing GLS (Gate Level Synthesis)**

Commands for GLS :

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```

Terminal output:

![Screenshot from 2024-10-20 22-22-56](https://github.com/user-attachments/assets/41b902bd-a798-425d-ba9c-064ce7f889c1)


GTKWave output:

![Screenshot from 2024-10-20 22-24-56](https://github.com/user-attachments/assets/f22b61f2-9892-4a7c-ad29-4ce61a6e281f)


Observation : Hence after performing GLS (gate level synthesis) drawback is overcomed as when a=0 , b=0 , c=1 ; output of a|b should be = 0 ; hench the resultant d ie {a|b}&c should be 0 and we can observe it to be 0. 


</details>

</details>

<details>
 <summary> TASK-9 </summary>

 ***Synthesis of RISC-V using yosys and Post synthesis simulation of Babysoc using iverilog GTKwave***


To perform synthesis and generate netlist we will use YOSYS synthesizer.

**Commands to generate netlist** 

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -lib ../lib/avsddac.lib
read_liberty -lib ../lib/avsdpll.lib
read_verilog vsdbabysoc.v
read_verilog rvmyth.v
read_verilog clk_gate.v
synth -top vsdbabysoc
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show vsdbabysoc
write_verilog -noattr vsdbabysoc.synth.v
!gvim vsdbabysoc.synth.v
```

Synthesised Circuit Diagram for generated netlist:

![Screenshot from 2024-10-24 00-31-40](https://github.com/user-attachments/assets/907cc374-c317-47fc-8434-d00c54c83004)

Generated Netlist :

![Screenshot from 2024-10-24 01-23-40](https://github.com/user-attachments/assets/3339f763-7d54-407c-b259-8fe87870c531)


![Screenshot from 2024-10-24 01-23-48](https://github.com/user-attachments/assets/f970804c-47f3-4af7-94e7-a91dca75928b)


![Screenshot from 2024-10-24 01-24-17](https://github.com/user-attachments/assets/307c1345-11e0-4ab4-a86f-37f7691a1a7a)

Terminal output :

![Screenshot from 2024-10-24 01-03-53](https://github.com/user-attachments/assets/986f4e2f-922c-4200-b3b1-8b5ef53fac01)
![Screenshot from 2024-10-24 01-05-08](https://github.com/user-attachments/assets/d10e83cd-177b-475a-9e29-c0782f148140)


![Screenshot from 2024-10-24 01-05-16](https://github.com/user-attachments/assets/cf16388d-e969-4500-8a0e-1d8c8354c8f8)

![Screenshot from 2024-10-24 01-05-23](https://github.com/user-attachments/assets/e7943e34-e414-47c2-98ed-85acedf4c86e)


![Screenshot from 2024-10-24 01-05-38](https://github.com/user-attachments/assets/204bcd16-697b-4cee-8e16-a822fcf60715)

![Screenshot from 2024-10-24 01-05-47](https://github.com/user-attachments/assets/a30d49fa-ae78-4cf9-bb22-4be49888a635)


***Performing GLS (Gate Level Synthesis):***

Commands to perform GLS :

```
cd VSDBabySoC
mkdir -p output/post_synth_sim && iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM -DFUNCTIONAL -DUNIT_DELAY=#1 -I src/module/include -I src/module -I src/gls_model src/module/testbench.v && cd output/post_synth_sim && ./post_synth_sim.out
gtkwave post_synth_sim.vcd
```

***After performing GLS we can see the post synthesis simulation of RISCV processor as below***

Terminal output -

![Screenshot from 2024-10-24 01-12-33](https://github.com/user-attachments/assets/4d5c4538-f99f-4469-941b-29c7740bdeb1)

GTKwaveform :

***Post synthesis simulation waveform:[SYNTHESIZED OUTPUT]***

![Screenshot from 2024-10-24 01-08-57](https://github.com/user-attachments/assets/3d252f7a-a8af-4e03-87e1-c140a4de1577)

Now verifying the result with pre-synthesis-simulation :

![Screenshot from 2024-10-23 20-23-54](https://github.com/user-attachments/assets/774decad-6be7-4cc1-8d40-f2509327dd22)

***Pre synthesis simulation waveform [FUNCTIONALITY OUTPUT]***

![Screenshot from 2024-10-23 20-24-07](https://github.com/user-attachments/assets/201272dc-13a7-4d89-9fa5-c23e83822023)

***Observation : We can observed that the waveforms for pre_synth_simulation and  post_synth_simulation i.e after using Yosys synthesis are the same.
		  Hence we can observe sum of 1 to 9 as 2D. Hence output O1 = O2***


</details>

</details>

<details>
 <summary> TASK-10 </summary>

***LAB - Timing Analysis of VSDBabySOC using OpenSTA***


## STA:
Static Timing Analysis (STA) is essential in ASIC design for ensuring that the digital circuit meets the required timing constraints without requiring dynamic simulation of actual data. The focus of STA is to validate that all timing paths within the design meet specific constraints, which ensures the circuit will function correctly across all operational conditions.

* Timing Paths: In STA, timing paths are analyzed to ensure data can travel from one point to another within a defined time. The main types are:

* Setup Paths: Ensure data arrives at the next stage before the clock edge.
* Hold Paths: Ensure data is stable for a certain period after the clock edge.
* Clock Domains: STA divides the design into different clock domains to verify timing between elements synchronized to the same or different clocks. For multiple clocks, STA verifies the timing paths between each clock domain, focusing on:

* Synchronous Domains: Where clocks are related and can be analyzed for setup and hold constraints.
* Asynchronous Domains: Where clocks are unrelated, requiring special handling, often with synchronizers or FIFO buffers.
Clock Skew and Jitter:

* Clock Skew: The difference in arrival times of a clock signal at different flip-flops. STA checks skew impact since it affects timing paths and data setup/hold requirements.
* Clock Jitter: Variation in clock edge timing due to noise or other factors. STA incorporates jitter in timing analysis to ensure that jitter doesn’t cause timing violations.


### Timing Checks:
* Setup Check: Ensures data arrives before the clock edge, allowing sufficient time for stabilization.
* Hold Check: Ensures data remains stable long enough after the clock edge.

### Timing Margins and Slack:

* Slack: The difference between the required time and the actual arrival time of signals. Positive slack means timing constraints are met, while negative slack indicates a timing violation.
* Setup Slack: Time margin for setup constraints.
* Hold Slack: Time margin for hold constraints.
* Static Timing Tools: STA tools, like Synopsys PrimeTime and Cadence Tempus, perform analysis by creating and traversing timing graphs that represent all paths in the design. These tools provide reports on slack, critical paths, and timing violations.

Process, Voltage, and Temperature (PVT) Corners: STA includes PVT analysis to account for variations in manufacturing, operational voltages, and temperature ranges. STA ensures that timing constraints are met across worst-case PVT corners.

## Optimization Techniques:

* Buffer Insertion: Adds buffers to reduce delay in long paths.
* Gate Sizing: Resizes gates to improve timing on critical paths.
* Clock Tree Optimization (CTO): Minimizes skew and jitter in the clock distribution network. By ensuring that timing analysis is thorough and covers all potential scenarios, STA plays a crucial role in achieving reliable and high-performance ASIC designs.

### reg2reg Path:
A reg2reg path (register-to-register path) refers to a timing path in a digital circuit that connects two sequential elements, specifically flip-flops or registers. This path is crucial in the context of Static Timing Analysis (STA) because it represents the flow of data from one register to another through combinational logic.

Reg2reg paths are essential for ensuring proper data flow and synchronization in digital circuits, especially in designs with pipelining or sequential operations. Analyzing these paths helps in verifying that the data processing occurs correctly across clock cycles, thereby ensuring the overall functionality and reliability of the circuit.

### clk2reg Path:
A clk2reg path (clock-to-register path) refers to a timing path in a digital circuit that connects the clock signal to a register (flip-flop). This path is crucial for ensuring that the register operates correctly in response to clock events.

The following commands were run to get the max-min report of the VSDbabysoc design:

```
read_liberty /mnt/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog /mnt/vsdbabysoc.synth.v  
link_design rvmyth

create_clock -name CLK -period 9.95 [get_ports CLK]
set_clock_uncertainty [expr 0.05 * 9.95] -setup [get_clocks CLK]
set_clock_uncertainty [expr 0.08 * 9.95] -hold [get_clocks CLK]
set_clock_transition [expr 0.05 * 9.95] [get_clocks CLK]
set_input_transition [expr 0.08 * 9.95] [all_inputs]

report_checks -path_delay max
report_checks -path_delay min
```

Timing configurations:

    Clock period: 9.95 nanoseconds
    Setup uncertainty: 5% of clock period
    Clock transition: 5% of clock period
    Hold uncertainty: 8% of clock period
    Input transition: 8% of clock period


Terminal output :

![Screenshot from 2024-10-28 18-49-57](https://github.com/user-attachments/assets/e57a2e6a-1fb4-4459-8c8f-a310ded2d904)

Reg2Reg max path:

![Screenshot from 2024-10-28 18-50-48](https://github.com/user-attachments/assets/5492c675-14fd-4a6b-ab27-eeff5e5e63e0)

Reg2Reg min path:

![Screenshot from 2024-10-28 18-51-00](https://github.com/user-attachments/assets/dd536846-6310-4689-8d27-938dec7c8c9a)

The max path report indicates Setup Slack while the min path report shows Hold Slack measurements.

</details>

<details>
 <summary> TASK-11 </summary>

***LAB: PVT Corner Analysis for Synthesized VSDBabySoC using OpenSTA***

The STA checks are performed across all the corners to confirm the design meets the target timing requirements.

The worst max path (Setup-critical) corners in the sub-40nm process nodes are usually: ss_LowTemp_LowVolt, ss_HighTemp_LowVolt (Slowest corners)
The worst min path (Hold-critical) corners being: ff_LowTemp_HighVolt,ff_HighTemp_HighVolt (Fastest corners).

***The below tcl script ```sta_pvt.tcl``` can be run to perform the STA across the PVT corners for which the sky130 lib files are available:***

```
set list_of_lib_files(1) "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(2) "sky130_fd_sc_hd__tt_100C_1v80.lib"
set list_of_lib_files(3) "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(4) "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(7) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(8) "sky130_fd_sc_hd__ff_n40C_1v95.lib"
set list_of_lib_files(9) "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(14) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(15) "sky130_fd_sc_hd__ss_n40C_1v60.lib"
set list_of_lib_files(16) "sky130_fd_sc_hd__ss_n40C_1v76.lib"

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
read_liberty /mnt/$list_of_lib_files($i)
read_liberty -min /mnt/avsdpll.lib
read_liberty -max /mnt/avsdpll.lib
read_liberty -min /mnt/avsddac.lib
read_liberty -max /mnt/avsddac.lib
read_verilog /mnt/vsdbabysoc.synth.v
link_design rvmyth
read_sdc /mnt/vsdbabysoc_synthesis.sdc
check_setup -verbose
report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > /mnt/sta_output/min_max_$list_of_lib_files($i).txt

exec echo "$list_of_lib_files($i)" >> /mnt/sta_output/sta_worst_max_slack.txt
report_worst_slack -max -digits {4} >> /mnt/sta_output/sta_worst_max_slack.txt

exec echo "$list_of_lib_files($i)" >> /mnt/sta_output/sta_worst_min_slack.txt
report_worst_slack -min -digits {4} >> /mnt/sta_output/sta_worst_min_slack.txt

exec echo "$list_of_lib_files($i)" >> /mnt/sta_output/sta_tns.txt
report_tns -digits {4} >> /mnt/sta_output/sta_tns.txt

exec echo "$list_of_lib_files($i)" >> /mnt/sta_output/sta_wns.txt
report_wns -digits {4} >> /mnt/sta_output/sta_wns.txt
}

```

***The SDC file used for generating clock and data constraints is given below:***

```
# Create clock with new period
create_clock [get_pins pll/CLK] -name clk -period 9.95 -waveform {0 4.975}

# Set loads
set_load -pin_load 0.5 [get_ports OUT]
set_load -min -pin_load 0.5 [get_ports OUT]

# Set clock latency
set_clock_latency 1 [get_clocks clk]
set_clock_latency -source 2 [get_clocks clk]

# Set clock uncertainty
set_clock_uncertainty 0.4975 [get_clocks clk]  ; # 5% of clock period for setup
set_clock_uncertainty -hold 0.796 [get_clocks clk] ; # 8% of clock period for hold

# Set maximum delay
set_max_delay 10.05 -from [get_pins dac/OUT] -to [get_ports OUT]

# Set input delay for VCO_IN
set_input_delay -clock clk -max 4 [get_ports VCO_IN]
set_input_delay -clock clk -min 1 [get_ports VCO_IN]

# Set input delay for ENb_VCO
set_input_delay -clock clk -max 4 [get_ports ENb_VCO]
set_input_delay -clock clk -min 1 [get_ports ENb_VCO]

# Set input delay for ENb_CP
set_input_delay -clock clk -max 4 [get_ports ENb_CP]
set_input_delay -clock clk -min 1 [get_ports ENb_CP]

# Set input transition for VCO_IN
set_input_transition -max 0.4975 [get_ports VCO_IN] ; # 5% of clock
set_input_transition -min 0.796 [get_ports VCO_IN] ; # adjust if needed

# Set input transition for ENb_VCO
set_input_transition -max 0.4975 [get_ports ENb_VCO] ; # 5% of clock
set_input_transition -min 0.796 [get_ports ENb_VCO] ; # adjust if needed

# Set input transition for ENb_CP
set_input_transition -max 0.4975 [get_ports ENb_CP] ; # 5% of clock
set_input_transition -min 0.796 [get_ports ENb_CP] ; # adjust if needed
```

***Run below commands on terminal to source the sta_pvt.tcl file***

![Screenshot from 2024-11-09 01-48-26](https://github.com/user-attachments/assets/faa27cec-0d1a-48de-9ad9-a157e69f0be0)



***A table comprising of the worst setup, hold slacks and TNS from the reports is shown below:***

| Library                                      | WNS     | Worst Min Slack (or) Worst Hold Slack | TNS     | Worst Max Slack (or) Worst Setup Slack |
|----------------------------------------------|---------|--------------------------------------|---------|----------------------------------------|
| sky130_fd_sc_hd__tt_025C_1v80.lib            | 0.0000  | -0.4864                              | 0.0000  | 0.3917                                 |
| sky130_fd_sc_hd__tt_100C_1v80.lib            | 0.0000  | -0.4815                              | 0.0000  | 0.5460                                 |
| sky130_fd_sc_hd__ff_100C_1v65.lib            | 0.0000  | -0.5469                              | 0.0000  | 2.5070                                 |
| sky130_fd_sc_hd__ff_100C_1v95.lib            | 0.0000  | -0.6000                              | 0.0000  | 4.0193                                 |
| sky130_fd_sc_hd__ff_n40C_1v56.lib            | 0.0000  | -0.5045                              | 0.0000  | 0.7306                                 |
| sky130_fd_sc_hd__ff_n40C_1v65.lib            | 0.0000  | -0.5409                              | 0.0000  | 1.8637                                 |
| sky130_fd_sc_hd__ff_n40C_1v76.lib            | 0.0000  | -0.5717                              | 0.0000  | 2.8826                                 |
| sky130_fd_sc_hd__ff_n40C_1v95.lib            | 0.0000  | -0.6085                              | 0.0000  | 4.0444                                 |
| sky130_fd_sc_hd__ss_100C_1v40.lib            | -18.6691| 0.1093                               | -3124.0125| -18.6691                              |
| sky130_fd_sc_hd__ss_100C_1v60.lib            | -9.4215 | -0.1540                              | -1232.7720| -9.4215                               |
| sky130_fd_sc_hd__ss_n40C_1v28.lib            | -64.1107| 1.0336                               | -14859.7744| -64.1107                             |
| sky130_fd_sc_hd__ss_n40C_1v35.lib            | -41.2445| 0.5515                               | -8823.7441| -41.2445                             |
| sky130_fd_sc_hd__ss_n40C_1v40.lib            | -31.2412| 0.3289                               | -6218.5728| -31.2412                             |
| sky130_fd_sc_hd__ss_n40C_1v44.lib            | -25.4554| 0.1949                               | -4771.8467| -25.4554                             |
| sky130_fd_sc_hd__ss_n40C_1v60.lib            | -12.1565| -0.1332                              | -1743.6814| -12.1565                             |
| sky130_fd_sc_hd__ss_n40C_1v76.lib            | -5.9294 | -0.2922                              | -639.6851 | -5.9294                              |




From the table, we have plotted the below graphs:

***1: WNS:***


![WNS_plot](https://github.com/user-attachments/assets/9a132e8c-bdde-4771-96b5-c88e4d2d79c9)





***2: Worst min slack (or) Worst Hold slack***


![Worst_Min_Slack_plot](https://github.com/user-attachments/assets/38bc652f-b0a3-4986-98d6-01ed6ca533cf)



***3: Total Negative Slack (TNS)***


![TNS_plot](https://github.com/user-attachments/assets/bbd3467c-1f7e-44ab-828e-f4720f6c3745)



***4: Worst max slack (or) Worst Setup slack***


![Worst_Max_Slack_plot](https://github.com/user-attachments/assets/3e944497-b026-405a-9d5c-907595d250fe)



Observation:

1: Worst setup slack - sky130_fd_sc_hd__ss_n40C_1v28 PVT Corner library file

2: Worst hold slack - sky130_fd_sc_hd__ff_n40C_1v95 PVT Corner library file

</details>

<details>
 <summary> TASK-12 </summary>

# Advanced Physical Design Using Openlane/Sky130 Wokshop


<details>
 <summary> Day-1 </summary>

## Inception of open-source EDA, OpenLANE and Sky130 PDK:

Package
In any embedded board we have seen, the part of the board we consider as the chip is only the PACKAGE of the chip which is nothing but a protective layer or packet bound over the actual chip and the actual manufatured chip is usually present at the center of a package wherein, the connections from package is fed to the chip by WIRE BOUND method which is none other than basic wired connection.

![312795278-7562205a-7435-46c7-a66e-de1626911f14](https://github.com/user-attachments/assets/6129687c-6614-4222-8548-a152477648ac)

![312795953-7005a9e3-79da-4590-bea0-eb3768127a3d](https://github.com/user-attachments/assets/4524ebc8-b0be-475a-9aa5-09198c2f10b6)

![312797220-70b1c678-2a2e-484f-9181-812dbcd5f0a3](https://github.com/user-attachments/assets/5b7b982b-38c0-4bf3-b03e-09d61882283f)

Chip
Now, taking a look inside the chip, all the signals from the external world to the chip and vice versa is passed through PADS. The area bound by the pads is CORE where all the digital logic of the chip is placed. Both the core and pads make up the DIE which is the basic manufacturing unit in regards to semiconductor chips.

![312798569-d65a0ddf-2f86-4bbc-8d36-b02e09a1483e](https://github.com/user-attachments/assets/3b8ebd12-3ace-48af-8a35-81261ab8cbf0)


FOUNDRY is the place where the semiconductor chips are manufactured and FOUNDRY IP's are Intellectual Properties based on a specific foundry and these IP's require a specific level of intelligence to be produced whereas, repeatable digital logic blocks are called MACROS.

![312801338-ed1cd25e-6270-4b84-8f0d-f0ea7c8a7ef8](https://github.com/user-attachments/assets/11b260a2-a0b9-4ae2-a98a-be9db3eab904)

ISA (Intruction Set Architecture)
A C program which has to be run on a specific hardware layout which is the interior of a chip in your laptop, there is certain flow to be followed.
Initially, this particular C program is compiled in it's assembly language program which is nothing but RISC-V ISA (Reduced Instruction Set Compting - V Intruction Set Architecture).
Following this, the assembly language program is then converted to machine language program which is the binary language logic 0 and 1 which is understood by the hardware of the computer.
Directly after this, we've to implement this RISC-V specification using some RTL (a Hardware Description Language). Finally, from the RTL to Layout it is a standard PnR or RTL to GDSII flow.

![269298849-7dc4601a-e386-48e5-9d1f-7fa5b47ca0ba](https://github.com/user-attachments/assets/c65ea3ac-8f5e-4d36-ae81-5f8755e7809f)


For an application software to be run on a hardware there are several processes taking place. To begin with, the apps enters into a block called system software and it converts the application program to binary language. There are various layers in system software in which the major layers or components are OS (Operating System), Compiler and Assembler.
At first the OS outputs are small function in C, C++, VB or Java language which are taken by the respective compiler and converted into instructions and the syntax of these instructions varies with the hardware architecture on which the system is implemented.
Then, the job of the assembler is to take these instructions and convert it into it's binary format which is basically called as a machine language program. Finally, this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.

![269299259-19e8b634-f209-41a6-928d-6fba66f5b177](https://github.com/user-attachments/assets/c0e056e7-66cc-4103-9818-b51f0e004b15)

For example, if we take a stopwatch app on RISC-V core, then the output of the OS could be a small C function which enters into the compiler and we get output RISC-V instructions following this, the output of the assembler will be the binary code which enters into your chip layout.

![269300431-7d4570ca-82a6-4abe-81d2-067ebb9b2c15](https://github.com/user-attachments/assets/4ea137ab-e6a9-4025-9fd1-f26c39153179)

For the above stopwatch the following are the input and output of the compiler and assembler.

![269300848-d7b7fd1b-21ee-46b7-9a91-8314bd753a51](https://github.com/user-attachments/assets/befb5b74-ba3a-49c2-bed6-46f6ad970a12)

The output of the compiler are instructions and the output of the assembler is the binary pattern. Now, we need some RTL (a Hardware Description Language) which understands and implements the particular instructions. Then, this RTL is synthesised into a netlist in form of gates which is fabricated into the chip through a physical design implementation.


![269301398-e349cb06-45e3-4ae4-b85f-9020a0a62737](https://github.com/user-attachments/assets/8c3cef92-00bf-4d7e-8c23-13c522cf4a34)


There are mainly 3 different parts in this course. They are:
1. RISC-V ISA
2. RTL and synthesis of RISC-V based CPU core - picorv32
3. Physical design implementation of picorv32

![269301455-832f0ea6-2d60-4d9a-937c-a2dedd5f8cac](https://github.com/user-attachments/assets/09fbcee1-cd89-4b57-aa19-d9a1b4b879d0)

Open-source Implementation
For open-source ASIC design implemantation, we require the following enablers to be readily available as open-source versions. They are:-
RTL Designs
EDA Tools
PDK Data
Initially in the early ages, the design and fabrication of IC's were tightly coupled and were only practiced by very few companies like TI, Intel, etc.
In 1979, Lynn Conway and Carver Mead came up with an idea to saperate the design from the fabrication and to do this they inroduced structured design methodologies based on the λ-based design rules and published the first VLSI book "Introduction to VLSI System" which started the VLSI education.
This methodology resulted in the emergence of the design only companies or "Fabless Companies" and fabrication only companies that we usually refer to as "Pure Play Fabs".
The inteface between the designers and the fab by now became a set of data files and documents, that are reffered to as the "Process Design Kits (PDKs)".
The PDK include but not limited to Device Models, Technology Information, Design Rules, Digital Standard Cell Libraries, I/O Libraries and many more.
Since, the PDK contained variety of informations, and so they were distributed only under NDAs (Non-Disclosure Agreements) which made it in-accessible to the public.
Recently, Google worked out an agreement with skywater to open-source the PDK for the 130nm process by skywater Technology, as a result on 30 June 2020 Google released the first ever open-source PDK.


![312922831-87384374-e66b-4ec6-b9c4-3fb92ad4d275](https://github.com/user-attachments/assets/304a8081-dcce-4481-8848-4074f306118a)

ASIC design is a complex step that involves tons of steps, various methodologies and respective EDA tools which are all required for successful ASIC implementation which is achieved though an ASIC flow which is nothing but a piece of software that pulls different tools togather to carry out the design process.

![312933981-1762d6d6-c5f8-4bd9-8a3d-968eb4360889](https://github.com/user-attachments/assets/18755981-b2dc-4453-b614-e940e937ddce)


OpenLANE Open-source ASIC Design Implementation Flow
The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.


![312934312-533f58ee-4524-4a18-abb5-36b4d6a56b1f](https://github.com/user-attachments/assets/7974d8d7-2a3a-494e-8ddc-45e82d38a018)

Synthesis is the process of convertion or translation of design RTL into circuits made out of Standard Cell Libraries (SCL) the resultant circuit is described in HDL and is usually reffered to as the Gate-Level Netlist.
Gate-Level Netlist is functionally equivalent to the RTL.


![312938905-e43891a0-ab09-4df2-898d-7e843158e936](https://github.com/user-attachments/assets/5769f79d-79c6-446b-96a6-5e86c7e2ff09)

The fundemental building blocks which are the standard cells have regular layouts.
Each cell has different views/models which are utilised by different EDA tools like liberty view with electrical models of the cells, HDL behavioral models, SPICE or CDL views of the cells, Layout view which include GDSII view which is the detailed view and LEF view which is the abstract view.


![312940995-48df884c-c894-4a2a-a511-09321c208d6b](https://github.com/user-attachments/assets/97a19548-b02b-48e5-925f-15ba92ecc9e2)

Chip Floor Planning

![312946544-38ecd866-ac83-42c7-83ba-2ba995f9ba4e](https://github.com/user-attachments/assets/64866591-3b51-407d-9510-a1d082ec5b96)

Macro Floor Planning

![312947291-35ac760c-bba9-4bd1-9c65-e8ceeee2ccf5](https://github.com/user-attachments/assets/86f196b0-fe98-4cca-ad25-34f61c33bd7b)

Power Planning typically uses upper metal layers for power distribution since thay are thicker than lower metal layers and so have lower resistance and PP is done to avoid electron migration and IR drops.

![312948523-f18013a7-e4c7-4a6d-ba53-33362c04689a](https://github.com/user-attachments/assets/0a0ec742-fb5c-4307-b9dd-cf476f346831)


Placement


![312949059-3654398b-40bc-4e42-9205-77f673d5584c](https://github.com/user-attachments/assets/377c2ec3-d964-4353-9064-1048fe839968)

Global placement provide approximate locations for all cells based on connectivity but in this stage the cells may be overlapped on each other and in detailed placement the positions obtained from global placements are minimally altered to make it legal (non-overlapping and in site-rows)


![312949260-817c504d-0b8e-4a0a-9c3c-e9d110c23535](https://github.com/user-attachments/assets/8e6baefb-0915-42ab-8868-04a0018f0142)

Clock Tree Synthesis

![312950486-6db284d4-065f-450a-9200-a6e6cbfd7fbb](https://github.com/user-attachments/assets/328d68af-11b0-48ad-a355-91a415dae8f5)

Clock skew is the time difference in arrival of clock at different components.
Routing

![312951506-7458495f-b527-4f21-813e-8dbcbf29ed9b](https://github.com/user-attachments/assets/28ddc7a2-9e1a-4434-9f05-c60c522ebde6)

skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.

![312952603-e4438c12-d83e-4083-a58f-33a410a47927](https://github.com/user-attachments/assets/fcffe85f-e771-449e-bb2f-d8d76b25459b)


Global and Detailed Routing

![312953218-b54ebd4c-127a-441f-829e-6000531e9b8d](https://github.com/user-attachments/assets/d9f6d7d0-15dd-4016-83fe-c8336f8214ba)

Once done with the routing the final layout can be generated which undergoes various Sign-Off checks.
Design Rules Checking (DRC) which verifies that the final layout honours all design fabrication rules.
Layout Vs Schematic (LVS) which verifies that the final layout functionality matches the gate-level netlist that we started with.
Static Timing Analysis (STA) to verify that the design runs at the designated clock frequency.



![312954748-d8bc72cd-2fe9-4ae2-9431-68a6fa77c671](https://github.com/user-attachments/assets/da1501a5-b57a-44d3-a1f9-3e794a2dedd9)

Implementation
Section 1 tasks:-

Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
Calculate the flop ratio.

```
Flop Ratio = Number of D Flip Flops / Total Number of Cells

Percentage of DFF's = Flop Ratio * 100
```




Tasks:

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.

2. Calculate the flop ratio.

The Flop ratio can be calculated as follows:

```
Flop Ratio = Number of D Flip-Flops/ Total Number of Cells
	Percentage of Flip Flops = Flop Ratio * 100
```


## 1.  Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs

Commands to invoke the OpenLANE flow and perform floorplan -

```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```

```
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```
 
Screenshots of running each commands -


![Screenshot 2024-11-10 235419](https://github.com/user-attachments/assets/fb37b0a2-e62c-4710-be55-05b677be698a)


![Screenshot 2024-11-10 235625](https://github.com/user-attachments/assets/fab4766a-71b0-4b1d-b70e-40b4a7780c3f)


![Screenshot 2024-11-11 001955](https://github.com/user-attachments/assets/da59d0b3-a3ff-45a5-b06e-7cd7754f689d)

![Screenshot 2024-11-11 002354](https://github.com/user-attachments/assets/5aa03c06-3a1d-4bad-ac96-177563b3ef93)


![Screenshot 2024-11-11 002411](https://github.com/user-attachments/assets/776e0c46-1333-4377-8479-4a7676d620a4)

## Date: 10-11_18-25

![Screenshot 2024-11-11 003811](https://github.com/user-attachments/assets/8eedcf39-ef7f-4f6b-a152-26baf2c4b5c0)

Calculation of Flop Ratio and DFF % from synthesis statistics report file

```
Flop Ratio = 1613/14876 = 0.108429685
    Percentage of Flip Flops = 0.108429685 ∗ 100 = 10.84296854%
```

</details>

<details>
 <summary> Day-2 </summary>

 ## Good floorplan vs bad floorplan and introduction to library cells
 
**Tasks:**

1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2. Calculate the die area in microns from the values in floorplan def.
3. Load generated floorplan def in magic tool and explore the floorplan.
4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate 
   necessary outputs.
5. Load generated placement def in magic tool and explore the placement. Area of Die in 
   microns = Die width in microns ∗ Die height in microns
   
***1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs***

Commands to invoke the OpenLANE flow and perform floorplan

```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```

```
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```
***Screenshot of floorplan run***

![Screenshot 2024-11-12 230418](https://github.com/user-attachments/assets/3ed1f9a5-aa2d-46d7-b0c2-c92daf977f40)

![Screenshot 2024-11-12 230511](https://github.com/user-attachments/assets/c515f353-67d7-4bc6-9e87-353945ee8330)


***2. Calculate the die area in microns from the values in floorplan def.***

![Screenshot 2024-11-12 235300](https://github.com/user-attachments/assets/c1a8c769-c1d0-4568-b4c8-8557708ffe7c)

![Screenshot 2024-11-12 231625](https://github.com/user-attachments/assets/cf05ef5b-beb0-4fbe-9fee-a9b78824e305)

## Floorplan DEF Analysis

According to the floorplan DEF:

- **1000 Unit Distance**: 1 Micron
- **Die Width in Unit Distance**: \(660685 - 0 = 660685\)
- **Die Height in Unit Distance**: \(671405 - 0 = 671405\)
- **Distance in Microns**: Value in Unit Distance / 1000

### Calculated Die Dimensions in Microns:
- **Die Width**: \(660685/1000 = 660.685\) Microns
- **Die Height**: \(671405/1000 = 671.405\) Microns
- **Area of Die in Square Microns**:
  \[
  660.685 * 671.405 = 443587.212425 Square Microns
  \]

***Load generated floorplan def in magic tool and explore the floorplan.***

Commands to load floorplan def in magic in another terminal

```
# Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-11_17-31/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

![Screenshot 2024-11-12 232001](https://github.com/user-attachments/assets/3a96caf9-5764-4042-8028-dc8e3895ab13)

***Equidistant placement of ports:***


![Screenshot 2024-11-12 232435](https://github.com/user-attachments/assets/ef231500-fa5d-46f4-b1bb-40e055cd86f1)

**Port layer as set through config.tcl**

![Screenshot 2024-11-12 234047](https://github.com/user-attachments/assets/8e4de56f-f7fb-47fa-a951-d2b804b6a877)

![Screenshot 2024-11-12 234146](https://github.com/user-attachments/assets/24f46e44-5696-4436-ba27-a121344271d4)

**Decap Cells and Tap Cells**

![Screenshot 2024-11-12 234453](https://github.com/user-attachments/assets/8b0d11c4-d61d-4a3e-a0f5-5948d9f83e2f)

**Diogonally equidistant Tap cells**

![Screenshot 2024-11-12 234608](https://github.com/user-attachments/assets/fc08eddc-6340-45b4-9d3c-5cd534c78ad5)

**Unplaced standard cells at the origin**

![Screenshot 2024-11-12 234727](https://github.com/user-attachments/assets/6557ee36-e85a-490c-9c55-cc3ab64f5f1d)

***4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs. Command to run placement***


```
# Congestion aware placement by default
run_placement

```


![Screenshot 2024-11-12 235402](https://github.com/user-attachments/assets/03fdd702-9fa0-4308-a26d-a1090aab7769)

***5. Load generated placement def in magic tool and explore the placement. Commands to load placement def in magic in another terminal***

```
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-11_17-31/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![Screenshot 2024-11-13 000448](https://github.com/user-attachments/assets/1427e415-5d3e-4418-a800-16d9ae6eef4a)


![Screenshot 2024-11-13 000500](https://github.com/user-attachments/assets/e35a7aa6-a18e-467c-b5ce-c0ebbffa1681)

**Standard cells legally placed**

![Screenshot 2024-11-13 000537](https://github.com/user-attachments/assets/726887ed-33e2-45cb-824d-49ed8250f30a)

</details>

<details>
 <summary> Day-3 </summary>

## Design Library Cell Using Magic Layout and Cell characterization:

Tasks:

1.Clone custom inverter standard cell design from github repository: Standard cell design and characterization using OpenLANE flow.
2.Load the custom inverter layout in magic and explore.
3.Spice extraction of inverter in magic.
4.Editing the spice model file for analysis through simulation.
5.Post-layout ngspice simulations.
6.Find problem in the DRC section of the old magic tech file for the skywater process and fix 
  them.

## 1. Clone custom inverter standard cell design from github repository

```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vaiinv.mag &
```

***2.Load the custom inverter layout in magic and explore.***

Screenshot of custom inverter layout in magic

![Screenshot 2024-11-14 114841](https://github.com/user-attachments/assets/122fa962-888c-4291-9147-f16154908085)

![Screenshot 2024-11-14 115506](https://github.com/user-attachments/assets/f73cb902-7be6-4a43-9245-4068770393c4)


NMOS and PMOS identified

![Screenshot 2024-11-13 112131](https://github.com/user-attachments/assets/4b820177-0312-46db-9dbc-6c6b241bb06d)


![Screenshot 2024-11-13 112301](https://github.com/user-attachments/assets/358ca3b8-8257-434e-8ca9-e2b5b4d0fb50)

Output Y connectivity to PMOS and NMOS drain verified

![Screenshot 2024-11-14 121142](https://github.com/user-attachments/assets/147a301c-3c2a-4ca2-a87b-20cb1fb7388f)



PMOS source connectivity to VDD (here VPWR) verified

![Screenshot 2024-11-14 121240](https://github.com/user-attachments/assets/352ebfb9-0781-4da5-9367-0ef68cec13d3)


NMOS source connectivity to VSS (here VGND) verified

![Screenshot 2024-11-14 121324](https://github.com/user-attachments/assets/d8afedb5-7400-4b77-b75d-667540ad2fa3)


Deleting necessary layout part to see DRC error


![Screenshot 2024-11-13 120003](https://github.com/user-attachments/assets/9da3f8a1-d6b9-45ff-a532-4090ff983165)

***3.Spice extraction of inverter in magic.***

Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic

```
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```

Screenshot of tkcon window after running above commands

![Screenshot 2024-11-14 121558](https://github.com/user-attachments/assets/4546a136-74fb-4f17-94d5-07543da5c1a0)


Screenshot of created spice file

![Screenshot 2024-11-14 121808](https://github.com/user-attachments/assets/227da811-e527-4735-8b94-c275063cbe69)

![Screenshot 2024-11-14 121745](https://github.com/user-attachments/assets/286dde20-fd3b-4613-9a3a-c7c2b7ec1440)


***4. Editing the spice model file for analysis through simulation.***

Measuring unit distance in layout grid

![Screenshot 2024-11-14 121945](https://github.com/user-attachments/assets/08efd25a-a095-4d18-abf7-e758a79b432b)


Final edited spice file ready for ngspice simulation

![Screenshot 2024-11-14 122323](https://github.com/user-attachments/assets/bd465aa6-387f-49c3-8094-abfafab75723)


***5.Post-layout ngspice simulations.***

Commands for ngspice simulation

```
# Command to directly load spice file for simulation to ngspice
ngspice sky130_vaiinv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a

```

Screenshots of ngspice run

![Screenshot 2024-11-14 122539](https://github.com/user-attachments/assets/bc07e154-27c0-4655-9e1c-01acceef37ec)


Screenshot of generated plot

![Screenshot 2024-11-14 122614](https://github.com/user-attachments/assets/ae24667d-7028-43d7-a4fd-44e6b01fff46)


Rise transition time calculation Rise Transition Time = Time taken for output to rise to 80% − Time taken for output to rise to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots

![Screenshot 2024-11-14 122654](https://github.com/user-attachments/assets/a2824a3e-957e-495c-87bc-84ca6329cd63)

![Screenshot 2024-11-13 144355](https://github.com/user-attachments/assets/847feee7-d87e-4b94-9a35-187bfcc1f3f9)

80% Screenshots

![Screenshot 2024-11-14 123014](https://github.com/user-attachments/assets/c0b107d7-58e6-4956-a630-44cb66763286)

![Screenshot 2024-11-13 144801](https://github.com/user-attachments/assets/0e488de3-0610-4a96-a5b9-ad1c3d2eafbf)

```
Rise Transition Time = 2.2389 - 2.1792 = 0.0597 ns = 59.70 ps
```

Fall Transition Time = Time taken for output to fall to 80% − Time taken for output to fall to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots

![Screenshot 2024-11-14 123044](https://github.com/user-attachments/assets/e33a0ed8-7726-4797-829b-5f0cd4ef5d1a)


![Screenshot 2024-11-13 145741](https://github.com/user-attachments/assets/7786b21c-8eea-4c98-ada4-60c1321ebc07)

80% Screenshots

![Screenshot 2024-11-14 123111](https://github.com/user-attachments/assets/279c1d2e-ed5d-48ae-8df8-4dccac6186ea)


```
Fall Transition Time = 4.0931 - 4.05 = 0.0431 ns = 43.10 ps
```

Rise Cell Delay Calculation Rise cell delay = Time taken by output to rise to 50% − Time taken by input to fall to 50% 50 % of 3.3V = 1.65V

50% Screenshots


![Screenshot 2024-11-14 123138](https://github.com/user-attachments/assets/2c2fc080-a4df-4553-9595-e1ec6561c779)


![Screenshot 2024-11-13 150539](https://github.com/user-attachments/assets/21c30a73-8da9-40f1-bad2-0d82202916a8)

```
Rise cell delay = 2.20787 - 2.14944 = 0.05843 ns = 58.43 ps
```
Fall Cell Delay Calculation Fall cell delay = Time taken by output to fall to 50% − Time taken by input to rise to 50% 50 % of 3.3V = 1.65V

50% Screenshots

![Screenshot 2024-11-14 123201](https://github.com/user-attachments/assets/28d42dd3-d9da-442a-b55d-c17fae21f3ed)


![Screenshot 2024-11-13 151323](https://github.com/user-attachments/assets/e539f012-4e4a-41c9-8fa0-94043b0d6964)

```
Fall cell delay = 4.07656 - 4.04844 = 0.02818 ns = 28.12 ps
```

***6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.***

Link to Sky130 Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &

```

Screenshots of commands run

![Screenshot 2024-11-13 152210](https://github.com/user-attachments/assets/625ecad7-dc51-4a58-9f47-f96c5b3d42cd)

![Screenshot 2024-11-13 152229](https://github.com/user-attachments/assets/64abf6ce-17d7-4d77-b503-f4a08aead20b)

Screenshot of .magicrc file

![Screenshot 2024-11-13 152323](https://github.com/user-attachments/assets/b202d7ee-5956-4cf7-a167-161608621f8e)

Incorrectly implemented poly.9 simple rule correction

Screenshot of poly rules

![Screenshot 2024-11-13 152501](https://github.com/user-attachments/assets/4356b64e-bbcc-4cea-bbf3-c67b7c1255c2)


Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u

![Screenshot 2024-11-13 153123](https://github.com/user-attachments/assets/3b846e57-b91f-41e7-98c7-04338bfac4d1)


![Screenshot 2024-11-13 155239](https://github.com/user-attachments/assets/1f3cabc9-359b-46b6-9e36-9d68da396df8)

New commands inserted in sky130A.tech file to update drc


![Screenshot 2024-11-13 160118](https://github.com/user-attachments/assets/80e27ecb-15c7-4c9c-876d-a46c8434916c)


![Screenshot 2024-11-13 160910](https://github.com/user-attachments/assets/45cf6f6d-4642-49c8-a18d-a4a66f766e3d)

Commands to run in tkcon window

```
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented


![Screenshot 2024-11-13 163017](https://github.com/user-attachments/assets/4966ebb7-c48a-482e-8b46-65150fc877a0)

Incorrectly implemented difftap.2 simple rule correction

Screenshot of difftap rules

![Screenshot 2024-11-13 163513](https://github.com/user-attachments/assets/7dfa311c-8408-437e-a361-a9e34c37e656)

Incorrectly implemented -

![Screenshot 2024-11-13 164153](https://github.com/user-attachments/assets/a7e55c52-11ed-448c-bba0-70913f67f26b)

Commands to run in tkcon window

```
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented showing ```no errors found```

![Screenshot 2024-11-13 161945](https://github.com/user-attachments/assets/3187c11f-9ee7-46a5-b372-b63757bc8691)


</details>

<details>
 <summary> Day-4 </summary>

## Pre-Layout timing analysis and Importance of good clock tree:


Implementation

Section 4 tasks:-

1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.


***1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.***

Conditions to be verified before moving forward with custom designed cell layout:

Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.

Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.

Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.


Commands to open the custom inverter layout.

```
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vaiinv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd

![Screenshot 2024-11-13 182739](https://github.com/user-attachments/assets/c534402b-a43e-48fd-a5f1-f894f82acba2)


Commands for tkcon window to set grid as tracks of locali layer
```
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```

Screenshot of commands run

![Screenshot 2024-11-14 234316](https://github.com/user-attachments/assets/11b0d053-bf66-4760-b420-3ce313f43ac6)



Condition 1 verified

![Screenshot 2024-11-14 234359](https://github.com/user-attachments/assets/4bc12781-df58-4463-a72f-7f0e706bc96b)


Condition 2 verified

Horizontal track pitch = 0.46um


![Screenshot 2024-11-14 234610](https://github.com/user-attachments/assets/edb53cfa-0301-4d61-a131-de93adedfae5)


width of standard cell = 1.38 um = 0.46*3

Condition 3 verified


Vertical track pitch = 0.34um

![Screenshot 2024-11-14 234758](https://github.com/user-attachments/assets/22a89745-4588-4d95-a8b8-34d6e13a457b)


width of standard cell = 2.72 um = 0.34*3

***2. Save the finalized layout with custom name and open it.***


Command for tkcon window to save the layout with custom name


```
# Command to save as
save sky130_vaiinv.mag

```

![Screenshot 2024-11-13 185311](https://github.com/user-attachments/assets/eff94435-7323-4395-b6c7-ebaa07b41e60)

Command to open the newly saved layout

```
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vaiinv.mag &
```

![Screenshot 2024-11-13 190818](https://github.com/user-attachments/assets/000f5e34-6192-4079-9bbf-2b7d3e1186f7)


Screenshot of newly saved layout


![Screenshot 2024-11-13 185655](https://github.com/user-attachments/assets/d0b61e23-7dd4-4f54-a200-a73e38b7febe)

***3. Generate lef from the layout.***

Command for tkcon window to write lef


```
# lef command
lef write
```

Screenshot of command run


![Screenshot 2024-11-13 185805](https://github.com/user-attachments/assets/59163ec7-2588-4abf-aefd-76f214747ed0)

Screenshot of newly created lef file

![Screenshot 2024-11-13 190052](https://github.com/user-attachments/assets/c03cce03-a311-463a-800f-f69419a88471)


***4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.***

Commands to copy necessary files to 'picorv32a' design 'src' directory
```
# Copy lef file
cp sky130_vaiinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

```

Screenshot of commands run


![Screenshot 2024-11-13 190818](https://github.com/user-attachments/assets/cfd9232c-14d2-4dcd-b2a8-5affde633fe4)

***5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.***

Commands to be added to config.tcl to include our custom cell in the openlane flow

```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory


![Screenshot 2024-11-13 192051](https://github.com/user-attachments/assets/002ebf3f-d6cc-4896-805b-4c3bce29c2a6)

***6. Run openlane flow synthesis with newly inserted custom inverter cell.***

Commands to invoke the OpenLANE flow include new lef and perform synthesis
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run

![Screenshot 2024-11-13 194908](https://github.com/user-attachments/assets/3c373a89-6548-4aa4-90ac-8e20d67e6644)


![Screenshot 2024-11-13 195207](https://github.com/user-attachments/assets/3aa211eb-c2ac-46b9-8648-02412215268c)

***7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.***

Noting down current design values generated before modifying parameters to improve timing

![Screenshot 2024-11-13 195325](https://github.com/user-attachments/assets/63827941-448d-4cbd-b7c3-d43be02ff272)

![Screenshot 2024-11-13 205253](https://github.com/user-attachments/assets/1d936cc7-d7ae-4dc9-a4ea-d6a6f35bbddb)

Commands to view and change parameters to improve timing and run synthesis

```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 13-11_15-20 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

```

Screenshot of merged.lef in tmp directory with our custom inverter as macro


![Screenshot 2024-11-13 205918](https://github.com/user-attachments/assets/083a90b1-e070-40e4-a955-cf0bfe085a28)


Screenshots of commands run


![Screenshot 2024-11-13 212034](https://github.com/user-attachments/assets/d9d8cf38-44da-4829-a74f-93d59f2576b2)


![Screenshot 2024-11-13 212440](https://github.com/user-attachments/assets/73245899-b7e3-424c-8d1c-d450d4a795f9)

Comparing to previously noted run values area has increased and worst negative slack has become 0


![Screenshot 2024-11-13 212453](https://github.com/user-attachments/assets/895e801a-46eb-43c5-88fb-a2b31f253a2a)

![Screenshot 2024-11-13 212506](https://github.com/user-attachments/assets/429f5353-15c2-4673-89c9-9aa2d133c785)


***8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.***

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```
# Now we can run floorplan
run_floorplan
```

![Screenshot 2024-11-13 212540](https://github.com/user-attachments/assets/98c43549-8e94-41ad-a7e3-c816cc77b4b2)


![Screenshot 2024-11-13 212741](https://github.com/user-attachments/assets/ba5c4083-7b95-476d-afd6-6bfa820f7ab3)

Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands available based on information from Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl and also based on Floorplan Commands section in Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md


```
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```

Screenshots of commands run



![Screenshot 2024-11-13 212837](https://github.com/user-attachments/assets/be921242-89e4-4c4b-aec3-ba00cffde422)

![Screenshot 2024-11-13 212918](https://github.com/user-attachments/assets/068369da-d98f-4cf5-afb7-1f7198c9b3a4)


![Screenshot 2024-11-13 212933](https://github.com/user-attachments/assets/4e5d2ad8-c0b5-46d8-9aa5-6f6be3c1ac8e)

Now that floorplan is done we can do placement using following command
```
# Now we are ready to run placement
run_placement
```
Screenshots of command run

![Screenshot 2024-11-13 212956](https://github.com/user-attachments/assets/19c2b2a1-f56b-4a58-87a7-120b2cd09f64)

![Screenshot 2024-11-13 213228](https://github.com/user-attachments/assets/4616ff71-ddb2-4f37-b660-1130d2f58fcf)


Commands to load placement def in magic in another terminal

```
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_15-20/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

```

Screenshot of placement def in magic

![Screenshot 2024-11-13 213602](https://github.com/user-attachments/assets/3a2feee4-64e8-4f77-a63c-8058b3000aab)


![myinv_vaiinv](https://github.com/user-attachments/assets/ad1599d7-1398-4cb4-89b2-c1b00bcc5bbd)


![Screenshot 2024-11-13 223839](https://github.com/user-attachments/assets/d7b4f291-ac8d-4cde-929b-991d25e71cf2)

***9. Do Post-Synthesis timing analysis with OpenSTA tool.***

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot


![Screenshot 2024-11-13 232119](https://github.com/user-attachments/assets/2bd92bac-dede-4a46-960d-c07dd98c7401)


Newly created pre_sta.conf for STA analysis in openlane directory

![Screenshot 2024-11-13 234401](https://github.com/user-attachments/assets/9bd09e6d-0730-46ac-ba8b-0ea68fabcdc5)


Newly created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory based on the file openlane/scripts/base.sdc

![Screenshot 2024-11-13 234353](https://github.com/user-attachments/assets/627cfc85-503c-4d2c-9388-4ad5d55d6385)


Commands to run STA in another terminal
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf

```

Screenshots of commands run


![Screenshot 2024-11-13 235308](https://github.com/user-attachments/assets/31cea7b1-a64b-4661-9766-a571bf7929e2)


![Screenshot 2024-11-13 235329](https://github.com/user-attachments/assets/f572f672-9292-43ed-aeed-ee297dfee11d)

![Screenshot 2024-11-13 235359](https://github.com/user-attachments/assets/9f16898b-5419-4bad-a9b1-95a6dbe2747c)


![Screenshot 2024-11-13 235434](https://github.com/user-attachments/assets/fd41708c-5631-4b0b-a17f-8dfffaebbc30)


Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis
```
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 13-11_17-48 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot


![Screenshot 2024-11-14 000353](https://github.com/user-attachments/assets/fcd0cf70-d044-4fbf-b4a8-499531690f0e)


Commands to run STA in another terminal
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

![Screenshot 2024-11-14 005613](https://github.com/user-attachments/assets/62ec3738-9ac5-436d-84cf-09f05662e2b4)

![Screenshot 2024-11-14 005626](https://github.com/user-attachments/assets/3907cb29-cb79-4488-a897-939b10728b3c)

![Screenshot 2024-11-14 005634](https://github.com/user-attachments/assets/1fedc301-fd71-4943-8360-cb9043f0aae1)



***10. Make timing ECO fixes to remove all violations.***

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot 2024-11-14 005701](https://github.com/user-attachments/assets/13c4e33e-0c27-485a-b8a0-81817f79a2e0)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot 2024-11-14 005827](https://github.com/user-attachments/assets/a37903a6-ae30-4e1f-8f23-3e2882329e58)


![Screenshot 2024-11-14 005855](https://github.com/user-attachments/assets/25b6b2ea-8b9b-42ca-b2e3-da27b617b268)


![Screenshot 2024-11-14 005918](https://github.com/user-attachments/assets/0c8b2793-3d61-439c-9879-830b5e39a262)


OR gate of drive strength 2 is driving 4 fanouts

![Screenshot 2024-11-14 010017](https://github.com/user-attachments/assets/ded1c68c-15b6-4e46-976c-61fc11d72ee2)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
Result - slack reduced

```

![Screenshot 2024-11-14 010208](https://github.com/user-attachments/assets/fe962a77-669b-4c23-839f-044f5b960acc)

![Screenshot 2024-11-14 010231](https://github.com/user-attachments/assets/efb43b77-9672-402b-8289-82c2bc34df21)

![Screenshot 2024-11-14 010253](https://github.com/user-attachments/assets/b1f89bef-d6db-4e9d-8ce2-ce2dadaf9235)

OR gate of drive strength 2 driving OA gate has more delay



![Screenshot 2024-11-14 010327](https://github.com/user-attachments/assets/b498777f-587e-441b-8716-20fb5877b661)


Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11643_

# Replacing cell
replace_cell _14481_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot 2024-11-14 010431](https://github.com/user-attachments/assets/955ce6e0-3d3f-411f-89cf-4737ef247000)

![Screenshot 2024-11-14 010457](https://github.com/user-attachments/assets/0f5cc396-9583-4165-b57b-74d7ff64325d)


OR gate of drive strength 2 driving OA gate has more delay


![Screenshot 2024-11-14 010531](https://github.com/user-attachments/assets/4eb2ca33-b089-41f2-9dde-375e768f4348)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot 2024-11-14 010644](https://github.com/user-attachments/assets/0aec21c4-ed79-4b61-ad4a-9f960f2d9de8)


![Screenshot 2024-11-14 010659](https://github.com/user-attachments/assets/637b28ca-701f-4f92-8ff7-f4da7e8287d8)

Commands to verify instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
```
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```

Screenshot of replaced instance


![Screenshot 2024-11-14 010808](https://github.com/user-attachments/assets/3ce89ea8-6dd8-4ecb-95b3-ed0db905b88f)


We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation

***11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.***

Now to insert this updated netlist to PnR flow and we can use write_verilog and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist
```
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_19-21/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run


![Screenshot 2024-11-14 011433](https://github.com/user-attachments/assets/34dbdf9a-612c-4810-9868-71893fe1ba8a)


Commands to write verilog
```
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_19-21/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```
Screenshot of commands run

![Screenshot 2024-11-14 011715](https://github.com/user-attachments/assets/08a44e8a-90fd-48fb-b100-5a28943dceb9)

Verified that the netlist is overwritten by checking that instance _14506_ is replaced with sky130_fd_sc_hd__or4_4

![Screenshot 2024-11-14 011831](https://github.com/user-attachments/assets/d4d13658-3a7b-4150-9752-3674d9df8b58)


Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages
```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 25-03_18-52 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

```

Screenshots of commands run

![Screenshot 2024-11-14 012733](https://github.com/user-attachments/assets/14f4138a-7e06-43ca-9bcb-34a98fabe957)

![Screenshot 2024-11-14 013329](https://github.com/user-attachments/assets/d9810afa-f821-4134-a3bd-b360656a472a)


![Screenshot 2024-11-14 013840](https://github.com/user-attachments/assets/7597a7a9-522e-48e7-9db8-454fc9c9c62e)

***12. Post-CTS OpenROAD timing analysis.***

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/13-11_19-21/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/13-11_19-21/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/13-11_19-21/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![Screenshot 2024-11-14 014917](https://github.com/user-attachments/assets/4c2826dc-3cd2-4954-adfc-c8b69f46e512)

![Screenshot 2024-11-14 015034](https://github.com/user-attachments/assets/fc02c7f2-edb6-4f81-bbf2-431eeb6c8315)


13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.
Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing CTS_CLK_BUFFER_LIST

```
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/13-11_19-21/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/13-11_19-21/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/13-11_19-21/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/13-11_19-21/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

```

Screenshots of commands run and timing report generated

![Screenshot 2024-11-14 022316](https://github.com/user-attachments/assets/7133f4e2-d26c-4cae-9de9-84085a2dcab5)

![Screenshot 2024-11-14 022413](https://github.com/user-attachments/assets/916b4afb-ee72-48c2-9ca2-c15485296e35)

![Screenshot 2024-11-14 022624](https://github.com/user-attachments/assets/0c6445e3-ed5f-4d0b-bcdb-d9c602eba7a5)

![Screenshot 2024-11-14 022640](https://github.com/user-attachments/assets/2887ebb4-b70d-46cb-a6c9-46559772c040)

![Screenshot 2024-11-14 022956](https://github.com/user-attachments/assets/3a5bf061-2fdc-4731-9cbb-f5c79b5969b1)

</details>

<details>
 <summary> Day-5 </summary>

Final steps for RTL2GDS using tritonRoute and openSTA

## Theory

Implementation

Tasks:-

1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
2. Perfrom detailed routing using TritonRoute.
3. Post-Route parasitic extraction using SPEF extractor.
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

***1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.***

Commands to perform all necessary stages up until now
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 

```

Screenshots of power distribution network run

![Screenshot 2024-11-14 023535](https://github.com/user-attachments/assets/f65fb3d8-5c19-47a4-9d95-936256b93851)


![Screenshot 2024-11-14 024311](https://github.com/user-attachments/assets/d937d9a5-a2ba-49ba-b4fc-f0dec8adcb96)

Commands to load PDN def in magic in another terminal

```
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_21-04/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &

```

![Screenshot 2024-11-14 024724](https://github.com/user-attachments/assets/1e3d063e-418a-4e30-bf70-f48937f293fd)


Screenshots of PDN def


![Screenshot 2024-11-14 024736](https://github.com/user-attachments/assets/94b95231-700e-4b86-8b39-06655973cd48)


![Screenshot 2024-11-14 025559](https://github.com/user-attachments/assets/d5a7e5b4-e663-46cc-a13e-b4bc6826146a)

![Screenshot 2024-11-14 025709](https://github.com/user-attachments/assets/d4fa6285-e6ac-4529-a7d9-f777524b7a77)


2. Perfrom detailed routing using TritonRoute and explore the routed layout.
   
Command to perform routing
```
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing

```

Screenshots of routing run


![Screenshot 2024-11-14 025929](https://github.com/user-attachments/assets/57fe803c-987f-45e0-a150-c952e3a57c9b)

![Screenshot 2024-11-14 031351](https://github.com/user-attachments/assets/4d77e761-947c-4606-93ae-4f9c64d06d3f)

![Screenshot 2024-11-14 031416](https://github.com/user-attachments/assets/942c3c48-a2b0-469f-a7d6-a429c205f179)


Commands to load routed def in magic in another terminal

```
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_21-04/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &

```


![Screenshot 2024-11-14 031838](https://github.com/user-attachments/assets/d2325678-8063-4b5b-957b-f5a56bf7ac52)

Screenshots of routed def


![Screenshot 2024-11-14 031903](https://github.com/user-attachments/assets/22219c99-8c99-42a1-a6e9-d905570f92cb)

![Screenshot 2024-11-14 031931](https://github.com/user-attachments/assets/2948dce1-b2f1-4f24-a9ed-0dd82b4b1c50)

![Screenshot 2024-11-14 032035](https://github.com/user-attachments/assets/cb640963-cbe5-4a9e-9aa7-33bc4d94a702)


Screenshot of fast route guide present in openlane/designs/picorv32a/runs/26-03_08-45/tmp/routing directory


![Screenshot 2024-11-14 032420](https://github.com/user-attachments/assets/cd797fdc-6171-4327-a63d-b5324886e6a5)


4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.
Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in

```
OpenROAD

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated


![Screenshot 2024-11-14 033355](https://github.com/user-attachments/assets/0c31aba2-2a4e-452f-b7c8-5e6c050fc37f)


![Screenshot 2024-11-14 033403](https://github.com/user-attachments/assets/5d52a2c3-b00f-4615-9cb0-83b88801c4e9)

![Screenshot 2024-11-14 033413](https://github.com/user-attachments/assets/3a11b2ea-36c5-451d-adad-f157144ea99a)

![Screenshot 2024-11-14 033425](https://github.com/user-attachments/assets/f1b3baee-0c57-47c7-b5f3-167e2cb20a2c)


</details>

</details>

<details>
 <summary>TASK-13 </summary>

# OpenROAD PHYSICAL DESIGN

***OpenROAD : Integrated Chip Physical Design Tool***

OpenROAD is a comprehensive tool for integrated chip physical design, enabling a seamless transition from RTL to GDSII. It encompasses key stages of chip design, including synthesis, floorplanning, placement, routing, parasitic extraction, and timing analysis.

Designed to minimize wire length using hierarchical placement algorithms, OpenROAD provides optimization features for both timing and power. Its modular architecture supports extensibility, allowing users to integrate custom algorithms and features.


***OpenROAD Flow Controllers***

The OpenROAD project offers two primary flow controllers:

1. OpenROAD-flow-scripts (ORFS)
ORFS is a flow controller that provides a collection of open-source tools for automated digital ASIC design, enabling a fully automated RTL-to-GDSII design flow. Key features include:

Stages: Synthesis, Placement and Routing (PnR), Static Timing Analysis (STA), Design Rule Check (DRC), and Layout Versus Schematic (LVS).
Flexibility: Supports customization, allowing users to combine and configure tools based on project needs.
Physical Design Plugin: Integrates OpenROAD as a plugin for physical design, offering advanced features such as hierarchical placement, global routing, and detailed routing optimization.
PDK Support: Compatible with several public and private PDKs (under NDA). Publicly available PDKs include GF180, Skywater130, and ASAP7.


2. OpenLane
OpenLane, developed by Efabless, is another automated RTL-to-GDSII flow similar to ORFS. It is tailored for the Skywater130 MPW Program.


***High-Level ORFS Process (RTL to GDSII)***


Below is a brief overview of the stages in the ORFS flow:

1. Configuration
Customize the framework to meet specific project requirements.
Define design parameters such as the target technology node, constraints, and tool settings.
2. Design Entry
Input design files in formats like Verilog.
Prepare design sources for further processing.
3. Synthesis
Convert RTL into a gate-level netlist using tools like Yosys and ABC.
4. Floorplanning
Determine the placement of design modules within the chip area.
Tools: RePlAce, Capo.
5. Placement
Precisely position each gate or cell in the chip area.
Tool: OpenROAD.
6. Routing
Connect gates and cells using metal wires to form a complete circuit.
Tools: FastRoute, TritonRoute.
7. Layout Verification
Verify the correctness of the layout using tools like Magic.
8. GDSII Generation
Generate the final GDSII layout file using tools like Magic and KLayout.


***Installation and setting up ORFS***


***Clone and Install Dependencies***

```
mkdir OpeRoad
cd OpenRoad
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts .
sudo ./setup.sh
```

***Build***

```
./build_openroad.sh --local
```

***Verify Installation***

```
cd flow
make
make gui_final
```

![Screenshot 2024-11-24 212546](https://github.com/user-attachments/assets/0eaab0bb-aff7-455c-991a-add0ad3e4ed0)



![Screenshot 2024-11-24 212613](https://github.com/user-attachments/assets/4380371a-91b7-41c6-a917-d21603c210c1)



![Screenshot 2024-11-24 212710](https://github.com/user-attachments/assets/88c2288e-d5db-4e1d-942e-41214583c5f8)


***Makefile***




![Screenshot 2024-11-25 232457](https://github.com/user-attachments/assets/4eb63519-3a5b-4531-8806-57e7e64b6ec6)

![Screenshot 2024-11-25 232509](https://github.com/user-attachments/assets/a1573744-24da-4224-9b57-6d59780823f9)


![Screenshot 2024-11-25 232522](https://github.com/user-attachments/assets/73755fd7-fcc5-4201-9529-a1dc4645bb03)


![Screenshot 2024-11-25 232531](https://github.com/user-attachments/assets/8c717b4a-406c-4f1e-a0dc-31cd7b2dfcdf)

![Screenshot 2024-11-25 232552](https://github.com/user-attachments/assets/955b4155-eaa4-4504-8561-61a6c5218097)

![Screenshot 2024-11-25 232610](https://github.com/user-attachments/assets/207e032e-72e3-44df-a159-e2b87510f079)


![Screenshot 2024-11-25 232621](https://github.com/user-attachments/assets/96912af0-a0bb-4f7a-9656-122c546a4116)

The designs library has different examples for RTL to GDS flow across different technology nodes.
Platforms directory has different technology node libraries, lib files, GDS,etc. The ORFS automated flow has been defined inside the platforms directory

Automated RTL2GDS Flow for VSDBabySoC:

Initial Steps:

We need to create a directory vsdbabysoc inside OpenROAD-flow-scripts/flow/designs/sky130hd
Now create a directory vsdbabysoc inside OpenROAD-flow-scripts/flow/designs/src and include all the verilog files here.
Now copy the folders gds, include, lef and lib from the VSDBabySoC folder in your system into this directory.
The gds folder would contain the files avsddac.gds and avsdpll.gds
The include folder would contain the files sandpiper.vh, sandpiper_gen.vh, sp_default.vh and sp_verilog.vh
The gds folder would contain the files avsddac.lef and avsdpll.lef
The lib folder would contain the files avsddac.lib and avsdpll.lib
Now copy the constraints file(vsdbabysoc_synthesis.sdc) from the VSDBabySoC folder in your system into this directory.
Now copy the files(macro.cfg and pin_order.cfg) from the VSDBabySoC folder in your system into this directory.

Now, create a config.mk file whose contents are shown below:

![Screenshot 2024-11-25 233810](https://github.com/user-attachments/assets/dcd89da8-69f8-4119-b3f0-f004f3751546)

```
export DESIGN_NICKNAME = vsdbabysoc
export DESIGN_NAME = vsdbabysoc
export PLATFORM    = sky130hd

# export VERILOG_FILES_BLACKBOX = $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/IPs/*.v
# export VERILOG_FILES = $(sort $(wildcard $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/*.v))
# Explicitly list the Verilog files for synthesis
export VERILOG_FILES = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/vsdbabysoc.v \
                       /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/module/rvmyth.v \
                       /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/clk_gate.v

export SDC_FILE      = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/sdc/vsdbabysoc_synthesis.sdc

#export DIE_AREA   = 0 0 1500 1500
# export CORE_AREA  = 10 10 2910 3510

# export PLACE_DENSITY ?= 0.23

export vsdbabysoc_DIR = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc

export VERILOG_INCLUDE_DIRS = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/include

# export SDC_FILE      = $(wildcard $(vsdbabysoc_DIR)/sdc/*.sdc)
export ADDITIONAL_GDS  =/home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/gds
export ADDITIONAL_LEFS  = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/lef

export ADDITIONAL_LIBS = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/lib/avsddac.lib \
             /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/src/lib/avsdpll.lib
# Clock Configuration (vsdbabysoc specific)
# export CLOCK_PERIOD = 20.0
export CLOCK_PORT = CLK
export CLOCK_NET = $(CLOCK_PORT)

# Floorplanning Configuration (vsdbabysoc specific)
export FP_PIN_ORDER_CFG = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/pin_order.cfg
export FP_SIZING = absolute
export DIE_AREA = 0 0 2000 2000
export CORE_AREA = 10 10 1800 1800


# export PL_RESIZER_HOLD_MAX_BUFFER_PERCENT = 80
# export PL_RESIZER_HOLD_MAX_BUFFER_COUNT = 5000  # Set the buffer limit to a higher value if needed
# export GLB_RESIZER_HOLD_MAX_BUFFER_PERCENT = 80

# Hold Slack Margin Configuration
# export PL_RESIZER_HOLD_SLACK_MARGIN = 0.01
# export GLB_RESIZER_HOLD_SLACK_MARGIN = 0.01


export BOTTOM_MARGIN_MULT = 50
export TOP_MARGIN_MULT = 50
export LEFT_MARGIN_MULT = 200
export RIGHT_MARGIN_MULT = 200

# Placement Configuration (vsdbabysoc specific)
export MACRO_PLACEMENT_CFG = /home/vaibhav2000/OpenRoad/flow/designs/sky130hd/vsdbabysoc/macro.cfg

# Magic Tool Configuration
export MAGIC_ZEROIZE_ORIGIN = 0
export MAGIC_EXT_USE_GDS = 1

export SYNTH_HIERARCHICAL = 1

# export RTLMP_BOUNDARY_WT = 0
#  MACRO_PLACE_HALO = 100 100
# export MACRO_PLACE_CHANNEL = 200 200

# CTS tuning
# export CTS_BUF_DISTANCE = 600
# export SKIP_GATE_CLONING = 1

# export SETUP_SLACK_MARGIN = 0.2

# This is high, some SRAMs should probably be converted
# to real SRAMs and not instantiated as flops
# export SYNTH_MEMORY_MAX_BITS ?= 42000

```

***Commands for synthesis:***

```
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk synth
```

![Screenshot 2024-11-25 171819](https://github.com/user-attachments/assets/c7371235-1917-4f70-b8a2-ce5894529892)


Synthesis netlist:


![Screenshot 2024-11-26 021841](https://github.com/user-attachments/assets/39cafccf-c209-4eaf-8b28-64587f3a4efd)



Synthesis log:


![Screenshot 2024-11-25 155146](https://github.com/user-attachments/assets/bc38c2c7-2415-4e2d-b150-d28b205cd9c6)

Synthesis Check:

![Screenshot 2024-11-26 045001](https://github.com/user-attachments/assets/165e26a5-5354-4f9c-80fa-e23bba2ac74f)


Synthesis Stats:


![Screenshot 2024-11-26 044521](https://github.com/user-attachments/assets/e337d3e2-7ef0-42b9-94bb-66b32b0bd834)



![Screenshot 2024-11-26 044609](https://github.com/user-attachments/assets/33099688-2f91-4f1c-84eb-5c6161dbdcb1)

![Screenshot 2024-11-26 044636](https://github.com/user-attachments/assets/19fee150-776f-4235-91fd-ba4f3fb543ec)



Commands for floorplan:

```
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk floorplan
```

![Screenshot 2024-11-25 172031](https://github.com/user-attachments/assets/73ea3727-4c19-44fd-87a1-ab19d2209c4b)



![Screenshot 2024-11-25 172116](https://github.com/user-attachments/assets/b9c4d18f-e2be-4882-8440-3ff2064a8275)


![Screenshot 2024-11-25 173614](https://github.com/user-attachments/assets/1a439b3e-cc30-4a3d-a950-4fee5234d422)


***OpenROAD GUI And Review Logs For Synthesis, Floorplan and Init STA***

We use the below command and get the following result to observe the floorplanning

```
make gui_floorplan

```

![Screenshot 2024-11-25 173632](https://github.com/user-attachments/assets/99c6fdef-6fe5-4b88-8863-3dcbb1edc0b2)

![Screenshot 2024-11-26 122037](https://github.com/user-attachments/assets/d2856c64-2234-4c66-9baa-974fde8c2e7e)



The command to see the floorplanning is as follows and we get the following layout

```
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk gui_floorplan
```


![Screenshot 2024-11-25 174937](https://github.com/user-attachments/assets/7d225fb7-b17b-478c-b162-a8a64ace0689)


![Screenshot 2024-11-26 040627](https://github.com/user-attachments/assets/21e6a3be-4f9f-4dde-819e-4768ea805445)




![Screenshot 2024-11-26 040704](https://github.com/user-attachments/assets/e104cf54-51b1-4852-a0a8-d715386e7bf0)


![Screenshot 2024-11-26 042852](https://github.com/user-attachments/assets/e4ea2675-9cf6-44d8-a7a4-6097bc3c3c24)

![Screenshot 2024-11-26 042914](https://github.com/user-attachments/assets/5aad399d-1743-4b16-959a-40fd9cb27c1a)


![Screenshot 2024-11-26 043004](https://github.com/user-attachments/assets/f5be8a13-a929-43f0-b502-c684aec816b3)


![Screenshot 2024-11-26 043026](https://github.com/user-attachments/assets/137686c3-cdee-4873-9ad0-54ed31870d26)





***FLOORPLAN TIMING REPORT***


![Screenshot 2024-11-26 044155](https://github.com/user-attachments/assets/c738a011-19a0-4632-a6f3-2eb1ef36d6c4)

```

==========================================================================
floorplan final report_tns
--------------------------------------------------------------------------
tns 0.00

==========================================================================
floorplan final report_wns
--------------------------------------------------------------------------
wns 0.00

==========================================================================
floorplan final report_worst_slack
--------------------------------------------------------------------------
worst slack INF

==========================================================================
floorplan final report_checks -path_delay min
--------------------------------------------------------------------------
No paths found.

==========================================================================
floorplan final report_checks -path_delay max
--------------------------------------------------------------------------
No paths found.

==========================================================================
floorplan final report_checks -unconstrained
--------------------------------------------------------------------------
Startpoint: core.CPU_reset_a3$_DFF_P_ (rising edge-triggered flip-flop)
Endpoint: core.CPU_Xreg_value_a4[10][13]$_SDFFE_PP0P_
          (rising edge-triggered flip-flop)
Path Group: unconstrained
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                  0.00    0.00    0.00 ^ core.CPU_reset_a3$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
   591    1.46   13.42    9.67    9.67 ^ core.CPU_reset_a3$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                         core.CPU_reset_a3 (net)
                 13.42    0.00    9.67 ^ _10124_/A (sky130_fd_sc_hd__inv_1)
   464    1.04    0.00   21.17   30.85 v _10124_/Y (sky130_fd_sc_hd__inv_1)
                                         _04513_ (net)
                  0.00    0.00   30.85 v _10227_/A (sky130_fd_sc_hd__nand3_1)
    31    0.08    0.78    0.52   31.37 ^ _10227_/Y (sky130_fd_sc_hd__nand3_1)
                                         _04613_ (net)
                  0.78    0.00   31.37 ^ _10232_/B1 (sky130_fd_sc_hd__o221ai_1)
     1    0.00    0.20    0.22   31.59 v _10232_/Y (sky130_fd_sc_hd__o221ai_1)
                                         _00548_ (net)
                  0.20    0.00   31.59 v core.CPU_Xreg_value_a4[10][13]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                 31.59   data arrival time
-----------------------------------------------------------------------------
(Path is unconstrained)



==========================================================================
floorplan final report_power
--------------------------------------------------------------------------
Group                  Internal  Switching    Leakage      Total
                          Power      Power      Power      Power (Watts)
----------------------------------------------------------------
Sequential             7.92e-12   3.67e-12   1.45e-08   1.45e-08  58.0%
Combinational          1.01e-11   1.77e-11   1.04e-08   1.05e-08  42.0%
Clock                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
----------------------------------------------------------------
Total                  1.80e-11   2.13e-11   2.49e-08   2.49e-08 100.0%
                           0.1%       0.1%      99.8%

```

#For Placement

```

make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk place

```


![Screenshot 2024-11-26 001058](https://github.com/user-attachments/assets/baeea49c-0a01-42bd-b12c-c11225ed8457)



![Screenshot 2024-11-26 001657](https://github.com/user-attachments/assets/9fb6f621-016d-4d0f-99d6-5d731a09c5ab)


```
make gui_place
```

![Screenshot 2024-11-26 001728](https://github.com/user-attachments/assets/3d0c20c8-cfea-49a5-a7ff-ae681727d6f7)


![Screenshot 2024-11-26 051500](https://github.com/user-attachments/assets/61e84dad-3b65-451e-9709-c55a766d98e3)


```



==========================================================================
detailed place report_tns
--------------------------------------------------------------------------
tns 0.00

==========================================================================
detailed place report_wns
--------------------------------------------------------------------------
wns 0.00

==========================================================================
detailed place report_worst_slack
--------------------------------------------------------------------------
worst slack INF

==========================================================================
detailed place report_checks -path_delay min
--------------------------------------------------------------------------
No paths found.

==========================================================================
detailed place report_checks -path_delay max
--------------------------------------------------------------------------
No paths found.

==========================================================================
detailed place report_checks -unconstrained
--------------------------------------------------------------------------
Startpoint: core.CPU_valid_taken_br_a4$_DFF_P_ (rising edge-triggered flip-flop)
Endpoint: core.CPU_Xreg_value_a4[15][18]$_SDFFE_PP0P_
          (rising edge-triggered flip-flop)
Path Group: unconstrained
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                  0.76    0.00    0.00 ^ core.CPU_valid_taken_br_a4$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
     2    0.01    0.04    0.46    0.46 v core.CPU_valid_taken_br_a4$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                         core.CPU_valid_taken_br_a4 (net)
                  0.04    0.00    0.46 v _07913_/B (sky130_fd_sc_hd__or4_4)
    41    0.23    0.36    0.84    1.30 v _07913_/X (sky130_fd_sc_hd__or4_4)
                                         _02930_ (net)
                  0.36    0.02    1.31 v load_slew103/A (sky130_fd_sc_hd__buf_16)
    36    0.28    0.15    0.35    1.66 v load_slew103/X (sky130_fd_sc_hd__buf_16)
                                         net103 (net)
                  0.15    0.01    1.68 v max_cap102/A (sky130_fd_sc_hd__buf_16)
    24    0.27    0.14    0.26    1.94 v max_cap102/X (sky130_fd_sc_hd__buf_16)
                                         net102 (net)
                  0.16    0.04    1.97 v _07915_/A (sky130_fd_sc_hd__clkinv_16)
    43    0.48    0.31    0.25    2.22 ^ _07915_/Y (sky130_fd_sc_hd__clkinv_16)
                                         _02932_ (net)
                  0.37    0.11    2.33 ^ _09981_/C (sky130_fd_sc_hd__nor3_2)
     2    0.02    0.10    0.13    2.46 v _09981_/Y (sky130_fd_sc_hd__nor3_2)
                                         _04371_ (net)
                  0.10    0.00    2.46 v _09982_/B1 (sky130_fd_sc_hd__a21oi_4)
     6    0.10    0.69    0.57    3.02 ^ _09982_/Y (sky130_fd_sc_hd__a21oi_4)
                                         _04372_ (net)
                  0.69    0.00    3.02 ^ _09988_/A2 (sky130_fd_sc_hd__o21ai_4)
    16    0.12    0.32    0.36    3.39 v _09988_/Y (sky130_fd_sc_hd__o21ai_4)
                                         _04378_ (net)
                  0.32    0.00    3.39 v _11217_/A (sky130_fd_sc_hd__nor3_4)
    14    0.11    1.07    0.96    4.35 ^ _11217_/Y (sky130_fd_sc_hd__nor3_4)
                                         _05443_ (net)
                  1.07    0.00    4.35 ^ wire20/A (sky130_fd_sc_hd__buf_8)
    10    0.11    0.19    0.30    4.65 ^ wire20/X (sky130_fd_sc_hd__buf_8)
                                         net20 (net)
                  0.20    0.01    4.66 ^ _11238_/B (sky130_fd_sc_hd__nand2_4)
     5    0.04    0.22    0.13    4.79 v _11238_/Y (sky130_fd_sc_hd__nand2_4)
                                         _05460_ (net)
                  0.22    0.00    4.79 v _11253_/B1 (sky130_fd_sc_hd__o221ai_1)
     1    0.00    0.23    0.23    5.02 ^ _11253_/Y (sky130_fd_sc_hd__o221ai_1)
                                         _00713_ (net)
                  0.23    0.00    5.02 ^ core.CPU_Xreg_value_a4[15][18]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                  5.02   data arrival time
-----------------------------------------------------------------------------
(Path is unconstrained)



==========================================================================
detailed place report_check_types -max_slew -max_cap -max_fanout -violators
--------------------------------------------------------------------------

==========================================================================
detailed place max_slew_check_slack
--------------------------------------------------------------------------
0.06809719651937485

==========================================================================
detailed place max_slew_check_limit
--------------------------------------------------------------------------
1.4951549768447876

==========================================================================
detailed place max_slew_check_slack_limit
--------------------------------------------------------------------------
0.0455

==========================================================================
detailed place max_fanout_check_slack
--------------------------------------------------------------------------
1.0000000150474662e+30

==========================================================================
detailed place max_fanout_check_limit
--------------------------------------------------------------------------
1.0000000150474662e+30

==========================================================================
detailed place max_capacitance_check_slack
--------------------------------------------------------------------------
0.007044170051813126

==========================================================================
detailed place max_capacitance_check_limit
--------------------------------------------------------------------------
0.19410200417041779

==========================================================================
detailed place max_capacitance_check_slack_limit
--------------------------------------------------------------------------
0.0363

==========================================================================
detailed place max_slew_violation_count
--------------------------------------------------------------------------
max slew violation count 0

==========================================================================
detailed place max_fanout_violation_count
--------------------------------------------------------------------------
max fanout violation count 0

==========================================================================
detailed place max_cap_violation_count
--------------------------------------------------------------------------
max cap violation count 0

==========================================================================
detailed place setup_violation_count
--------------------------------------------------------------------------
setup violation count 0

==========================================================================
detailed place hold_violation_count
--------------------------------------------------------------------------
hold violation count 0

==========================================================================
detailed place report_checks -path_delay max reg to reg
--------------------------------------------------------------------------
No paths found.

==========================================================================
detailed place report_checks -path_delay min reg to reg
--------------------------------------------------------------------------
No paths found.

==========================================================================
detailed place critical path target clock latency max path
--------------------------------------------------------------------------
0

==========================================================================
detailed place critical path target clock latency min path
--------------------------------------------------------------------------
0

==========================================================================
detailed place critical path source clock latency min path
--------------------------------------------------------------------------
0

==========================================================================
detailed place critical path delay
--------------------------------------------------------------------------
-1

==========================================================================
detailed place critical path slack
--------------------------------------------------------------------------
0

==========================================================================
detailed place slack div critical path delay
--------------------------------------------------------------------------
0.000000

==========================================================================
detailed place report_power
--------------------------------------------------------------------------
Group                  Internal  Switching    Leakage      Total
                          Power      Power      Power      Power (Watts)
----------------------------------------------------------------
Sequential             9.16e-12   1.10e-11   1.45e-08   1.46e-08  49.9%
Combinational          1.89e-11   4.94e-11   1.46e-08   1.46e-08  50.1%
Clock                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
----------------------------------------------------------------
Total                  2.80e-11   6.04e-11   2.91e-08   2.92e-08 100.0%
                           0.1%       0.2%      99.7%

```




CTS Command

```
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk cts
```

![Screenshot 2024-11-26 051831](https://github.com/user-attachments/assets/a21cf9ae-ee17-4bad-b430-dd51f8029f38)



```
make gui_cts
```

![Screenshot 2024-11-26 002130](https://github.com/user-attachments/assets/65e9575e-383d-40cf-a0ff-822aef0d7336)



![Screenshot 2024-11-26 052318](https://github.com/user-attachments/assets/5cc4bcd8-afab-4a06-8ffe-0f27e87769da)


For Route

```
sudo make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config_2.mk route
```


![Screenshot 2024-11-26 004333](https://github.com/user-attachments/assets/fa1869ba-9d72-43c9-9f2d-6e2661a8d3cd)


```
make gui_route
```


![Screenshot 2024-11-26 005755](https://github.com/user-attachments/assets/ad81dd58-3264-4278-bfc6-c3849dbc92ad)



![Screenshot 2024-11-26 005824](https://github.com/user-attachments/assets/e0bf99fd-e1a3-47f3-aa13-112e4303a7f3)

For Final Layout

```
make gui_final
```

![Screenshot 2024-11-26 010952](https://github.com/user-attachments/assets/d3f6dacd-fc22-4776-aaed-99270efc1c94)



![Screenshot 2024-11-26 011016](https://github.com/user-attachments/assets/c5cdd5bb-0e5d-48f5-b64e-3268ef68ed97)


![Screenshot 2024-11-26 011202](https://github.com/user-attachments/assets/b83d9b77-c7fe-4a5c-95c6-b8173f8ec4d6)



![Screenshot 2024-11-26 011743](https://github.com/user-attachments/assets/f7c6c8bc-59f7-4a13-b5f3-f3ab3e145a10)




Heatmap for vsdbabysoc -


![Screenshot 2024-11-26 123824](https://github.com/user-attachments/assets/2d342aaf-46b2-4093-bc02-bf9a21639411)

***Placement***

![Screenshot 2024-11-26 124055](https://github.com/user-attachments/assets/4e6469c0-325d-4db6-b0ca-c23a929baea6)

***Power***

![Screenshot 2024-11-26 124556](https://github.com/user-attachments/assets/2111b8fb-9bcc-47dc-a0ad-ba97db7e2473)

***Routing congestion***

![Screenshot 2024-11-26 124736](https://github.com/user-attachments/assets/d2af60b2-2f3e-4b74-a9a9-114942fd50d7)

***Estimated congestion***

![Screenshot 2024-11-26 124809](https://github.com/user-attachments/assets/eceec0f1-208e-41a4-b39b-5c1815afd4aa)


***IR Drop***


![Screenshot 2024-11-26 124917](https://github.com/user-attachments/assets/6ed46db1-a791-4c25-8f01-828913dcbd12)

***QOR Report***


![Screenshot 2024-11-26 133322](https://github.com/user-attachments/assets/8d2a1c20-8bc4-4a55-81d9-aefbc994b40a)


![Screenshot 2024-11-26 133340](https://github.com/user-attachments/assets/f19377c4-b260-4d64-87b5-297916602960)








