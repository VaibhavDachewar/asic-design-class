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
magic -T sky130A.tech sky130_inv.mag &
```
![Screenshot 2024-11-13 111509](https://github.com/user-attachments/assets/4e585c17-ffe9-4560-9411-c8793154220e)

***2.Load the custom inverter layout in magic and explore.***

Screenshot of custom inverter layout in magic

![Screenshot 2024-11-13 111534](https://github.com/user-attachments/assets/30d22557-e3a3-42f3-ad83-deca97679316)

NMOS and PMOS identified

![Screenshot 2024-11-13 112131](https://github.com/user-attachments/assets/4b820177-0312-46db-9dbc-6c6b241bb06d)


![Screenshot 2024-11-13 112301](https://github.com/user-attachments/assets/358ca3b8-8257-434e-8ca9-e2b5b4d0fb50)

Output Y connectivity to PMOS and NMOS drain verified

![Screenshot 2024-11-13 112559](https://github.com/user-attachments/assets/8ab9cf59-9dfe-4dec-b8d8-5f60ec733e01)

PMOS source connectivity to VDD (here VPWR) verified

![Screenshot 2024-11-13 112636](https://github.com/user-attachments/assets/37b4e5bb-92b9-4ca6-9c70-694514ee145a)

NMOS source connectivity to VSS (here VGND) verified

![Screenshot 2024-11-13 112724](https://github.com/user-attachments/assets/86b87b07-5678-4143-b538-2adaf5dd33fc)

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

![Screenshot 2024-11-13 122149](https://github.com/user-attachments/assets/e2dd200e-85bb-4282-a938-ceea35956182)

Screenshot of created spice file

![Screenshot 2024-11-13 122241](https://github.com/user-attachments/assets/9ea08c2b-198f-43cf-80ce-dab5de1ffc1f)


![Screenshot 2024-11-13 122221](https://github.com/user-attachments/assets/42fbff87-6138-42ec-b75e-b683d27a945f)

***4. Editing the spice model file for analysis through simulation.***

Measuring unit distance in layout grid

![Screenshot 2024-11-13 123851](https://github.com/user-attachments/assets/867fa31c-78b4-421d-8e1c-006de1015c63)

Final edited spice file ready for ngspice simulation

![Screenshot 2024-11-13 125243](https://github.com/user-attachments/assets/9e6c6d50-3f4b-4fc7-88be-f54c09fbdf6b)

***5.Post-layout ngspice simulations.***

Commands for ngspice simulation

```
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a

```

Screenshots of ngspice run

![Screenshot 2024-11-13 125808](https://github.com/user-attachments/assets/d5fa10ea-7dc0-4014-90e4-c32ef49879e3)

Screenshot of generated plot

![Screenshot 2024-11-13 125820](https://github.com/user-attachments/assets/52d00637-9570-4b09-b3bd-47a905eb73d1)

Rise transition time calculation Rise Transition Time = Time taken for output to rise to 80% − Time taken for output to rise to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots

![Screenshot 2024-11-13 144300](https://github.com/user-attachments/assets/ff048c3e-ebb6-4df4-9455-30cb4f24e678)

![Screenshot 2024-11-13 144355](https://github.com/user-attachments/assets/847feee7-d87e-4b94-9a35-187bfcc1f3f9)

80% Screenshots

![Screenshot 2024-11-13 145211](https://github.com/user-attachments/assets/5edc732f-cc84-4100-b195-8cd30359d0f7)

![Screenshot 2024-11-13 144801](https://github.com/user-attachments/assets/0e488de3-0610-4a96-a5b9-ad1c3d2eafbf)

```
Rise Transition Time = 2.2389 - 2.1792 = 0.0597 ns = 59.70 ps
```

Fall Transition Time = Time taken for output to fall to 80% − Time taken for output to fall to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots


![Screenshot 2024-11-13 145715](https://github.com/user-attachments/assets/ee6cc6d6-fa8a-419b-b801-9b6fc0908e1b)

![Screenshot 2024-11-13 145741](https://github.com/user-attachments/assets/7786b21c-8eea-4c98-ada4-60c1321ebc07)

80% Screenshots

![Screenshot 2024-11-13 145903](https://github.com/user-attachments/assets/c9659fcb-681a-4eb9-9892-2dfaac3eb5cb)

```
Fall Transition Time = 4.0931 - 4.05 = 0.0431 ns = 43.10 ps
```

Rise Cell Delay Calculation Rise cell delay = Time taken by output to rise to 50% − Time taken by input to fall to 50% 50 % of 3.3V = 1.65V

50% Screenshots


![Screenshot 2024-11-13 150529](https://github.com/user-attachments/assets/63779075-483c-45fb-bc43-182b73c8cb1d)


![Screenshot 2024-11-13 150539](https://github.com/user-attachments/assets/21c30a73-8da9-40f1-bad2-0d82202916a8)

```
Rise cell delay = 2.20787 - 2.14944 = 0.05843 ns = 58.43 ps
```
Fall Cell Delay Calculation Fall cell delay = Time taken by output to fall to 50% − Time taken by input to rise to 50% 50 % of 3.3V = 1.65V

50% Screenshots

![Screenshot 2024-11-13 151302](https://github.com/user-attachments/assets/b4a96aca-3ebb-46c4-979a-a22f948c41aa)

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





