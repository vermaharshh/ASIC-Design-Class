<details>
<summary> LAB 1 </summary>
<br>
1) Compile a C program of sum from 1 to n natural numbers using gcc compiler.

Step 1: Create a C file named sum1ton.c using leafpad editor.

Step 2: write a C program for sum from 1 to n natural numbers and save it,here n is taken as 50 for refernce.

Step 3 : Use gcc compiler to compile the program & run it using ./a.out to observe the output.



![Screenshot from 2024-07-29 15-55-14](https://github.com/user-attachments/assets/e9f02238-8f67-4404-9439-6dee57d8dd8d)

2) Compile the same program using riscv compiler.

Step 1: Open the code & run it using -O1.





![Screenshot from 2024-07-29 15-57-26](https://github.com/user-attachments/assets/43088f0d-8e73-44f4-804e-cc1fce029871)

Step 2: Check for number of instructions in main function. 





![Screenshot from 2024-07-29 15-58-56](https://github.com/user-attachments/assets/8a0f37cf-a5f8-4ed5-b92b-79bd26a462a6)

we will calculate the number of instructions by subtracting the address of first instruction of main section from address of the first instruction of the next section and divide the result by 4 since each instruction requires 4 memory locations.

No. of instructions = (101bc - 10184)/4 = 56/4 = 14 instructions

Step 3: Now compile using -Ofast: 



![Screenshot from 2024-07-29 16-00-02](https://github.com/user-attachments/assets/9ff0b1f4-c069-4f49-8f50-4c2e24787675)

No. of instructions = (100dc - 100b0)/4 = 44/4 = 11 instructions
</details>
<details>
<summary> LAB 2 </summary>
<br>
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

</details>

<details>
<summary> LAB 3 </summary>
<br>
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

</details>

<details>
<summary> LAB 4 </summary>
<br>
Task: Compile a C application with GCC and RISC-V GCC


Application : Sequence Detector
Sequence detectors are essential components in digital systems and have a wide range of applications. They are used to detect and identify specific patterns or sequences in binary data streams. 


Step 1: C Program
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to detect a sequence in a bit stream
void detectSequence(const char *stream, const char *sequence) {
    int streamLength = strlen(stream);
    int sequenceLength = strlen(sequence);
    
    // Iterate through the bit stream
    for (int i = 0; i <= streamLength - sequenceLength; i++) {
        // Check if the current substring matches the sequence
        if (strncmp(&stream[i], sequence, sequenceLength) == 0) {
            printf("Sequence '%s' detected at position %d.\n", sequence, i);
        }
    }
}

int main() {
    char stream[1024];
    char sequence[1024];
    
    // Read the bit stream
    printf("Enter the bit stream: ");
    scanf("%s", stream);

    // Read the sequence to detect
    printf("Enter the sequence to detect: ");
    scanf("%s", sequence);

    // Ensure the input strings are valid
    if (strspn(stream, "01") != strlen(stream) || strspn(sequence, "01") != strlen(sequence)) {
        printf("Error: Bit stream and sequence must contain only '0' and '1'.\n");
        return 1;
    }

    // Detect the sequence in the bit stream
    detectSequence(stream, sequence);

    return 0;
}

 
```



Step 2: Compile the program using gcc compiler
![Screenshot from 2024-08-14 21-45-38](https://github.com/user-attachments/assets/96ec5c83-7f5f-4b8a-b646-08fa459d1e3b)


Step 3: Compile the program using risc-v compiler
![Screenshot from 2024-08-14 21-55-15](https://github.com/user-attachments/assets/d960d898-fe74-4106-a009-47f7f183a477)
Observation: Output matches for both gcc and risc-v compiler.

</details>

<details>
<summary> LAB 5 </summary>
<br>
    
## TL Verilog ## 
    
Transaction Level Verilog is a higher-level abstraction of Verilog that allows designers to write hardware descriptions with fewer lines of code. It's used to define hardware designs at a more abstract level than traditional Verilog, making the design and simulation process more efficient.

## Makerchip ##
The Makerchip platform is an online integrated development environment (IDE) designed for developing, simulating, and verifying digital hardware designs, particularly in the context of RISC-V processors and open-source hardware. Makerchip supports the emerging Transaction-Level Verilog standard. Transaction-Level Verilog, or TL-Verilog, represents a huge step forward, by eliminating the need for the legacy language features of Verilog and by introducing simpler syntax. At the same time, TL-Verilog adds powerful constructs for pipelines and transactions.

# [Combinational Circuit Implementation:](url)
1) NOT GATE/ Inverter
   Inverter Inverts the Input and gives Output
   Writing and implementing NOT Gate Combinational Circuit using TL Verilog we get the following output

   

![NOTGATE](https://github.com/user-attachments/assets/4b542d36-ba68-4ade-ac31-cc0bf3ba684c)

2) XNOR GATE



![XNOR](https://github.com/user-attachments/assets/2465a5a7-ca52-4c8a-a0cd-6f0716bcd068)

## MUX 2:1 




![mux1](https://github.com/user-attachments/assets/7440bfa0-e171-4831-a04f-e192d02b85f6)

# 2:1 MUX Using Vectors



![mux2](https://github.com/user-attachments/assets/5af2bea3-368a-4e85-bd52-3a5e08caef99)

# [Combinational Calculator](url)

The combinational calculator is implemented using a 4*1 MUX.The calculator is implemented to perform basic operations like addition, subtraction, multiplication & division.
TL code & waveform for the combinational calculator:



![calc](https://github.com/user-attachments/assets/daf53384-55f1-4bc6-a921-eb18e1ca6a78)

#  [Sequential Circuit in TL Verilog](url)
## Sequential Calculator

This gives us the following waveforms and block diagram:- 



![seqcalc](https://github.com/user-attachments/assets/6cf524f4-9b77-4f39-8ca4-743650e6ca13)

# [Pipelined Logic](url)
## The below output describes for pipelined validity in the screenshot attached below




![pipelinevalidity](https://github.com/user-attachments/assets/7d9346a4-b560-4a43-9d06-1339b9f4c726)

Validity is another feature in TL verilog which is asserted if a particular transactions in a pipeline is valid or true. A new scope, called “when” scope is introduced for this and it is denoted as ?$valid. This new scope has many advantages - easier design, cleaner debug, better error checking and automated clock gating. Validity provides :

    Better error checking
    Automated Clock gating


# 2 Cycle Calculator
The attached snapshot of the pipeline sequential calcuator is included. The first pipeline stage consists of the input followed by arithimetic operation in the second pipeline stage and finally the ouput is included 2 cycles ahead in the third pipeline stage.


![2cyclecounter](https://github.com/user-attachments/assets/4750e45e-806f-4653-b0cc-91752405e4ce)

# Total Distance Calculator
The output for the above code is as follows:- 





![totaldist](https://github.com/user-attachments/assets/cf9bbc27-dc13-45e8-9265-4e28f2b6a225)

# [NEXT LAB](url)

## Instruction Fetch

In the fetch stage, the CPU will fetch the next instruction to be executed from the instruction memory.
The address from where the instruction will be fetched is provided by the program counter(PC).
If the reset signal is high, then the program counter will be reset to value 0, otherwise when the program counter will increment by 4 since the address of each instruction is 32 bits wide. The PC value will be fed as an input to the instruction memory to fetch the instruction from that particular address location.
Below is the screenshot where we can observe the implementation of the Fetch logic in MakerChip platform.



![fetch](https://github.com/user-attachments/assets/e3f7ff17-bf84-4fe3-b170-4095b004344b)

## Instruction Decode

In decode stage, we try to get the various infomation about an instruction from the fetch stage instruction read output. The information what we try to decode is which instruction set it belongs to, what is the immediate value if it is present, the register values etc.

Below code shows the implementation of decode stage in the MakerChip platform, 



![decode](https://github.com/user-attachments/assets/32a1aa91-d487-45d7-89a7-0b3c17d340aa)

## Register Read and Write
Inputs:
    Read_Enable - Enable signal to perform read operation
    Read_Address1 - Address1 from where data has to be read
    Read_Address2 - Address2 from where data has to be read
    Write_Enable - Enable signal to perform write operation
    Write_Address - Address where data has to be written
    Write_Data - Data to be written at Write_Address
Outputs:
    Read_Data1 - Data from Read_Address1
    Read_Data2 - Data from Read_Address2




![regreadwrite](https://github.com/user-attachments/assets/bea02c63-c1c1-4dc3-88bc-f0adfb6aaa41)





    











   
</details>






