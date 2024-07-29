LAB 1
1) Compile a C program of sum from 1 to n natural numbers using gcc compiler.

Step 1: Create a C file named sum1ton.c using leafpad editor.

Step 2: Now write a C program for sum from 1 to n natural numbers and save it,here i kept n=50.

Step 3 : Use gcc compiler to compile the program & run it using ./a.out to observe the output.



![Screenshot from 2024-07-29 15-55-14](https://github.com/user-attachments/assets/e9f02238-8f67-4404-9439-6dee57d8dd8d)

2) Compile the same program using riscv compiler.

Step 1: Open the code & run it using -O1.





![Screenshot from 2024-07-29 15-57-26](https://github.com/user-attachments/assets/43088f0d-8e73-44f4-804e-cc1fce029871)

Step 2: Check for number of instructions in main function. 





![Screenshot from 2024-07-29 15-58-56](https://github.com/user-attachments/assets/8a0f37cf-a5f8-4ed5-b92b-79bd26a462a6)

Now we can calculate the number of instructions by subtracting the address of first instruction of main section from address of the first instruction of the next section and divide the result by 4 since each instruction requires 4 memory locations.

No. of instructions = (101bc - 10184)/4 = 56/4 = 14 instructions

Step 3: Now compile using -Ofast: 



![Screenshot from 2024-07-29 16-00-02](https://github.com/user-attachments/assets/9ff0b1f4-c069-4f49-8f50-4c2e24787675)

No. of instructions = (100dc - 100b0)/4 = 44/4 = 11 instructions


LAB 2
1) Verify the instructions in riscv compiler for sum1ton.c code

Step 1: Verify the output of the C program first using gcc compiler and then using spike simulator for riscv. Output must be same in both cases.



![Screenshot from 2024-07-29 16-02-01](https://github.com/user-attachments/assets/06f58533-db44-489e-83e1-b8c714b1239f)

Step 2: Open the spike debugger and run the program counter until the first address of the main function.




![Screenshot from 2024-07-29 16-02-46](https://github.com/user-attachments/assets/7834c3e5-5209-4c80-9cac-2df001322aba)

Step 3: Read the initial contents of the register a0 and then press enter to run the instruction.

Step 4: Verify that the instruction is executed properly.

Step 5: Now read the initial contents of sp register & run the next instruction.


![Screenshot from 2024-07-29 16-03-36](https://github.com/user-attachments/assets/1b817b39-cf70-4ad6-bea8-4cd8b4048ad0)

Step 6: Using calculator ensure that the difference between initial and final contents of the sp register should be as per the intruction set.


![Screenshot from 2024-07-29 16-04-19](https://github.com/user-attachments/assets/234d4c04-54ea-4753-992c-ba4cc6be670f)


LAB 3

1) RISC-V Instruction type of Given Instructions


| Instruction     | Type | 32-bit Instruction        | Hexadecimal    |
|-----------------|------|---------------------------|----------------|
| ADD r5, r6, r7  | R    | 0000000 00111 00110 000 00101 0110011 | 0x00B30333  |
| SUB r7, r5, r6  | R    | 0100000 00110 00101 000 00111 0110011 | 0x40A282B3  |
| AND r6, r5, r7  | R    | 0000000 00111 00101 111 00110 0110011 | 0x00F2F2B3  |
| OR r8, r6, r5   | R    | 0000000 00101 00110 110 01000 0110011 | 0x00B301B3  |
| XOR r8, r5, r4  | R    | 0000000 00100 00101 100 01000 0110011 | 0x00A281B3  |
| SLT r10, r2, r4 | R    | 0000000 00100 00010 010 01010 0110011 | 0x004102A3  |
| ADDI r12, r3, 5 | I    | 000000000101 00011 000 01100 0010011  | 0x00518313  |
| SW r3, r1, 4    | S    | 0000000 00011 00001 010 00001 0100011 | 0x00312023  |
| SRL r16, r11, r2| R    | 0000000 00010 01011 101 10000 0110011 | 0x0025C833  |
| BNE r0, r1, 20  | B    | 0000000 00001 00000 001 0000 1100011  | 0x00100263  |
| BEQ r0, r0, 15  | B    | 0000000 00000 00000 000 0000 1100011  | 0x00000063  |
| LW r13, r11, 2  | I    | 000000000010 01011 010 01101 0000011  | 0x0025A293  |
| SLL r15, r11, r2| R    | 0000000 00010 01011 001 01111 0110011 | 0x0025A933  |



2) 32 Bit Pattern and Hardcoded Instructions


| Operation           | Standard RISC-V ISA | Standard RISC-V ISA (Binary)               | Hardcoded ISA     | Hardcoded ISA (Binary)                  |
|---------------------|---------------------|--------------------------------------------|-------------------|-----------------------------------------|
| ADD R6, R2, R1      | 32'h00110333        | 000000000001 00010 000 00110 0110011       | 32'h02208300      | 000000100010 00000 100 00000 01100000  |
| SUB R7, R1, R2      | 32'h402083b3        | 010000000010 00000 000 00111 0110011       | 32'h02209380      | 000000100010 01000 100 10000 01100000  |
| AND R8, R1, R3      | 32'h0030f433        | 000000000011 00000 111 01000 0110011       | 32'h0230a400      | 000000100011 01000 101 00100 01100000  |
| OR R9, R2, R5       | 32'h005164b3        | 000000000101 00010 110 01001 0110011       | 32'h02513480      | 000000100101 00010 110 10100 01100000  |
| XOR R10, R1, R4     | 32'h0040c533        | 000000000100 00000 100 01010 0110011       | 32'h0240c500      | 000000100100 00000 100 11000 01100000  |
| SLT R1, R2, R4      | 32'h0045a0b3        | 000000000100 00010 010 00001 0110011       | 32'h02415580      | 000000100100 00010 101 01010 01100000  |
| ADDI R12, R4, 5     | 32'h004120b3        | 000000000101 00010 010 01100 0010011       | 32'h00520600      | 000000100100 00010 010 00010 01100000  |
| BEQ R0, R0, 15      | 32'h00000f63        | 000000000000 00000 000 00000 1100011       | 32'h00f00002      | 000000000000 00000 000 00000 11000000  |
| SW R3, R1, 2        | 32'h0030a123        | 000000000011 00000 010 00001 0100011       | 32'h00209181      | 000000100010 00000 010 00001 01100000  |
| LW R13, R1, 2       | 32'h0020a683        | 000000000010 00000 010 01101 0000011       | 32'h00208681      | 000000100010 00000 010 01100 01100000  |
| SRL R16, R14, R2    | 32'h0030a123        | 000000000011 00000 010 00001 0100011       | 32'h00271803      | 000000100010 00000 011 00110 01100000  |
| SLL R15, R1, R2     | 32'h002097b3        | 000000000010 00000 111 01111 0110011       | 32'h00208783      | 000000100010 00000 111 01111 01100000  |



Task 2
Instruction 1: ADD R6, R2, R1


![ADDR6](https://github.com/user-attachments/assets/9523b401-5a26-4277-92f4-c0dfd0c76d5c)



Instruction 2: SUB R7, R1, R2




![subr7](https://github.com/user-attachments/assets/5281c4c1-016a-4eb9-8e1b-20754b717716)



Instruction 3: AND R8, R1, R3






![andr6](https://github.com/user-attachments/assets/9aab96ba-9846-43df-8388-4fd22c2462db)



Instruction 4: OR R9, R2, R5




![ORR8](https://github.com/user-attachments/assets/798acce4-fedc-4fb7-bab5-ff0c7c1839bb)




Instruction 5: XOR R10, R1, R4




![XORR8](https://github.com/user-attachments/assets/8362e3bc-2fbb-48e2-97e2-c6b94fbd1cb5)




Instruction 6: SLT R1, R2, R4





![SLTR8](https://github.com/user-attachments/assets/93ce019f-1e7c-49b6-a093-b14bd9f850b2)


Instruction 7: ADDI R12, R4, 5




![ADDIR12](https://github.com/user-attachments/assets/e8663a74-9148-4372-ad5e-15e730d87b90)



Instruction 8: BEQ R0, R0, 15





![BEQR0](https://github.com/user-attachments/assets/eefb842b-c00c-4227-9bd3-196c350cb496)




