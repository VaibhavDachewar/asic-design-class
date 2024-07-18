LAB1 -

TASK1 - Create a C program and compile it using GCC and then verify the output.

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


Task 2 - Compiling a C code on  RISC_V compiler using O1 and Ofast.

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

