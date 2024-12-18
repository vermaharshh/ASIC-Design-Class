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

## Objective
To perform the lab sessions of Day 3, 4 and 5 from RISC-V based MYTH Workshop.
To gradually Implement a risc-v processor, 9-bit output which shows the gradual addition of 1 to 9 using TL- Verilog.
    
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


## [Next LAB](url)

# Risc-V processor core using TL-Verilog

TL-Verilog (Transaction-Level Verilog) is an extension of traditional Verilog that focuses on improving the abstraction and productivity in hardware design, especially for complex digital systems. It was developed to address some of the limitations of traditional RTL (Register-Transfer Level) design by introducing higher-level constructs and simplifying the design process.



![riscvimg](https://github.com/user-attachments/assets/8f073bd4-46dd-4d45-a620-dfdb572423da)


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
         $clk_har = *clk;
         
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


# Simulation Passed




![Screenshot from 2024-08-21 17-07-47](https://github.com/user-attachments/assets/93420c40-0bab-4a50-a11d-144b39adb4fc)

# Diagram




![Screenshot from 2024-08-21 17-05-03](https://github.com/user-attachments/assets/697de0ec-142d-4605-9e1a-8992c81a8908)


# Waveform




![Screenshot from 2024-08-21 17-07-28](https://github.com/user-attachments/assets/d73b5f30-e41c-488b-9f56-5b2f5834bafa)

# Viz



![Screenshot from 2024-08-21 17-05-45](https://github.com/user-attachments/assets/33306cb3-24d0-417e-ad89-546e7589ebe7)

# The waveform for the /xreg[14] where the sum of this program is store:




![image](https://github.com/user-attachments/assets/358d9017-ae35-4147-a47f-cb77b8cedb29)


Use Cases:
Processor Design, TL-Verilog is particularly useful in designing complex processors, where pipelining and transaction-level abstraction can significantly reduce development time. Digital Signal Processing (DSP): It can also be used in DSP applications where performance and efficiency are crucial. System-on-Chip (SoC) Design: TL-Verilog's ability to handle complex and large-scale designs makes it suitable for SoC design.
</details>



<details>
<summary> LAB 6 </summary>
<br>


## To convert the TLV to verilog using Sandpiper and then use GTKWave pre-synthesis simulation to verify the design.

# Aim

To compare the pre-synthesis simulation outputs of a RISC-V processor using the Icarus Verilog, GTKWave, and Makerchip tools.

# Step-by-Step Procedure:

**Step 1**: Install the Required Packages:

Run the following command to install the necessary packages:

~~~
sudo apt install make python python3 python3-pip git iverilog gtkwave
sudo apt-get install python3-venv
pip3 install pyyaml click sandpiper-saas
python3 -m venv .venv
source ~/.venv/bin/activate
sudo apt install make python python3 python3-pip git iverilog gtkwave docker.io
sudo chmod 666 /var/run/docker.sock
~~~

**Step 2**: Now clone the given repository in the home directory :

~~~
cd ~
git clone https://github.com/manili/VSDBabySoC.git
~~~



![WhatsApp Image 2024-08-26 at 18 31 47](https://github.com/user-attachments/assets/6349da74-1ccd-4141-934e-b195acb598cc)

**Step 3**: Replace the .tlv file in the VSDBabySoC/src/module folder with our RISC-V .tlv file which we want to convert into verilog.

**Step 4**: Change the working directory to VSDBabySoC.

~~~
cd VSDBabySoC
~~~

**Step 5**: Translate TL-Verilog to Verilog:

Use the Sandpiper-SaaS compiler to convert the TL-Verilog description of the RISC-V processor into Verilog:

~~~
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
~~~

This command will generate a Verilog file named rvmyth.v in the specified output directory.




![WhatsApp Image 2024-08-26 at 18 31 47(1)](https://github.com/user-attachments/assets/a5484221-29f9-40a4-a1b1-38aabc4e8699)

**Step 6**: Create the Pre-Synthesis Simulation File:

Run the following command to create the pre_synth_sim.vcd file required for simulation:
~~~
make pre_synth_sim
~~~




![WhatsApp Image 2024-08-26 at 18 31 47(2)](https://github.com/user-attachments/assets/2006cfcf-17aa-4188-be1d-c6dc7be86f73)



This step prepares the simulation environment and generates the necessary .vcd file for visualization.

**Step 7**: Compile and Simulate the RISC-V Design:

Compile and run the simulation using Icarus Verilog with the following command:

~~~
iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module
~~~

**Step 8**: The result of the simulation (i.e. pre_synth_sim.vcd) will be stored in the output/pre_synth_sim directory. Therefore change the working directory to output.

~~~
cd output
./pre_synth_sim.out
~~~



![WhatsApp Image 2024-08-26 at 18 31 47(3)](https://github.com/user-attachments/assets/328b9b19-ef32-416e-a224-a9a516d4549a)

**Step 9**: Open the .vcd File in GTKWave:

Use GTKWave to view the waveform of the simulation results:

~~~
gtkwave pre_synth_sim.vcd
~~~
GTKWave will launch, displaying the waveform generated from the pre-synthesis simulation, allowing you to analyze the processor's behavior.


![WhatsApp Image 2024-08-26 at 18 31 48](https://github.com/user-attachments/assets/8b1a33d0-0722-40fe-82f2-d8c940885492)

## GTKWave Output Waveform



![WhatsApp Image 2024-08-26 at 18 31 31](https://github.com/user-attachments/assets/9d0944a5-5e51-4cd5-b4df-d8426eccd3c7)

## Comparison of Output Waveforms

![image](https://github.com/user-attachments/assets/b656bd3d-fc82-4d50-9f19-46dddff21262)

## Conclusion

The waveform outputs from GTKWave and Makerchip matched perfectly, validating the RISC-V processor design's accuracy and consistency. This alignment confirms that the design of RISC-V core processor is robust.
</details>
<details>
<summary> LAB 7 </summary>

## Integration of Peripherals for Converting Digital Output to Analog Output using DAC and PLL

**Aim: Analyzing RISC-V Pre-Synthesis Analog Simulation outputs using Iverilog GTKwave**

Install Yosys

Yosys is a framework for RTL synthesis. Follow these steps to install it:

    Clone the Yosys Repository

    git clone https://github.com/YosysHQ/yosys.git
    cd yosys

Ensure make is Installed

sudo apt install make

Install Required Dependencies

sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev

Compile Yosys

make config-gcc
make
sudo make install

Verify Yosys Installation

yosys








![Screenshot from 2024-09-02 15-04-52](https://github.com/user-attachments/assets/8ab69eb1-eca9-497a-a9e9-d50140a32fd9)
















Install IVerilog

IVerilog is a Verilog simulation and synthesis tool. Follow these steps to install it:

    Install IVerilog

    sudo apt-get install iverilog

Verify IVerilog Installation

iverilog -v



![Screenshot from 2024-09-02 15-02-46](https://github.com/user-attachments/assets/506fb726-cc2c-4201-ab61-68c5a711f474)







Install GTKWave

GTKWave is a waveform viewer used for debugging digital circuits. Follow these steps to install it:

    Update and Install GTKWave

    sudo apt update
    sudo apt install gtkwave

Verify GTKWave Installation

gtkwave



![Screenshot from 2024-09-02 15-01-13](https://github.com/user-attachments/assets/8aca125f-2105-4122-bfdc-ff683749b794)




-)Phase-Locked Loop (PLL)
The crystal oscillator on the board generates a clock with a frequency range of 12 to 20 MHz. Since the processor operates at a frequency near 100 MHz, an IP or peripheral is required to boost this low-frequency clock to a higher frequency. The PLL fulfills this role by taking the crystal oscillator clock as input and providing a high-frequency clock output to our RISC-V core. This clock is named `CPU_clk_har_a0`.

A Phase-Locked Loop (PLL) is an electronic circuit that synchronizes an output signal's phase and frequency with a reference signal. It typically consists of three main components:

    Phase Detector: Compares the phase of the reference signal with the output signal and generates an error signal based on the difference.

    Loop Filter: Processes the error signal to smooth it out, reducing noise and improving stability.

    Voltage-Controlled Oscillator (VCO): Adjusts its output frequency based on the filtered error signal to minimize the phase difference.

The PLL is widely used in applications such as clock generation, frequency synthesis, and data recovery in communication systems.


-)Digital to Analog Converter (DAC)
While the processor operates with digital inputs, signals are transmitted and received in analog form. To convert the digital signals from our RISC-V core into analog signals, we utilize the DAC IP.



A Digital-to-Analog Converter (DAC) is an electronic device that converts digital signals (typically binary) into analog signals (such as voltage or current).

This conversion is crucial in systems where digital data needs to be interpreted by analog devices or for output to be perceived by humans, like in audio and video equipment.

DACs are commonly used in applications like audio playback, video display, and signal processing.

# Commands to Run the `rvmyth.v` File

```bash
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
```

```bash
./pre_synth_sim.out
```

```bash
gtkwave pre_synth_sim.vcd
```
## Execution Process
The above process was executed as follows:


![sub1](https://github.com/user-attachments/assets/f1018f80-e161-48f9-ae16-020d5431683c)

## Output
The output generated is shown below:



![sub](https://github.com/user-attachments/assets/4a791490-6041-4eca-bea5-90e798113124)



CLK is the output clk signal from the PLL module.

clk_har is the clock used by the RISC-V CPU for the operations.

reset is the reset signal for the RISC-V CPU.

REF is the input clk reference signal to the PLL module.

OUT is the DAC output signal.

The **ZOOMED** OUT image of the waveform is shown below:

![Screenshot from 2024-09-04 18-17-29](https://github.com/user-attachments/assets/78c4fd29-4f9c-4007-84c9-df5813892847)






</details>

<details>
<summary> LAB 8 </summary>
<br>

# **RTL design using Verilog with SKY130 Technology**

<details>
<summary> Day1 </summary>
<br>
	
## Day 1: Introduction to Verilog RTL Design and Synthesis

In digital circuit design, register-transfer level (RTL) is an abstraction that models a synchronous digital circuit by describing how data flows between hardware registers and how logic operations are applied to these signals. This RTL abstraction is used in HDL (Hardware Description Language) to create high-level models of a circuit, which can then be used to derive lower-level representations and, eventually, the actual hardware layout.

**Simulator:** A tool used to verify the design. In this workshop, we utilize the iverilog tool. Simulation involves generating models that replicate the behavior of the intended device (simulation models) and creating test models to validate the device (test benches). RTL Design: Consists of one or more Verilog files that implement the required design specifications and functionality for the circuit.

Test Bench: The configuration used to provide stimulus (test vectors) to the design in order to verify its functionality.
HOW SIMULATOR WORKS

Simulator looks for changes on input signals and based on that output is evaluated.



![Screenshot from 2024-10-20 13-36-14](https://github.com/user-attachments/assets/89bf52ea-60a3-4bc7-ac9b-891d3240d90a)

SIMULATION FLOW
Simulator continuously checks for changes in the input. If there is an input change, the output is evaluated; else the simulator will never evaluate the output.
![image](https://github.com/user-attachments/assets/0ab0df32-613b-4754-9fff-046a6aead12b)

# ENVIRONMENT SETUP
```
mkdir VLSI 
cd VLSI
git clone https://github.com/kunalg123/vsdflow.git
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

```


![DAY1L1](https://github.com/user-attachments/assets/e200cabf-4d01-46ed-bd0a-0b38fd017f12)

Command to view the folder structure of the lab, and list the contents of the directory:

```
cd sky130RTLDesignAndSynthesisWorkshop
```


![DAY1L1a](https://github.com/user-attachments/assets/ce61d0ab-c247-4968-a99f-5cba8417d509)

There are a number of verilog designs and testbench files for simulation. Run the following commands to simulate the verilog code 'good_mux.v'. The first line will compile and check for syntax errors in both the design and testbench. An executable file 'a.out' is generated on successful compilation. On executing a.out, a vcd file is generated that captures changes in the input and output values. GTKWave is used to view the waveforms

```
iverilog good_mux.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```



![DAY1L2A](https://github.com/user-attachments/assets/97b0f252-c867-4cfe-88d7-dbd5e8702eff)

We can view the waveform of a simple 2:1 mux which selects the input based on the select line 

![Day1L2](https://github.com/user-attachments/assets/b2fde258-4fac-44e9-83fc-b4ad2e526d8f)

Access Module Files

To view the contents of the file run the following command

```
$ vim tb_good_mux.v -o good_mux.v
```



![DAY1L3](https://github.com/user-attachments/assets/4862b636-b2c4-44fe-b6dc-43ae741576d2)


Yosys

Synthesizer is a tool for converting the RTL to Netlist and here we are using the Yosys as the Synthesizer.

A synthesizer plays a key role in digital design by transforming RTL (Register Transfer Level) code into a gate-level netlist. This netlist provides a detailed description of the circuit, outlining the logical gates and their interconnections, and serves as the foundation for later stages like place and route. In this design flow, the synthesizer being used is Yosys, an open-source tool for Verilog HDL synthesis. Yosys applies several optimization techniques to generate an efficient gate-level implementation from the RTL code.
Block Diagram of Yosys setup :

![image](https://github.com/user-attachments/assets/d37c0e04-9513-4d06-8dfd-cbf3cff9e1dd)

Block Diagram of Systhesis Verification :
![image](https://github.com/user-attachments/assets/9512a77a-d63c-40de-a797-3d9e0f97a8be)

Logic Systhesis

RTL Design: The design is described using a behavioral representation in Hardware Description Language (HDL) based on the required specifications.

Synthesis: The RTL (Register Transfer Level) code is translated into a gate-level representation. This process converts the design into gates and interconnections, resulting in a file known as the netlist.
![image](https://github.com/user-attachments/assets/23109d24-c4e8-437f-9475-eb8e662b8f4f)

Liberty(.lib): Its a collection of logical modules. It includes basic logic gates like And, Or, Not, etc... and it contains different variants of the same gate ike 2input, 3input, 4input, slow, fast, medium gates etc. Fast cells are used if only high performance is needed. Slower cells is used to address hold time issues. IThe selection of faster cells in digital circuit design can increase area and power consumption while potentially leading to hold time violations. Conversely, excessive use of slower cells can result in suboptimal performance. The optimal cell selection for synthesis is guided by constraints that balance area, power, and timing requirements.


This will invoke/start the yosys

```
yosys
```



![day1l3a](https://github.com/user-attachments/assets/c939df26-3b52-4530-b28c-b1808d3c31ec)

Load the sky130 standard library.
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib      
```
Read the design files
```
read_verilog good_mux.v        
```
Synthesize the top level module
```
synth -top good_mux     
```



![day1l3b](https://github.com/user-attachments/assets/57ee5026-6357-486e-bb8c-32a2f2d591ee)

Map to the standard library
```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```


![day1l3c](https://github.com/user-attachments/assets/3befd597-be42-47e7-ac76-47ace5864323)


![day1l3d](https://github.com/user-attachments/assets/faefd963-cf46-459f-9a92-476b805b090c)

In order to see graphical version of the logic it has realized type :
```
show
```


![day1l3e](https://github.com/user-attachments/assets/32b98648-3ab3-457d-bd56-d2ede27bba7f)

Now, To write the result netlist to a file use the write_veriog command. This will output the netlist to a file in the current directory.
```
write_verilog -noattr good_mux_netlist.v
!gvim good_mux_netlist.v
```



![day1l3ff](https://github.com/user-attachments/assets/432335a1-d909-4fcf-b991-c3db843bb2f7)

</details>

<details>
<summary> Day 2 </summary>
<br>



## **DAY 2 Timing libs, hierarchical vs flat synthesis and efficient flop coding styles**

navigate to the verilog_files directory then type these below commands
Command to open the libary file
```
$ vim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
To shut off the background colors/ syntax off:
: syn off
To enable the line numbers
: se nu

![image](https://github.com/user-attachments/assets/b748ddb8-caff-4127-82a6-432fa7f7b090)

The liberty(.lib) files store PVT parameters (Process, Voltage, Temperature). Variations in these parameters can significantly affect circuit performance. Manufacturing variations, voltage fluctuations, and temperature changes all contribute to this impact.
The timing data of standard cells is provided in the liberty format. Every .lib file will provide timing, power, noise, area information for a single corner ie process,voltage, temperature etc.

    Library
    general information common to all cells in the library.
    Cell
    specific information about each standard cell.
    Pin
    Timing, power, capacitance, leakage functionality etc characteristics for each pin in each cell. 

The .lib file provides critical information about the type of process used (such as 130nm technology in this case) and the process conditions like temperature, voltage, etc. It also defines various constraints, including units for variables and the type of technology used. For example:

    technology("cmos"): Specifies the technology as CMOS.
    delay_model : "table_lookup": Defines the delay model.
    bus_naming_style : "%s[%d]": Defines the naming convention for buses.
    time_unit : "1ns": Sets the unit of time.
    voltage_unit : "1V": Sets the unit of voltage.
    leakage_power_unit : "1nW": Defines the unit for leakage power.
    current_unit : "1mA": Sets the unit of current.
    pulling_resistance_unit : "1kohm": Specifies the unit for pulling resistance.
    capacitive_load_unit(1.0000000000, "pf"): Defines the unit for capacitive load.

Additionally, the .lib file provides details about the characteristics of various cells, such as leakage power, power consumption, area, input capacitance, and delay for different input combinations.

We can also find different versions of the same cell. For example, consider the 2- INPUT AND gate


![day2l1](https://github.com/user-attachments/assets/bde4ef8f-8ed9-48bd-9856-b500b9befb6f)

# Hierarchial synthesis vs Flat synthesis

Hierarchial synthesis
Steps :

Invoke yosys
```
yosys
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog multiple_modules.v
```
![image](https://github.com/user-attachments/assets/c0fc026c-da32-4876-b43d-4f269f1b24f0)

Synthesize the Design
```
synth -top multiple_modules
```
"When running synth -top multiple_modules in Yosys, a hierarchical synthesis is performed, meaning that the hierarchy between modules is preserved.

![image](https://github.com/user-attachments/assets/15bb4a77-ff15-441e-9f6c-7e70c0a22435)

Multiple Modules: - 2 SubModules

Now Generate the Netlist
```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation of Logic for Multiple Modules
```
show multiple_modules
```

![image](https://github.com/user-attachments/assets/cc56de63-cd75-494e-ac9d-37c5aeab9542)

Writing the netlist and then viewing
```
write_verilog -noattr multiple_modules_hier.v
!vim multiple_modules_hier.v
```

![image](https://github.com/user-attachments/assets/7d81cdfe-3f69-4baa-b7fb-0429cb699b44)

is the required NETlist file.

**Flat synthesis**

Merges all hierarchical modules in the design into a single module to create a flat netlist
```
flatten
```
Writing the netlist and then viewing
```
write_verilog -noattr multiple_modules_hier.v
!vim multiple_modules_hier.v
```


![image](https://github.com/user-attachments/assets/f8171667-c105-43b6-93e3-9d632a8206d0)

Now let's Create a Graphical Representation of Logic for Multiple Modules
Just execute show command in yosys after that

```
show 
```

![image](https://github.com/user-attachments/assets/cd49d85c-97b2-4f87-9772-928a791ccb07)

## Various D Flops coding styles, Simulation using Iverilog and GTKWave followed by Synthesis using Yosys.

In a digital design, when an input signal changes state, the output changes after a propogation delay. All logic gates add some delay to singals. These delays cause expected and unwanted transitions in the output, called as Glitches where the output value is momentarily different from the expected value. An increased delay in one path can cause glitch when those signals are combined at the output gate. In short, more combinational circuits lead to more glitchy outputs that will not settle down with the output value.
Flip flop overview

A D flip-flop is a sequential element that follows the input pin d at the clock's given edge. D flip-flop is a fundamental component in digital logic circuits. There are two types of D Flip-Flops being implemented: Rising-Edge D Flip Flop and Falling-Edge D Flip Flop.

Every flop element needs an initial state, else the combinational circuit will evaluate to a garbage value. In order to achieve this, there are control pins in the flop namely: Set and Reset which can either be Synchronous or Asynchronous.

Simulation of D-Flipflop using Iverilog and GTKWave. Performed simulations for 3 types of D-Flipflops

    Asynchronous Reset
    Asynchronous Set
    Synchronous Reset.

1. Asynchronous Reset

The verilog code for the asynchronous reset is given below :
```
module dff_asyncres(input clk, input async_reset, input d, output reg q);
	always@(posedge clk, posedge async_reset)
	begin
		if(async_reset)
			q <= 1'b0;
		else
			q <= d;
	end
endmodule
```
Testbench code is as follows:
```
module tb_dff_asyncres; 
	reg clk, async_reset, d;
	wire q;
	dff_asyncres uut (.clk(clk),.async_reset (async_reset),.d(d),.q(q));

	initial begin
		$dumpfile("tb_dff_asyncres.vcd");
		$dumpvars(0,tb_dff_asyncres);
		// Initialize Inputs
		clk = 0;
		async_reset = 1;
		d = 0;
		#3000 $finish;
	end
		
	always #10 clk = ~clk;
	always #23 d = ~d;
	always #547 async_reset=~async_reset; 
endmodule

```
Command steps :

Go to the required directory:
```
cd /VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
Run the following commands to compile and simulate the design:
```
iverilog dff_asyncres.v tb_dff_asyncres.v
ls
```
The compiled output will be saved as a.out.

Execute the compiled output and open the waveform viewer:
```
./a.out
gtkwave tb_dff_asyncres.vcd
```
By following these steps,we can observe the behavior of the D Flip-Flop with an asynchronous reset in the waveform viewer:
![image](https://github.com/user-attachments/assets/d9243a04-9150-4d57-9840-34a8de4a6df6)

Observation: From the waveform, we can observe that when the asynchronous reset is activated (set high), the Q output immediately resets to zero, regardless of the clock's positive or negative edge. This demonstrates the asynchronous behavior of the reset signal.

-) Now we will see for a D Flip Flop with Asynchronous Set

The design ensures that when the asynchronous set signal is high, the output Q is immediately set to 1, regardless of the clock signal.

Verilog Code for Asynchronous Set D Flip-Flop:
```
module dff_async_set(input clk, input async_set, input d, output reg q);
	always@(posedge clk, posedge async_set)
	begin
		if(async_set)
			q <= 1'b1;
		else
			q <= d;
	end
endmodule
```
Testbench Code:
```
module tb_dff_async_set; 
	reg clk, async_set, d;
	wire q;
	dff_async_set uut (.clk(clk), .async_set(async_set), .d(d), .q(q));

	initial begin
		$dumpfile("tb_dff_async_set.vcd");
		$dumpvars(0, tb_dff_async_set);
		// Initialize Inputs
		clk = 0;
		async_set = 1;
		d = 0;
		#3000 $finish;
	end

	always #10 clk = ~clk;
	always #23 d = ~d;
	always #547 async_set = ~async_set; 
endmodule
```
Steps to Run the Simulation:

    Navigate to the directory containing the Verilog files:

```
cd /VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
Compile the Verilog code and the testbench using Icarus Verilog:
```
iverilog dff_async_set.v tb_dff_async_set.v
ls
```
The output will be saved as a.out.

Run the compiled file and open the waveform in GTKWave:
```
./a.out
gtkwave tb_dff_async_set.vcd
```
Result:

After running the simulation, we will observe the behavior of the D Flip-Flop with an asynchronous set in the waveform viewer. Below is a snapshot of the commands and the resulting waveforms.
![image](https://github.com/user-attachments/assets/b8f062e9-067d-4402-be17-fd0c9436a2b0)

Synchronous Reset

The verilog code for the Synchronous reset is given below :
```
module dff_syncres(input clk, input sync_reset, input d, output reg q);
	always@(posedge clk)
	begin
		if(sync_reset)
			q <= 1'b0;
		else
			q <= d;
	end
endmodule
```
Testbench code is as follows:
```
module tb_dff_syncres; 
	reg clk, syncres, d;
	wire q;
	dff_asyncres uut (.clk(clk),.sync_reset (sync_reset),.d(d),.q(q));

	initial begin
		$dumpfile("tb_dff_syncres.vcd");
		$dumpvars(0,tb_dff_syncres);
		// Initialize Inputs
		clk = 0;
		sync_reset = 1;
		d = 0;
		#3000 $finish;
	end
		
	always #10 clk = ~clk;
	always #23 d = ~d;
	always #547 sync_reset=~async_reset; 
endmodule
```
Command steps :

Go to the required directory:
```
cd /VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
put these commands to see the waveform:
```
iverilog dff_syncres.v tb_dff_syncres.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_dff_syncres.vcd
```
Below is the Snapshot of the above commands and the resultant Waveforms:
![image](https://github.com/user-attachments/assets/e3e2b565-fdfb-4c30-a7eb-9c5812df8ca9)

OBSERVATION : From the waveform, it can be observed that the Q output changes to zero when the synchronous reset is set high, only at the positive clock edge.

# Synthesis of Various D-Flipflop using Yosys. Performed simulations for 3 types of D-Flipflops

    Asynchronous Reset
    Asynchronous Set
    Synchronous Reset.

Asynchronous Reset
Command steps :

Invoke yosys
```
yosys
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_asyncres.v
```
Synthesize the Design
```
synth -top dff_asyncres
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation of Asynchronous Reset - D FlipFlop
```
show
```

![image](https://github.com/user-attachments/assets/f6261a22-6bb0-4530-81b8-2bf697627289)

Asynchronous Set
Command steps :

Invoke yosys
```
yosys
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_async_set.v
```
Synthesize the Design
```
synth -top dff_async_set
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation of Asynchronous Set - D FlipFlop
```
show
```
![image](https://github.com/user-attachments/assets/a4643783-36f2-4abf-9bce-f1cb9b0f9593)

Synchronous Reset
Command steps :

Invoke yosys
```
yosys
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_syncres.v
```
Synthesize the Design
```
synth -top dff_syncres
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation of Synchronous Reset - D FlipFlop
```
show
```

![image](https://github.com/user-attachments/assets/e0301b35-b6f3-4180-87da-0a0b7fb0c0a8)

</details>

<details>
<summary> Day 3 </summary>
<br>



## Day 3: Combinational and sequential optimizations

There are two types of optimisations: Combinational and Sequential optimisations. These optimisations are done inorder to achieve designs that are efficient in terms of area, power, and performance.

Combinational Optimization

The techiniques used are:

    Constant Propagation (Direct Optimisation)
    Boolean Logic Optimisation (using K-Map or Quine McCluskey method)


Let's see a 2 input AND gate

The verilog code is given below :
```
module opt_check(input a, input b, output y);
	assign y = a?b:0;
endmodule
```
The above code infers a multiplexer and since one of the inputs of the multiplexer is always connected to the ground it will infer an AND gate on optimisation.

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v
synth -top opt_check
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```


![image](https://github.com/user-attachments/assets/973799fa-e0af-43a4-8a1a-61d311dbd60e)
Example 2:

Verllog code:
```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```
Since one of the inputs of the multiplexer is always connected to the logic 1 it will infer an OR gate on optimisation.The OR gate will be NAND implementation since NOR gate has stacked pmos while NAND implementation has stacked nmos.

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check2.v
synth -top opt_check2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![image](https://github.com/user-attachments/assets/1475fec3-7c11-4e38-81cc-ffe2cac79905)

Example 3:

Verilog code:
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
On optimisation the above design becomes a 3 input AND gate.

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check3.v
synth -top opt_check3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```
![image](https://github.com/user-attachments/assets/f1b6155c-da5c-4197-b9af-c8360377c339)

Example 4:

Verilog code:
```
module opt_check4 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```
On optimisation the above design becomes a 2 input XNOR gate (3 input boolean logic)

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check4.v
synth -top opt_check4
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

![image](https://github.com/user-attachments/assets/756733bc-d41a-485e-a136-3f73a003a9b4)

Example 5:

Verilog code:
```
module sub_module1(input a , input b , output y);
 assign y = a & b;
endmodule

module sub_module2(input a , input b , output y);
 assign y = a^b;
endmodule

module multiple_module_opt(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
sub_module2 U3 (.a(b), .b(d) , .y(n3));

assign y = c | (b & n1); 

endmodule
```
On optimisation the above design becomes a AND OR gate

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module_opt.v
synth -top multiple_module_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
show
```
![image](https://github.com/user-attachments/assets/ddb76d3a-2e0b-4a1c-aded-c7f2ba950d4c)

Example 6:

Verilog code:
```
module sub_module(input a , input b , output y);
	assign y = a & b;
endmodule

module multiple_module_opt2(input a , input b , input c , input d , output y);
		wire n1,n2,n3;
	sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
	sub_module U2 (.a(b), .b(c) , .y(n2));
	sub_module U3 (.a(n2), .b(d) , .y(n3));
	sub_module U4 (.a(n3), .b(n1) , .y(y));
endmodule
```
On optimisation the above design becomes Y=0

Run the below code for netlist:
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module_opt2.v
synth -top multiple_module_opt2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
show
```

![image](https://github.com/user-attachments/assets/3cd89d50-a15b-4b6c-aa62-dbbedefffcaf)

# Optimization of various Sequential Designs

    D-Flipflop Constant 1 with Asynchronous Reset (active low)
    D-Flipflop Constant 2 with Asynchronous Reset (active high)
    D-Flipflop Constant 3 with Synchronous Reset (active low)
    D-Flipflop Constant 4 with Synchronous Reset (active high)
    D-Flipflop Constant 5 with Synchronous Reset
    Counter Optimization 1
    Counter Optimization 2
1. D-Flipflop Constant 1 with Asynchronous Reset (active low)

The verilog code for the asynchronous reset (active low) is given below :
```
module dff_const1(input clk, input reset, output reg q); 
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```
Testbench code is as follows:
```
module tb_dff_const1; 
	reg clk, reset;
	wire q;

	dff_const1 uut (.clk(clk),.reset(reset),.q(q));

	initial begin
		$dumpfile("tb_dff_const1.vcd");
		$dumpvars(0,tb_dff_const1);
		// Initialize Inputs
		clk = 0;
		reset = 1;
		#3000 $finish;
	end

	always #10 clk = ~clk;
	always #1547 reset=~reset;
endmodule
```
Steps:
```
iverilog dff_const1.v tb_dff_const1.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_dff_const1.vcd
```
Below is the Snapshot of the above commands and the resultant Waveforms:


![image](https://github.com/user-attachments/assets/d2fea82d-ff00-497b-b748-930592b0fc95)

OBSERVATION : From the waveform, it can be observed that the Q output is always high when reset is zero, and reset doesn't depend on clock edge.
SYNTHESIS :
Invoke yosys
```
yosys
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_const1.v
```
Synthesize the Design
```
synth -top dff_const1
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/1a0e4537-4214-4034-93cf-3482cf14c030)

OBSERVATION : Since reset doesn't depend on clock edge, therefore the D Flip Flop has not been removed.

2. D-Flipflop Constant 2 with Asynchronous Reset (active high)

The verilog code for the asynchronous reset (active high) is given below :
```
module dff_const1(input clk, input reset, output reg q); 
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```
Testbench code is as follows:
```
module tb_dff_const2; 
	reg clk, reset;
	wire q;

	dff_const2 uut (.clk(clk),.reset(reset),.q(q));

	initial begin
		$dumpfile("tb_dff_const1.vcd");
		$dumpvars(0,tb_dff_const1);
		// Initialize Inputs
		clk = 0;
		reset = 1;
		#3000 $finish;
	end

	always #10 clk = ~clk;
	always #1547 reset=~reset;
endmodule
```
Steps:
We just need to put few commands as stated below in order to see the waveforms.
```
iverilog dff_const2.v tb_dff_const2.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_dff_const2.vcd
```

![image](https://github.com/user-attachments/assets/31d674d0-4562-4b1a-aa66-461be3b0d21b)

OBSERVATION : From the waveform, it can be observed that the Q output is always high irrespective of reset.
SYNTHESIS :

This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_const2.v
```
Synthesize the Design
```
synth -top dff_const2
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/7f97eb24-2a88-42bd-a52d-3433fe955f02)

OBSERVATION : Since output q doesn't depend on reset edgeand is always 1, therefore the D Flip Flop has been removed.

3. D-Flipflop Constant 3 with Synchronous Reset (active low)

The verilog code for the synchronous reset (active low) is given below :
```
module dff_const3(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b0;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```
Testbench code is as follows:
```
module dff_const3(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b0;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule

```

SYNTHESIS :
This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_const3.v
```
Synthesize the Design
```
synth -top dff_const3
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/f88bf74e-bc5a-4938-89f6-bdce5d82b58a)

![image](https://github.com/user-attachments/assets/f8ac0e77-b25b-47e7-aa0c-0af664240e4b)

OBSERVATION : This module defines a D flip-flop, for a positive edge of reset, q is set to 1 and q1 is set to 0. On each clock cycle, q1 is set to 1, and q is updated with the value of q1.

When synthesized, the design will result in a flip-flop where q becomes 1 after the first clock cycle post-reset and stays 1 afterward.

4. D-Flipflop Constant 4 with Synchronous Reset (active high)

The verilog code for the synchronous reset (active high) is given below :
```
module dff_const4(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b1;
			q1 <= 1'b1;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```
SYNTHESIS :
This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_const4.v
```
Synthesize the Design
```
synth -top dff_const4
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/0abfc34a-38f0-409c-ad11-e25c968c6977)

![image](https://github.com/user-attachments/assets/58d8fde7-dfe6-40dc-a0d8-569a1e8a8ab2)

OBSERVATION : This module defines a D flip-flop that sets both q and q1 to 1 on a positive edge of reset. On each clock cycle, q1 remains 1, and q is updated with the value of q1 (which is always 1).

When synthesized, the design will result in a flip-flop where q is always 1, regardless of the reset or clock state.

Generating the netlist for the special case circuits.

    Multiplication by a factor of 2: In this circuit, there are no special hardware multipler blocks are not required for the implementation. Rather we will append zero bit to the LSB of the number effectively shifting it to the left. The same can be seen the netlist images generated from the below commands.
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_2.v
synth -top mul2
show
write_verilog -noattr mul2_netlist.v
!gvim mul2_netlist.v
```
As we can see that there is no hardware involved hence the command of abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib says don't call the ABC function as there is nothing to map.

![image](https://github.com/user-attachments/assets/dfb59c79-3922-43e0-b765-003e7f75ccf4)

![image](https://github.com/user-attachments/assets/f3d5f3c5-2f95-43d4-a35c-f596bf0ce2d2)


    Mul8: Similar to the previous one, here for multiplication of the given number with a factor of 9 will be implemented without the use of any hardware cells, memories, etc.

Below are the commands and the respective screenshots:

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_8.v
synth -top mult8
show
write_verilog -noattr mult8_netlist.v
!gvim mult8_netlist.v

![image](https://github.com/user-attachments/assets/ecce267d-61b6-4cc3-a36d-6bc9054595b0)

![image](https://github.com/user-attachments/assets/a87ce43c-2fe0-4c3f-b739-7c4b676f10aa)





5. D-Flipflop Constant 5 with Synchronous Reset

The verilog code for the synchronous reset is given below :
```
module dff_const5(input clk, input reset, output reg q); 
	reg q1;

	always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b0;
			q1 <= 1'b0;
		end
		else
		begin	
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```
SYNTHESIS :
This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog dff_const5.v
```
Synthesize the Design
```
synth -top dff_const5
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```
![image](https://github.com/user-attachments/assets/b97261df-2941-43ae-b249-79ba557a8d4d)

![image](https://github.com/user-attachments/assets/c656bc71-9169-4c7c-b215-32edc0b63a82)

OBSERVATION : This module defines a D flip-flop that resets both q and q1 to 0 on a positive edge of reset. On each clock cycle, it sets q1 to 1 and then updates q with the value of q1 (which will always be 1 after the first cycle).
When synthesized, the design will result in a flip-flop where q is always 1 after the first clock cycle post-reset.

6. Counter Optimization 1

The verilog code for the Counter Optimization 1 is given below :
```
module counter_opt (input clk, input reset, output q);
	reg [2:0] count;
	assign q = count[0];
	
	always @(posedge clk,posedge reset)
	begin
		if(reset)
			count <= 3'b000;
		else
			count <= count + 1;
	end
endmodule
```
SYNTHESIS :

This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog counter_opt.v
```
Synthesize the Design
```
synth -top counter_opt
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```
![image](https://github.com/user-attachments/assets/09372305-d92d-4551-8a00-871d7bdaf20b)

![image](https://github.com/user-attachments/assets/d9ef7bec-70d7-41a2-97b8-05995ad141b3)

7. Counter Optimization 2

The verilog code for the synchronous reset (active high) is given below :
```
module counter_opt2 (input clk, input reset, output q);
	reg [2:0] count;
	assign q = (count[2:0] == 3'b100);
	
	always @(posedge clk,posedge reset)
	begin
		if(reset)
			count <= 3'b000;
		else
			count <= count + 1;
	end
endmodule
```
SYNTHESIS :
This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog counter_opt2.v
```
Synthesize the Design
```
synth -top counter_opt2
```
Now Generate the Netlist
```
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/b5edf0a6-1415-4379-9db8-e648ffcba11d)



![image](https://github.com/user-attachments/assets/64e6c9e1-2913-4ce5-b8b2-1a442496b395)


</details>

<details>
<summary> Day 4 </summary>
<br>



## DAY 4: GLS, blocking vs non-blocking and Synthesis-Simulation mismatch

**Gate Level Simulation (GLS)**
Gate Level Simulation (GLS) is a crucial step in the verification process of digital circuits. It involves simulating the synthesized netlist, which is a lower-level representation of the design, using a testbench to verify its logical correctness and timing behavior. By comparing the simulated outputs to the expected outputs, GLS ensures that the synthesis process has not introduced any errors and that the design meets its performance requirements.
Sensitivity lists are crucial for accurate circuit behavior. If a sensitivity list is incomplete, it can lead to unexpected latches. Blocking and non-blocking assignments within always blocks have different execution behaviors. Incorrect use of blocking assignments can unintentionally create latches, causing synthesis and simulation mismatches. To avoid these issues, it's essential to carefully analyze circuit behavior and ensure that the sensitivity list and assignments align with the desired functionality.

![image](https://github.com/user-attachments/assets/eef2f618-6f72-482f-8690-f280e0d9f13f)



GLS Simulation

    Example 1: 2 x 1 MUX using ternary operator

Verilog code:
```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
assign y = sel?i1:i0;
endmodule
```
Command steps for Simulation:
```
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

![image](https://github.com/user-attachments/assets/ff74e3da-1421-4625-a846-95684c4629a9)

Synthesis:

This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog ternary_operator_mux.v
```
Synthesize the Design
```
synth -top ternary_operator_mux
```
Now Generate the Netlist
```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/6e412fb9-44f1-4ae7-93cb-f200d545d553)

To see the Netlist
```
write_verilog -noattr ternary_operator_mux_net.v
!gvim ternary_operator_mux_net.v
```

![image](https://github.com/user-attachments/assets/6c83bf5e-b5ff-42de-8d4a-18276ff825ad)

Gate Level Synthesis (GLS)
Command steps :

We just need to put few commands as stated below in order to see the waveforms.
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
Below is the Snapshot of the above commands and the resultant Waveforms:

![image](https://github.com/user-attachments/assets/dbde8378-0af6-42d8-844a-2859b66ab8e7)


These waveforms correspond to the GATE LEVEL SYNTHESIS for the Ternary Operator MUX.


Example 2: Design of a 2:1 Bad MUX

Verilog code:
```
module bad_mux(input i0, input i1, input sel, output reg y);
	always@(sel)
	begin
		if(sel)
			y <= i1;
		else
			y <= i0;
	end
endmodule
```
Command steps for Simulation:
```
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```


![image](https://github.com/user-attachments/assets/ee80d8cc-8768-41a8-a1c1-a50f7222bc12)

From the waveform it can be observed that the output y changes only when there is a change in select line, completely ignoring the change in i0 and i1, which should also change the output y. Thus, this design is that of a bad MUX.

Synthesis:

This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog bad_mux.v
```
Synthesize the Design
```
synth -top bad_mux
```
Now Generate the Netlist
```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/f3e785c5-96e2-4bf9-be49-e8e3c430ad30)

To see the Netlist
```
write_verilog -noattr bad_mux_net.v
!gvim bad_mux_net.v
```

![image](https://github.com/user-attachments/assets/13d155dd-0986-41e1-980c-b0154d35a6fa)

From the waveform it can be observed that the output y changes only when there is a change in select line, completely ignoring the change in i0 and i1, which should also change the output y. Thus, this design is that of a bad MUX.

Gate Level Synthesis (GLS)
Command steps :

We just need to put few commands as stated below in order to see the waveforms.
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux.v tb_bad_mux.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_bad_mux.vcd
```
Below is the Snapshot of the above commands and the resultant Waveforms:

![image](https://github.com/user-attachments/assets/935b69ad-698d-4228-a621-35fe65cb7098)

These waveforms correspond to the GATE LEVEL SYNTHESIS for the Bad MUX.


Example 3: Blocking Caveat

Verilog code:
```
module blocking_caveat(input a, input b, input c, output reg d);
	reg x;

	always@(*)
	begin
		d = x & c;
		x = a | b;
	end
endmodule
```
Command steps for Simulation:
```
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```

![image](https://github.com/user-attachments/assets/2b20f7f7-8782-44fe-8af1-455274251aaf)

As depicted, when A and B go zero, the OR gate output should be zero (X equal to zero), and the AND gate output should also be zero (same as D output). But, the AND gate input of X takes the previous value of A|B equal to one, based on the design created by the blocking statement, hence the discrepancy in the output.

Synthesis:

This will invoke/start the yosys
```
yosys       
```
Read the library
```
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
Read the design verilog files
```
read_verilog blocking_caveat.v
```
Synthesize the Design
```
synth -top blocking_caveat
```
Now Generate the Netlist
```
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```
Now let's Create a Graphical Representation
```
show
```

![image](https://github.com/user-attachments/assets/24440234-449a-4fa9-a6a4-68f74c187987)

To see the Netlist

write_verilog -noattr blocking_caveat_net.v
!gvim blocking_caveat_net.v

![image](https://github.com/user-attachments/assets/7de845bd-d004-472c-aeb5-3a3aabb6c497)

Gate Level Synthesis (GLS)
Steps:

We just need to put few commands as stated below in order to see the waveforms.
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
ls
```
After giving the above command the IVerilog stores the output as ' a.out '

Now let's execute the ' a.out ' file and observe the waveforms.
```
./a.out
gtkwave tb_blocking_caveat.vcd
```
Below is the Snapshot of the above commands and the resultant Waveforms:

![image](https://github.com/user-attachments/assets/90aa6f48-b1fd-47e7-b04f-e24fc2cb3761)

These waveforms represent the results of the Gate Level Synthesis for the Blocking Caveat, illustrating how the design behaves at the gate level with respect to the blocking assignment issue.

</details>
</details>

<details>
<summary> LAB 9 </summary>
<br>

## Synthesis of RISC-V using yosys and Post synthesis simulation of Babysoc using iverilog GTKwave

In the Post synthesis simulation design flow we synthesize the generated RTL code of RISC-V and after that we will simulate the result. This way we can find more about our code and its bugs. So in this section we are going to synthesize our code then do a post-synthesis simulation to look for any issues. The post and pre (modeling section) synthesis results should be identical.

To perform the synthesis process do the following:




![T1](https://github.com/user-attachments/assets/c67cc4c9-0fa9-437d-a9f7-1d5ebc41c632)





![T2](https://github.com/user-attachments/assets/5e9cebd6-283a-4748-8feb-0198ab4b8f79)






```
cd ~/VSDBabySoC/src
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -lib ../lib/avsddac.lib
read_liberty -lib ../lib/avsdpll.lib  
read_verilog ../module/vsdbabysoc.v
read_verilog ../module/rvmyth_pri.v
read_verilog ../module/clk_gate.v 
synth -top vsdbabysoc
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr vsdbabysoc.synth.v
```

These commands will generate the vsdbaby soc top level netlist file vsdbabysoc.synth.v which can be used for the post synthesis simulation of the RISC-V processor. The synthesized module is shown below:


![image](https://github.com/user-attachments/assets/4f476cb8-d50f-43f5-abfd-9580ffade9b0)



![image](https://github.com/user-attachments/assets/d0f005f9-843a-4a53-bab3-8a433965b7a2)


Below screenshots shows the synthesis output report,




![T3](https://github.com/user-attachments/assets/7ac48d86-20d1-46c3-ae6d-2451fa30e712)


![T4](https://github.com/user-attachments/assets/c8b108cd-7d7b-4118-aebd-6ff91305aa4b)

The testbench has been changed to :

![image](https://github.com/user-attachments/assets/c01e2900-9901-409e-b498-e7a6e1db11aa)





Now let`s Observe the output waveform of synthesised RISC-V

Below screenshot shows the output waveform more zoomed-in,

![T6](https://github.com/user-attachments/assets/cb2f25de-648d-4d63-82d8-e56dfc360447)



![T7](https://github.com/user-attachments/assets/d5e2fee4-4eb0-4ffb-bbd5-6ec5c649c19d)


If we compare the above waveforms with the pre synthesis waveforms, we can observe that the results are same.

Below is the screenshot which shows output waveform for simulation before synthesis,

```
cd ~
cd VSDBabySoC
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd
```


![T8](https://github.com/user-attachments/assets/1cb67204-493f-49be-9c5e-27e819072507)

Below screenshot shows the output waveform more zoomed-in,

![T9](https://github.com/user-attachments/assets/c3465305-cc67-49de-8346-2cda686493bf)


Standard cells in gtkwave






![t1-overlay (1)](https://github.com/user-attachments/assets/cc44d5c8-4f8b-46a2-a7dc-cbfc51de429c)







In the above waveforms, we can see the following signals:

cpu_clk_har_a0: This is the input CLOCK signal of the RVMYTH core. This signal comes from the PLL.

reset: This is the input reset signal of the RVMYTH core. This signal comes from an external source, originally. Here it is generated by the testbench

RV_to_DAC[9:0]: This is the 10-bit output RV_to_DAC[9:0] port of the RVMYTH core. This port comes from the RVMYTH register.

OUT: This is a real datatype wire which can simulate analog values. It is the output wire real OUT signal of the DAC module. This signal comes from the DAC.

**Observation :** We can observed that the waveforms for pre_synth_simulation and post_synth_simulation i.e after using Yosys synthesis are the same. Hence we can observe sum of 1 to 9 as 2D. Hence output O1 = O2



</details>


<details>
<summary> LAB 10 </summary>
<br>

## Static Timing Analysis for Synthesized VSDBabySoC using OpenSTA

Static Timing Analysis (STA) is a method used in digital circuit design to verify the timing performance of a circuit without requiring dynamic simulation. It checks whether the circuit meets its timing constraints by analyzing the timing paths in the design. Here are some key aspects of STA:

    Timing Paths: STA evaluates all possible paths through a circuit from input to output, taking into account the propagation delays of gates and interconnects.

    Setup and Hold Times: It checks for setup and hold time violations. The setup time is the minimum time before the clock edge that the input data must be stable, while the hold time is the minimum time after the clock edge that the data must remain stable.

    Clock Constraints: STA incorporates clock definitions, including the clock frequency, period, and any variations (like skew or jitter).

    Worst-case Scenario: STA assumes worst-case conditions for delay values (like maximum load, temperature, and voltage) to ensure that the circuit will perform correctly under all expected operating conditions.

    Tools: There are various tools for performing STA, such as Synopsys PrimeTime, Cadence Tempus, and others, which automate the process and provide detailed reports on timing violations.

Overall, STA is crucial for ensuring that digital circuits operate reliably at the intended speeds and for identifying potential timing issues early in the design process.

Timing Checks:

    Setup Check: Ensures data arrives before the clock edge, allowing sufficient time for stabilization.
    Hold Check: Ensures data remains stable long enough after the clock edge.

Timing Margins and Slack:

    Slack: The difference between the required time and the actual arrival time of signals. Positive slack means timing constraints are met, while negative slack indicates a timing violation.
    Setup Slack: Time margin for setup constraints.
    Hold Slack: Time margin for hold constraints.
    Static Timing Tools: STA tools, like Synopsys PrimeTime and Cadence Tempus, perform analysis by creating and traversing timing graphs that represent all paths in the design. These tools provide reports on slack, critical paths, and timing violations.

Process, Voltage, and Temperature (PVT) Corners: STA includes PVT analysis to account for variations in manufacturing, operational voltages, and temperature ranges. STA ensures that timing constraints are met across worst-case PVT corners.

Optimization Techniques:

    Buffer Insertion: Adds buffers to reduce delay in long paths.
    Gate Sizing: Resizes gates to improve timing on critical paths.
    Clock Tree Optimization (CTO): Minimizes skew and jitter in the clock distribution network. By ensuring that timing analysis is thorough and covers all potential scenarios, STA plays a crucial role in achieving reliable and high-performance ASIC designs.

reg2reg Path:

A reg2reg path (register-to-register path) refers to a timing path in a digital circuit that connects two sequential elements, specifically flip-flops or registers. This path is crucial in the context of Static Timing Analysis (STA) because it represents the flow of data from one register to another through combinational logic.

Reg2reg paths are essential for ensuring proper data flow and synchronization in digital circuits, especially in designs with pipelining or sequential operations. Analyzing these paths helps in verifying that the data processing occurs correctly across clock cycles, thereby ensuring the overall functionality and reliability of the circuit.
clk2reg Path:

A clk2reg path (clock-to-register path) refers to a timing path in a digital circuit that connects the clock signal to a register (flip-flop). This path is crucial for ensuring that the register operates correctly in response to clock events.

# Installation of Required Tools:

1. Install CUDD:

Download and move the file to the home directory for easy access:
```
cd ~
tar xvfz cudd-3.0.0.tar.gz
cd cudd-3.0.0
./configure
make
```
2. Set up OpenSTA: Ensure system update and installation of dependencies:
```
cd ~
sudo apt-get install cmake clang gcc tcl swig bison flex -y
```

Clone OpenSTA repository and build with CUDD support:
```
git clone https://github.com/parallaxsw/OpenSTA.git
cd OpenSTA
cmake -DCUDD_DIR=/home/harsh-verma/cudd-3.0.0
make
app/sta
```

Create a new directory for lab setup:
```
mkdir ~/OpenSTA/lab10
```

Move all necessary files into lab10 directory for timing analysis.
Timing Analysis Procedure:

Ensure the following parameters for analysis:

    Clock period: 10.25 ns
    Setup uncertainty & clock transition: 5% of clock period
    Hold uncertainty & data transition: 8% of clock period

```
cd /home/harsh-verma/OpenSTA/app
./sta

read_liberty /home/harsh-verma/OpenSTA/lab10/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog /home/harsh-verma/OpenSTA/lab10/harsh_riscv_netlist.v
link_design rvmyth

create_clock -name clk -period 10.25 [get_ports clk]
set_clock_uncertainty [expr 0.05 * 10.25] -setup [get_clocks clk]
set_clock_uncertainty [expr 0.08 * 10.25] -hold [get_clocks clk]
set_clock_transition [expr 0.05 * 10.25] [get_clocks clk]
set_input_transition [expr 0.08 * 10.25] [all_inputs]

report_checks -path_delay max
report_checks -path_delay min
```

To execute the OpenSTA and obtain the timing reports, run the below command,
```
sta scripts/sta.conf
```
Following are contents of the sta.conf file,
```
read_liberty -min ./lib/sta/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -max ./lib/sta/sky130_fd_sc_hd__tt_025C_1v80.lib
read_liberty -min ./lib/avsdpll.lib
read_liberty -max ./lib/avsdpll.lib
read_liberty -min ./lib/avsddac.lib
read_liberty -max ./lib/avsddac.lib
read_verilog ./src/module/vsdbabysoc_synth.v
link_design vsdbabysoc
read_sdc ./src/sdc/sta_post_synth.sdc
```

Terminal Output:



![l11](https://github.com/user-attachments/assets/e24532a5-f97f-457e-a0ce-d97c60167ac8)


In the below screenshot, we can observe the timing report for a reg2reg max path,



![l10](https://github.com/user-attachments/assets/e9994952-e0df-4939-a2a7-6fd30da41cf8)

Below screenshot shows the reg2reg min path report,




![l10min](https://github.com/user-attachments/assets/a1e6bcde-f88a-4c88-98aa-b61043d66562)

The max path report is for the Setup Slack and the min path report is for the Hold Slack.
We can conclude that the timing constraints are not met for our design by observing the OpenSTA Timing reports.




</details>



<details>
<summary> LAB 11 </summary>
<br>

# PVT Corner Analysis for Synthesized VSDBabySoC using OpenSTA

The PVT corner refers to the combination of Process, Voltage, and Temperature variations that a semiconductor chip might encounter during its operation. These variations can affect the performance, power consumption, and reliability of the chip, so they are simulated to ensure the chip functions correctly under different conditions. The below tcl script sta_pvt.tcl can be run to perform the STA across the PVT corners for which the sky130 lib files are available: The script is


![2](https://github.com/user-attachments/assets/b64f7df1-ef32-4df9-8c29-7b0cfe33a14f)


The SDC file used for generating clock and data constraints is given below:
## SDC constraints for VSDBabySoC



![3](https://github.com/user-attachments/assets/f891ef51-669d-4adb-80a0-289fd4feb6e4)


Analysis Report
## table of slack report:



![table](https://github.com/user-attachments/assets/f29cac3b-0737-4191-913a-3055ae9efae5)

Total Negative Slack:



![4](https://github.com/user-attachments/assets/832a6d6d-f9f8-4793-8659-e7a01daf1078)

Worst (Negative slack)Setup Slack:



![5wns](https://github.com/user-attachments/assets/bc464119-cbbb-47c0-8fc4-12802652c738)


Worst Setup Slack:


![6wns](https://github.com/user-attachments/assets/4181460a-73a6-4825-9c4f-ec82224dbdfe)

Worst Hold Slack:




![7](https://github.com/user-attachments/assets/74554ac4-b9e7-4702-a339-e32f968cf748)


The analysis report shows the following key points:

    Worst Setup Slack: sky130_fd_sc_hd__ss_n40C_1v28.lib library file has the worst setup slack.
    Worst Hold Slack: sky130_fd_sc_hd__ff_100C_1v95.lib library file has the worst hold slack.

The total negative slack and worst negative slacks are provided in the detailed slacks report screenshots.



</details>

<details>
<summary> LAB 12 </summary>
<br>

# Advanced Physical Design Using Openlane/Sky130 Wokshop

 ## Day 1 - Introduction to open-source EDA, OpenLANE and Sky130 PDK

1) Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs. Commands to invoke the OpenLANE flow and perform synthesis

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

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```




![Screenshot from 2024-11-12 23-39-04](https://github.com/user-attachments/assets/9a850654-7f17-461e-ab81-7278beb5da13)





![Screenshot from 2024-11-12 23-43-59](https://github.com/user-attachments/assets/e3c14452-721e-467c-8b32-856da2867af5)



![Screenshot from 2024-11-12 23-56-41](https://github.com/user-attachments/assets/ffbe07e1-c7ea-4c64-b279-e79739992b14)



![Screenshot from 2024-11-12 23-59-48](https://github.com/user-attachments/assets/4b0d1482-70b0-40f0-a9e5-0497306d342c)



![Screenshot from 2024-11-13 00-01-15](https://github.com/user-attachments/assets/e6952486-c73a-436b-b6bb-85132235ed2f)


![Screenshot from 2024-11-15 04-34-22](https://github.com/user-attachments/assets/249110bf-3512-42c1-8667-5298f5122922)


![Screenshot from 2024-11-15 04-35-47](https://github.com/user-attachments/assets/1b7916c9-1d63-4b84-88a9-35331762afba)









Calculation of Flop Ratio and DFF % from synthesis statistics report file
```
Flop Ratio = 1613/14876 = 0.108429685
    Percentage of Flip Flops = 0.108429685 ∗ 100 = 10.84296854%
```

##  Day2: Good Floorpan vs Bad Floorplan and Introduction to Library Cell

Tasks:

    Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
    Calculate the die area in microns from the values in floorplan def.
    Load generated floorplan def in magic tool and explore the floorplan.
    Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
    Load generated placement def in magic tool and explore the placement. Area of Die in microns = Die width in microns ∗ Die height in microns

1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs

Commands to invoke the OpenLANE flow and perform floorplan
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

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Screenshot of floorplan run


![Screenshot from 2024-11-13 00-13-42](https://github.com/user-attachments/assets/08c68b21-f0df-427a-8e65-e8d767440d7e)




![Screenshot from 2024-11-13 00-15-26](https://github.com/user-attachments/assets/55eddc9b-f5d6-47c7-9652-16d5de493797)


2. Calculate the die area in microns from the values in floorplan def.


![Screenshot from 2024-11-13 00-24-10](https://github.com/user-attachments/assets/b327e08e-7794-4ba7-85da-3e83658c10f7)


![Screenshot from 2024-11-13 00-25-15](https://github.com/user-attachments/assets/aba5a087-637a-4f35-9f74-a1f57aafba2b)

According to Floorplan def

    Load generated floorplan def in magic tool and explore the floorplan. Commands to load floorplan def in magic in another terminal

```

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
Screenshots of floorplan def in magic



![Screenshot from 2024-11-13 00-32-32](https://github.com/user-attachments/assets/58d5ce1c-4631-45ac-b897-ad9cd4a2627f)


Equidistant placement of ports
![Screenshot from 2024-11-13 00-48-45](https://github.com/user-attachments/assets/a7898ea3-916e-4929-a4e5-0cd2da7724fd)


Port layer as set through config.tcl


![Screenshot from 2024-11-13 00-58-57](https://github.com/user-attachments/assets/112663e6-9344-484d-9225-768e781283b0)


Decap Cells and Tap Cells

![WhatsApp Image 2024-11-13 at 16 56 20](https://github.com/user-attachments/assets/c2be0507-c0d3-4d08-bd78-3c0eb1cd9ef0)

Diagonally equidistant Tap cells

cell in columns of different are diagoanlly equidistant

![Screenshot from 2024-11-13 17-01-01](https://github.com/user-attachments/assets/3ec779fe-f189-4f38-a5b2-5e3d559a396c)

Unplaced standard cells at the origin

![Screenshot from 2024-11-13 17-05-58](https://github.com/user-attachments/assets/7de971f3-aa4e-48dc-98df-aadccebfe7f1)


    Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs. Command to run placement

# Congestion aware placement by default
```
run_placement
```


![Screenshot from 2024-11-13 17-11-41](https://github.com/user-attachments/assets/6277415e-c4c3-4650-b302-0e597666dde0)

To view the placement in magic:

![Screenshot from 2024-11-13 17-15-40](https://github.com/user-attachments/assets/3f3b2490-bdaf-438e-89d7-442d28aa4342)


![WhatsApp Image 2024-11-13 at 17 19 44](https://github.com/user-attachments/assets/4f17d52c-e1cb-43de-8af3-c803a4daabee)

![image](https://github.com/user-attachments/assets/bbf8aab8-cb49-464c-acb2-de043d77c6d8)



Commands to exit from current run
```
exit # Exit from OpenLANE flow
exit # Exit from OpenLANE flow docker sub-system
```


 # Day3: Design Library Cell Using Magic Layout and Cell characterization

Tasks:
```
    Clone custom inverter standard cell design from github repository: Standard cell design and characterization using OpenLANE flow.
    Load the custom inverter layout in magic and explore.
    Spice extraction of inverter in magic.
    Editing the spice model file for analysis through simulation.
    Post-layout ngspice simulations.
    Find problem in the DRC section of the old magic tech file for the skywater process and fix them.
```

    Clone custom inverter standard cell design from github repository

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
magic -T sky130A.tech sky130_harinv.mag &

![Screenshot from 2024-11-13 22-18-00](https://github.com/user-attachments/assets/fb569717-a21a-4fb3-89fa-3820f94ff890)




Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic
![Screenshot from 2024-11-13 22-18-46](https://github.com/user-attachments/assets/9ae595ae-80d3-4543-9397-caa4e88432e8)



nmos, pmos identified


![Screenshot from 2024-11-13 22-23-20](https://github.com/user-attachments/assets/cb2b33ae-6901-4369-8a8a-72c29c41296f)



![Screenshot from 2024-11-13 22-22-49](https://github.com/user-attachments/assets/a6373a03-670b-4110-9d93-34fa588ea8cf)



Output Y connectivity to PMOS and NMOS drain verified

![Screenshot from 2024-11-13 22-24-27](https://github.com/user-attachments/assets/1a384b6e-c8fa-4f87-a038-22ba49dfeea9)



PMOS source connectivity to VDD (here VPWR) verified
![Screenshot from 2024-11-13 22-26-05](https://github.com/user-attachments/assets/f3affaf3-f3bd-4547-bd63-8b1d38402447)


NMOS source connectivity to VSS (here VGND) verified
![Screenshot from 2024-11-13 22-27-27](https://github.com/user-attachments/assets/23ceabc5-5df6-4d62-a7ff-b0aa20837722)



Deleting necessary layout part to see DRC error
![Screenshot from 2024-11-13 22-33-39](https://github.com/user-attachments/assets/3428113d-bef7-4bb2-8930-9faf4ec333dd)




Spice extraction of inverter in magic.

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

![Screenshot from 2024-11-13 18-27-45](https://github.com/user-attachments/assets/d666df1e-dc06-47c5-85eb-c8c247791113)


Screenshot of created spice file


![Screenshot from 2024-11-13 20-05-11](https://github.com/user-attachments/assets/468368ea-e88d-45c9-8b1b-25c4c0cff9f5)

![WhatsApp Image 2024-11-14 at 19 34 14](https://github.com/user-attachments/assets/c6108854-aeb2-4c6e-b7d4-5fd8ba6bc3e5)






Simulate the spice netlist
```
ngspice sky130_inv.spice
```

![Screenshot from 2024-11-13 20-07-54](https://github.com/user-attachments/assets/31f9402f-682a-468c-9312-be1b63df0eb5)







Screenshot of generated plot
```
plot y vs time a
```

![Screenshot from 2024-11-14 19-40-38](https://github.com/user-attachments/assets/82840102-0e6f-42fb-9b37-995d6bd98f9b)











![Screenshot from 2024-11-13 23-08-42](https://github.com/user-attachments/assets/cd6566aa-0bf9-42de-acfe-d8a896f68092)


Using this transient response, we will now characterize the cell's slew rate and propagation delay:
Rise Transition: Time taken for the output to rise from 20% to 80% of max value Fall Transition: Time taken for the output to fall from 80% to 20% of max value Cell Rise delay: difference in time(50% output rise) to time(50% input fall) Cell Fall delay: difference in time(50% output fall) to time(50% input rise)

Cell Characterization: Slew Rate and Propagation Delay

To characterize the cell's transient response, we will measure its slew rate and propagation delay as follows:

    Rise Transition
    The time required for the output to rise from 20% to 80% of its maximum value.

    Fall Transition
    The time required for the output to fall from 80% to 20% of its maximum value.

    Cell Rise Delay
    The time difference between the input falling to 50% of its amplitude and the output rising to 50%.

    Cell Fall Delay
    The time difference between the input rising to 50% of its amplitude and the output falling to 50%.

maxm value:3.3V

20% screenshot image
Rise transition time calculation Rise Transition Time = Time taken for output to rise to 80% − Time taken for output to rise to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

![Screenshot from 2024-11-14 20-22-39](https://github.com/user-attachments/assets/c5f886d9-3ed8-4eeb-bda5-2cf918051174)



80% Screenshot

![Screenshot from 2024-11-14 20-26-53](https://github.com/user-attachments/assets/c740fac5-fd5b-413d-a9b8-24367efed084)

Rise Transition Time = 2.2394 - 2.1803 = 0.05639 ns = 56.39 ps

Fall Transition Time = Time taken for output to fall to 80% − Time taken for output to fall to 20% 20% of output (3.3V) = 0.66V 20% of output (3.3V) = 2.64V

20% Screenshots

![Screenshot from 2024-11-14 20-28-24](https://github.com/user-attachments/assets/f9baa042-8035-4df5-ab68-ec793a7b8543)


80% Screenshots

![Screenshot from 2024-11-14 20-29-30](https://github.com/user-attachments/assets/73b663b0-93f2-4227-bf2a-0b72550c63a5)


Fall Transition Time = 4.09266 - 4.05061 = 0.04205 ns = 42.05 ps

Rise Cell Delay Calculation Rise cell delay = Time taken by output to rise to 50% − Time taken by input to fall to 50% 50 % of 3.3V = 1.65V


50% Screenshot


![Screenshot from 2024-11-14 20-31-54](https://github.com/user-attachments/assets/2db60464-6ef4-45e5-b8e5-a1ace8d793de)

Rise cell delay = 2.20667 - 2.15061 = 0.05599 ns = 55.99 ps

Fall Cell Delay Calculation Fall cell delay = Time taken by output to fall to 50% − Time taken by input to rise to 50% of 3.3V = 1.65V


![Screenshot from 2024-11-14 20-35-41](https://github.com/user-attachments/assets/57139420-e3ab-4583-9c4d-efc7791c85a6)

Fall cell delay = 4.07494 - 4.04966 = 0.02528 ns = 25.28 ps

Magic Tool options and DRC Rules:

Go to home directory and run the below commands:
```
cd
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
tar xfz drc_tests.tgz
cd drc_tests
ls -al
gvim .magicrc
magic -d XR &
```


![Screenshot from 2024-11-13 23-13-16](https://github.com/user-attachments/assets/b0d236a9-0d4a-464b-84e8-8a5c3c6d93c5)

Screenshot of .magicrc file

![Screenshot from 2024-11-13 23-15-39](https://github.com/user-attachments/assets/4b0d87c6-1a62-46b8-bba6-fc7efb0c33e7)






![WhatsApp Image 2024-11-13 at 20 20 39](https://github.com/user-attachments/assets/f33ac531-6a4d-4057-9e76-74b9af537f9e)

![Screenshot from 2024-11-13 23-29-01](https://github.com/user-attachments/assets/7dba07bd-f0fa-44a8-860c-a982bc579493)

Incorrectly implemented poly.9 simple rule correction

Screenshot of poly rules

Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u


![WhatsApp Image 2024-11-13 at 20 23 38](https://github.com/user-attachments/assets/c61528d9-b5fb-4ca4-80fa-44ad586bc3d6)


Correction of Incorrectly Implemented poly.9 Rule
The poly.9 rule was not implemented correctly, requiring a simple correction. Please refer to the screenshot of the poly rules for specific details on the intended rule structure and constraints.

![Screenshot from 2024-11-13 20-34-34](https://github.com/user-attachments/assets/05819837-9360-4e3c-a327-14ba70c88e06)

![WhatsApp Image 2024-11-13 at 20 36 53](https://github.com/user-attachments/assets/5b14b329-0621-41a8-9b79-fec41bd439e0)


Run the commands in tkcon window:
```
tech load sky130A.tech
drc check
drc why
```


![WhatsApp Image 2024-11-13 at 20 58 51](https://github.com/user-attachments/assets/3f153e96-6cab-4254-88d5-7595b73692e4)


![WhatsApp Image 2024-11-14 at 20 41 12](https://github.com/user-attachments/assets/e4d13aaf-17dc-4597-8d15-611142530f63)



![WhatsApp Image 2024-11-14 at 20 42 05](https://github.com/user-attachments/assets/cfdebcc9-68d8-48fd-ae6e-584b31186419)

![WhatsApp Image 2024-11-14 at 20 42 46](https://github.com/user-attachments/assets/452b6703-cfa6-4156-a8c0-d744b344b9d8)





New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-11-13 22-01-13](https://github.com/user-attachments/assets/46be59f9-11c8-4269-a3e5-c5c86c114465)


Commands to run in tkcon window

# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why


Incorrectly implemented nwell.4 complex rule correction


Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell


![image](https://github.com/user-attachments/assets/cd87ab75-7421-4bae-b6a6-c150ebd427b6)



New commands inserted in sky130A.tech file to update drc

![Screenshot from 2024-11-14 00-07-27](https://github.com/user-attachments/assets/a2682127-36ff-41d6-b015-bf79c862a195)



![Screenshot from 2024-11-14 00-17-36](https://github.com/user-attachments/assets/b606f159-c7bb-4741-8ead-f49aa7112aa9)


Incorrectly implemented difftap.2


![Screenshot from 2024-11-14 23-22-58](https://github.com/user-attachments/assets/20c405e8-ff06-4a46-802b-f09ff563be9b)







# Day 4 - Pre-layout timing analysis and importance of good clock tree 



    Fix up small DRC errors and verify the design is ready to be inserted into our flow.

    Save the finalized layout with custom name and open it.

    Generate lef from the layout.

    Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

    Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

    Run openlane flow synthesis with newly inserted custom inverter cell.

    Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

    Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

    Do Post-Synthesis timing analysis with OpenSTA tool.

    Make timing ECO fixes to remove all violations.

    Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

    Post-CTS OpenROAD timing analysis.

    Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

    Fix up small DRC errors and verify the design is ready to be inserted into our flow. Conditions to be verified before moving forward with custom designed cell layout:

Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks. Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch. Condition 3: Height of the standard cell should be even multiples of the vertical track pitch. Commands to open the custom inverter layout
```

cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_harinv.mag &
```
Screenshot of tracks.info of sky130_fd_sc_hd

![Screenshot from 2024-11-14 00-39-05](https://github.com/user-attachments/assets/851376d9-5d8f-4b3b-bfe1-bcba4af2ea3d)

Commands for tkcon window to set grid as tracks of locali layer
```
help grid
grid 0.46um 0.34um 0.23um 0.17um
```
Screenshot of commands run

![Screenshot from 2024-11-14 00-42-56](https://github.com/user-attachments/assets/eda9a89c-e1f4-4c17-8985-3ae97cce995d)

Condition 1 verified

![Screenshot from 2024-11-14 00-58-25](https://github.com/user-attachments/assets/286df697-6dc9-4a0c-b111-e712eb25cff1)

Condition 2 verified


![Screenshot from 2024-11-14 01-01-21](https://github.com/user-attachments/assets/ba6008a0-b401-4299-adea-a6f64c45b35a)

Condition 3 verified



![WhatsApp Image 2024-11-15 at 00 54 38](https://github.com/user-attachments/assets/1ce710a9-59cf-4c07-981b-eac7a394c02f)



2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name
```
# Command to save as
save sky130_harinv.mag

Command to open the newly saved layout

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_harinv.mag &
```
Screenshot of newly saved layout

![Screenshot from 2024-11-14 02-33-21](https://github.com/user-attachments/assets/89ec0edb-ddb0-4303-aeb1-236c3cafc321)

Screenshot of newly created lef file

![Screenshot from 2024-11-14 02-34-48](https://github.com/user-attachments/assets/bc631739-d04d-4f1b-b614-187c38425941)

4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
Commands to copy necessary files to 'picorv32a' design 'src' directory

![Screenshot from 2024-11-14 02-47-02](https://github.com/user-attachments/assets/2457ea52-7cb2-4513-a79a-bdadbdb4c811)

 Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow
```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```
Edited config.tcl to include the added lef and change library to ones we added in src directory

![Screenshot from 2024-11-14 03-19-55](https://github.com/user-attachments/assets/1d69a125-557e-4695-bb22-93b148397b65)


Run openlane flow synthesis with newly inserted custom inverter cell.

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
![Screenshot from 2024-11-14 03-23-23](https://github.com/user-attachments/assets/d1b8b393-c02a-4dd9-9c08-e837307399c7)

![Screenshot from 2024-11-14 03-25-02](https://github.com/user-attachments/assets/2359133d-facc-4572-baf5-04609eb6d991)

Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
Noting down current design values generated before modifying parameters to improve timing

![Screenshot from 2024-11-14 03-26-34](https://github.com/user-attachments/assets/93ec6979-4cd1-4ac3-b873-f90a533e2657)

![Screenshot from 2024-11-14 03-26-58](https://github.com/user-attachments/assets/c58d5c9d-0907-4c87-ad9f-f0262f4d4639)

Commands to view and change parameters to improve timing and run synthesis
```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

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



![Screenshot from 2024-11-14 03-28-39](https://github.com/user-attachments/assets/cc1b34b0-db26-45cf-8ae1-df2399b607c6)


![Screenshot from 2024-11-14 03-30-57](https://github.com/user-attachments/assets/92e3f357-7972-41eb-9e56-f10eb43a84c2)

![Screenshot from 2024-11-14 03-31-58](https://github.com/user-attachments/assets/7f6f8aa9-8652-4300-93d6-649226055f85)

Screenshot of merged.lef in tmp directory with our custom inverter as macro


![Screenshot from 2024-11-14 03-35-01](https://github.com/user-attachments/assets/0824b4e7-a6c4-4447-99b0-4e21b28dc016)


![Screenshot from 2024-11-14 03-35-04](https://github.com/user-attachments/assets/39361cce-c64e-4027-8425-ebbb7f28a76a)

Comparing to previously noted run values area has increased and worst negative slack has become 0

![Screenshot from 2024-11-14 03-36-16](https://github.com/user-attachments/assets/b3f67051-fb86-4ff0-bf45-2a793d4da8d8)


![Screenshot from 2024-11-14 03-36-50](https://github.com/user-attachments/assets/59e25bd0-c51d-4b1a-a33d-ca0c553fbea2)

Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command
```
# Now we can run floorplan
run_floorplan
```
Screenshots of command run

![Screenshot from 2024-11-14 03-37-54](https://github.com/user-attachments/assets/c5b213f8-7a94-4f9f-bfbc-6161fb2a5e12)
![Screenshot from 2024-11-14 03-38-19](https://github.com/user-attachments/assets/be9ae8df-ee69-429d-9761-3fe34abdb8f7)


Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands available based on information from Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl and also based on Floorplan Commands section in Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md
```
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```


![Screenshot from 2024-11-14 03-39-44](https://github.com/user-attachments/assets/240879cf-5204-489b-a4a0-cc23b068a354)


![Screenshot from 2024-11-14 03-39-46](https://github.com/user-attachments/assets/d1e9d256-b304-4530-ae84-866827bf3d78)

Now that floorplan is done we can do placement using following command
```
# Now we are ready to run placement
run_placement
```
Screenshots of command run


![Screenshot from 2024-11-14 03-41-27](https://github.com/user-attachments/assets/c69bfd6e-825b-4c93-9a8d-d6894f316003)

Commands to load placement def in magic in another terminal
```
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
Screenshot of placement def in magic


![Screenshot from 2024-11-14 03-44-35](https://github.com/user-attachments/assets/b1667c2e-5a4e-4434-9fdb-043eedbd8b88)

Command for tkcon window to view internal layers of cells
```
# Command to view internal connectivity layers
expand
```
Custom inverter inserted and expanded in placement def is shown below


![WhatsApp Image 2024-11-14 at 15 00 25](https://github.com/user-attachments/assets/3e00436d-a20d-41a7-9156-d2bb31c7d22a)

for some random cell also shown

![Screenshot from 2024-11-14 03-51-59](https://github.com/user-attachments/assets/de85569e-6971-4968-b29b-cb093828b495)

Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis

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

Commands run final screenshot

![Screenshot from 2024-11-15 01-38-07](https://github.com/user-attachments/assets/8fa1207c-3f25-4e74-ba83-0f59f2cd7466)



Newly created pre_sta.conf for STA analysis in openlane directory


![Screenshot from 2024-11-15 01-43-55](https://github.com/user-attachments/assets/d9c59f0b-5a67-495a-b798-bd9c2474f0a1)




Newly created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory based on the file openlane/scripts/base.sdc

![Screenshot from 2024-11-14 04-25-07](https://github.com/user-attachments/assets/f12b6a7d-e57c-4c51-a7c8-efe6ac598557)


Commands to run STA in another terminal
```
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```
Screenshots of commands run
![Screenshot from 2024-11-15 01-42-15](https://github.com/user-attachments/assets/9759354e-8bd4-43e4-8bb1-16b4b2d31ee2)


![Screenshot from 2024-11-15 01-45-45](https://github.com/user-attachments/assets/5691878f-2022-4369-91c3-3d1a242ad3d2)



We now try to optimise synthesis.

Go to new terminal and run the follwoing commands:
```
cd Desktop/work/tools/openlane_working_dir/openlane
docker
./flow.tcl -interactive
prep -design picorv32a -tag 25-03_18-52 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_SIZING) 1
set ::env(SYNTH_MAX_FANOUT) 4
echo $::env(SYNTH_DRIVING_CELL)
run_synthesis
```
![Screenshot from 2024-11-15 01-49-41](https://github.com/user-attachments/assets/759203bb-5760-4f0a-9c84-6fb91abbf10b)






Commands to run STA:
```
cd Desktop/work/tools/openlane_working_dir/openlane
sta pre_sta.conf
```

![Screenshot from 2024-11-15 01-51-05](https://github.com/user-attachments/assets/7eef7c0e-24d2-49c7-8fe9-8a9ee206871d)


![Screenshot from 2024-11-15 01-51-09](https://github.com/user-attachments/assets/1a05db17-41f7-416f-b97a-07fccb747ecf)



Basic timing ECO

NOR gate of drive strength 2 is driving 5 fanouts

![WhatsApp Image 2024-11-14 at 15 48 43](https://github.com/user-attachments/assets/14bb5ff2-d3ee-4b9b-b3e4-d38175f4a93f)

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


![Screenshot from 2024-11-15 01-59-54](https://github.com/user-attachments/assets/f6e7c922-7811-4146-86e5-37a283734ebb)



![Screenshot from 2024-11-15 02-00-24](https://github.com/user-attachments/assets/07b39aaa-0763-422c-a6ff-c24fc8047bda)

![Screenshot from 2024-11-15 02-00-28](https://github.com/user-attachments/assets/b8cfbd0a-bc28-41b3-8221-6345a481926f)


OR gate of drive strength 2 is driving 4 fanouts


![Screenshot from 2024-11-15 02-02-42](https://github.com/user-attachments/assets/f6d7b7c1-2601-46cf-9973-310fca52a7fb)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Result - slack reduced

![Screenshot from 2024-11-15 02-04-40](https://github.com/user-attachments/assets/ec72a309-dd5d-4847-9d1b-121ba3905b33)

![Screenshot from 2024-11-15 02-04-50](https://github.com/user-attachments/assets/972ea1aa-d0f6-4361-9d89-65ee4a4e2cc1)

![Screenshot from 2024-11-15 02-04-53](https://github.com/user-attachments/assets/4a4ba8d1-0929-472c-a548-be248bc90232)


OR gate of drive strength 2 driving OA gate has more delay


![Screenshot from 2024-11-15 02-05-46](https://github.com/user-attachments/assets/2381ddf7-5322-4966-9882-a1f6648e85d1)

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


![Screenshot from 2024-11-15 02-07-16](https://github.com/user-attachments/assets/87bdda82-78d9-41b7-a80a-fd2d294612c9)


![Screenshot from 2024-11-15 02-07-19](https://github.com/user-attachments/assets/a26ac221-faf5-4ae7-b4ce-cc7b066499ea)


OR gate of drive strength 2 driving OA gate has more delay

![Screenshot from 2024-11-15 02-08-03](https://github.com/user-attachments/assets/9a18835f-55db-47d7-861f-2c1c964f3d4a)


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



![Screenshot from 2024-11-15 02-09-31](https://github.com/user-attachments/assets/dcdfd86e-9af1-4ebc-9a9d-f94ce80f9452)


![Screenshot from 2024-11-15 02-09-33](https://github.com/user-attachments/assets/e43deb68-b14b-43df-b7db-c6e7775a6879)

Commands to verify instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
```
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```
Screenshot of replaced instance

![Screenshot from 2024-11-15 02-10-37](https://github.com/user-attachments/assets/90d374f4-20cc-4f6d-ad53-1bd9772f1c50)

We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use write_verilog and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist
```
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```
Screenshot of commands run


![Screenshot from 2024-11-15 02-12-56](https://github.com/user-attachments/assets/d78986dc-38dc-4020-809e-887817580e27)


Commands to write verilog
```
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

![Screenshot from 2024-11-15 02-18-05](https://github.com/user-attachments/assets/100bb6e5-8f16-47d0-8d1d-a2b38f18695d)

Verified that the netlist is overwritten by checking that instance _14506_ is replaced with sky130_fd_sc_hd__or4_4

![Screenshot from 2024-11-15 02-19-56](https://github.com/user-attachments/assets/b033e6ad-d401-4717-8d50-ca8b31159eb1)


Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages
```
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

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

![Screenshot from 2024-11-15 02-24-41](https://github.com/user-attachments/assets/b4fea824-0cdb-4e08-bb93-bb1a471046c5)

![Screenshot from 2024-11-15 02-25-33](https://github.com/user-attachments/assets/a57ebdcd-51a2-4110-b90a-76a10f46c992)

![Screenshot from 2024-11-15 02-25-46](https://github.com/user-attachments/assets/764fd47d-a2df-4ab9-bd48-ec02574e9925)


![Screenshot from 2024-11-15 02-26-00](https://github.com/user-attachments/assets/12b3376c-1271-407d-975d-fd07f7af2eef)

![Screenshot from 2024-11-15 02-26-52](https://github.com/user-attachments/assets/de6d8835-f6db-4c0e-8810-a0da4687ffd3)



![Screenshot from 2024-11-15 02-27-52](https://github.com/user-attachments/assets/641298af-a212-4047-907d-62b6da9e5dae)

 Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_20-07/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_20-07/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_20-07/results/synthesis/picorv32a.synthesis_cts.v

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


![WhatsApp Image 2024-11-15 at 02 51 14](https://github.com/user-attachments/assets/55e02735-6a16-4f49-9257-ebdd2e1c3348)


![WhatsApp Image 2024-11-15 at 02 55 45](https://github.com/user-attachments/assets/5b3a0f04-1c0d-4f52-81a4-fa05ce7317b6)


Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

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
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/14-11_20-07/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_20-07/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_20-07/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_20-07/results/synthesis/picorv32a.synthesis_cts.v

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

running these commands will give following results:

![WhatsApp Image 2024-11-15 at 02 56 56](https://github.com/user-attachments/assets/87f494a4-0fc5-4358-8477-73e4419ec41e)



![WhatsApp Image 2024-11-15 at 02 57 22](https://github.com/user-attachments/assets/7966b07f-a64f-4abf-bb06-c1c0e0c44282)


![WhatsApp Image 2024-11-15 at 02 57 53](https://github.com/user-attachments/assets/40db232b-7e6b-463b-aeaf-c07cf81b9fbe)



#  Day-5: Final steps for RTL2GDS using tritonRoute and openSTA

Theory

Implementation

Tasks:-

    Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
    Perfrom detailed routing using TritonRoute.
    Post-Route parasitic extraction using SPEF extractor.
    Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

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

![Screenshot from 2024-11-14 21-39-28](https://github.com/user-attachments/assets/d780703a-6fee-439a-8660-66e3c9d002e7)


![Screenshot from 2024-11-14 21-47-55](https://github.com/user-attachments/assets/0d8bbf9c-9153-4374-840c-f976a621d31f)

Commands to load PDN def in magic in another terminal
```
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_16-09/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```



![Screenshot from 2024-11-15 00-10-22](https://github.com/user-attachments/assets/55910f9e-c6de-40fb-8a1b-8ab451e7e552)


![Screenshot from 2024-11-15 00-22-38](https://github.com/user-attachments/assets/0e833d9e-d5a1-46be-936c-6cc55a567a9e)

![Screenshot from 2024-11-15 00-23-54](https://github.com/user-attachments/assets/ba1caebf-d5f8-40b4-a7b0-73128b3c305d)

Perfrom detailed routing using TritonRoute and explore the routed layout.

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



![1](https://github.com/user-attachments/assets/86703c23-d706-42c8-b44b-da8b18a8d6d9)


![image](https://github.com/user-attachments/assets/9357f10a-157c-4951-813e-61426702cf6e)





Commands to load routed def in magic in another terminal
```
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_22-02/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
Screenshots of routed def


![2](https://github.com/user-attachments/assets/8289d6a6-db01-47dd-b185-c979e52d8c42)




![3](https://github.com/user-attachments/assets/b8a6f0af-b1d8-42e2-8af5-df2f64869461)




![4](https://github.com/user-attachments/assets/70628c70-eee1-42d1-8f97-94a42acc0290)

Screenshot of fast route guide present in openlane/designs/picorv32a/runs/26-03_08-45/tmp/routing directory



![5](https://github.com/user-attachments/assets/e71666b8-b016-47dd-89c1-7f011ec8aac6)

Post-Route parasitic extraction using SPEF extractor.

Commands for SPEF extraction using external tool
```
# Change directory
cd Desktop/work/tools/SPEF_EXTRACTOR

# Command extract spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_22-02/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_22-02/results/routing/picorv32a.def
```
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_22-02/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_22-02/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_22-02/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/14-11_22-02/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
Screenshots of commands run and timing report generated




![6](https://github.com/user-attachments/assets/df411ed5-aef9-4338-80a3-9a30d95f1c13)


![7](https://github.com/user-attachments/assets/663521e9-4aa0-4abb-904b-2dc739fe1ca1)


![8](https://github.com/user-attachments/assets/8d389f9f-412f-4637-889f-d4eb52294c15)


![9](https://github.com/user-attachments/assets/4b0183e1-671f-40cd-8b7f-89f9fc0171e6)




</details>



<details>
<summary> LAB 13 </summary>
<br>

# OpenRoad Physical Design:

Cloning and Installing Dependencies

To set up the environment, use the setup.sh script to install all necessary dependencies, including those required for OpenROAD.
```
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
sudo ./setup.sh
```

![asic1](https://github.com/user-attachments/assets/ca833ad0-aefa-4ae3-be05-937190dd4520)

![asic2](https://github.com/user-attachments/assets/d0095a21-bffb-4265-a313-635d204d4fab)



![asic3](https://github.com/user-attachments/assets/e18d28b8-30b6-41df-8621-811880bdcb9e)

![asic4](https://github.com/user-attachments/assets/ff8b8760-d167-432f-947e-d4f7781967c2)



![asic5](https://github.com/user-attachments/assets/061a223f-f494-4e5d-9716-80b2ad304e2b)

To view the final layout in the OpenROAD GUI, use the following command:
```
make gui_final
```


![asic6](https://github.com/user-attachments/assets/e8450108-180b-4f26-a023-4661afbd1d05)

Automated RTL-to-GDS Flow for VSDBabySoC

Follow these steps to set up the VSDBabySoC design in the OpenROAD-flow-scripts environment:

    Create the Directory:
    Navigate to OpenROAD-flow-scripts/flow/designs/sky130hd and create a new folder named vsdbabysoc.

    Copy Required Files:
    Transfer the following folders and their respective contents from the VSDBabySoC directory on the system to the newly created vsdbabysoc directory:
        gds: Includes avsddac.gds and avsdpll.gds.
        include: Contains sandpiper.vh, sandpiper_gen.vh, sp_default.vh, and sp_verilog.vh.
        lef: Includes avsddac.lef and avsdpll.lef.
        lib: Contains avsddac.lib and avsdpll.lib.

    Add Constraints File:
    Copy vsdbabysoc_synthesis.sdc to the vsdbabysoc directory.

    Include Additional Configuration Files:
    Transfer macro.cfg and pin_order.cfg from the VSDBabySoC folder to the same directory.

    Prepare Macro Configuration:
    Create a macro.cfg file in the vsdbabysoc directory with the required configuration details.

By following these steps, we can set up the VSDBabySoC design for RTL-to-GDS implementation.

![asic7](https://github.com/user-attachments/assets/2c051511-56d7-454b-b51d-880aeed4af2a)



![asic8](https://github.com/user-attachments/assets/9e1d2c03-f184-4230-a78f-bfbf3f111015)


![asic9](https://github.com/user-attachments/assets/8170f856-02a1-4a0f-bb47-58389df5c3cb)


![asic10](https://github.com/user-attachments/assets/306c0dd5-7fb4-4990-bf55-942de6c9f6eb)



![asic11](https://github.com/user-attachments/assets/73975864-e25f-4161-9d31-443e6fb6ab84)



![asic12](https://github.com/user-attachments/assets/ecb90d72-178a-4147-a9e3-577541a95233)



![image](https://github.com/user-attachments/assets/9abd5623-d639-4c6d-ac3f-9a67ea213b32)



![image](https://github.com/user-attachments/assets/1ca3d93c-244a-404e-834c-d2406fcbbb9a)



![asic14](https://github.com/user-attachments/assets/bcecf136-c247-412f-9d2c-4f196a4504d4)


![image](https://github.com/user-attachments/assets/88c77ba1-a13b-4daf-990d-7cd38d825741)



![image](https://github.com/user-attachments/assets/64010efa-4913-402b-a1cf-260a28d66c89)

![image](https://github.com/user-attachments/assets/a31fc236-7533-44ee-afe0-f43e0541668f)



## Floorplan


![image](https://github.com/user-attachments/assets/0153ea74-3296-4fac-a251-3919a5559cde)

![image](https://github.com/user-attachments/assets/9cd71d75-f401-4f91-8a78-2facabab6f62)

![image](https://github.com/user-attachments/assets/2d85a742-7c13-415c-9c60-89742e786ab7)


![asic19](https://github.com/user-attachments/assets/a1b0e01d-7cee-4c3b-9db5-374946cbd6b8)




![image](https://github.com/user-attachments/assets/0b360042-502c-4d4b-a3bc-5aaca95c4678)



![asic20](https://github.com/user-attachments/assets/ec7e1782-f26b-4a0c-94e0-50ba3fcc2e97)




![image](https://github.com/user-attachments/assets/5804588f-c49b-43dc-8d0a-f82980940578)

![image](https://github.com/user-attachments/assets/334e1436-df1c-4a49-bdee-3ba218615184)


![image](https://github.com/user-attachments/assets/08783787-6ed6-4913-8bd5-76901fca9fc4)

![image](https://github.com/user-attachments/assets/fd4da382-a92f-4b98-b753-abdd36de9a75)


## Placement

![image](https://github.com/user-attachments/assets/a8b16f09-21a1-435f-88c3-e72ba0fc9eb1)

![image](https://github.com/user-attachments/assets/2bcefe01-6a99-4e55-ab70-db3594e3c21a)


![image](https://github.com/user-attachments/assets/06e5125e-0bb2-4c5f-b892-40ed14c74119)

![image](https://github.com/user-attachments/assets/04358760-b3c9-4c32-9c43-5cca90562959)


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
worst slack 5.82

==========================================================================
detailed place report_checks -path_delay min
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_imm_a2[11]$_DFF_P_
            (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_imm_a3[11]$_DFF_P_
          (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: min

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                  0.00    0.00    0.00   clock clk (rise edge)
                          3.00    3.00   clock network delay (ideal)
                  0.00    0.00    3.00 ^ rvmyth.CPU_imm_a2[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
     1    0.00    0.04    0.28    3.28 ^ rvmyth.CPU_imm_a2[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                         rvmyth.CPU_imm_a2[11] (net)
                  0.04    0.00    3.28 ^ rvmyth.CPU_imm_a3[11]$_DFF_P_/D (sky130_fd_sc_hd__dfxtp_1)
                                  3.28   data arrival time

                  0.00    0.00    0.00   clock clk (rise edge)
                          3.00    3.00   clock network delay (ideal)
                          0.92    3.92   clock uncertainty
                          0.00    3.92   clock reconvergence pessimism
                                  3.92 ^ rvmyth.CPU_imm_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
                         -0.04    3.89   library hold time
                                  3.89   data required time
-----------------------------------------------------------------------------
                                  3.89   data required time
                                 -3.28   data arrival time
-----------------------------------------------------------------------------
                                 -0.61   slack (VIOLATED)



==========================================================================
detailed place report_checks -path_delay max
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
            (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_
          (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                  0.00    0.00    0.00   clock clk (rise edge)
                          3.00    3.00   clock network delay (ideal)
                  0.00    0.00    3.00 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
     3    0.01    0.13    0.35    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                         rvmyth.CPU_src1_value_a3[11] (net)
                  0.13    0.00    3.35 ^ _05952_/A (sky130_fd_sc_hd__inv_1)
     2    0.01    0.08    0.11    3.45 v _05952_/Y (sky130_fd_sc_hd__inv_1)
                                         _05526_ (net)
                  0.08    0.00    3.45 v _11479_/B (sky130_fd_sc_hd__ha_4)
     9    0.06    0.09    0.30    3.75 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
                                         _05528_ (net)
                  0.09    0.00    3.75 v _08072_/A (sky130_fd_sc_hd__or4_2)
     2    0.01    0.14    0.74    4.49 v _08072_/X (sky130_fd_sc_hd__or4_2)
                                         _02699_ (net)
                  0.14    0.00    4.49 v _08077_/D (sky130_fd_sc_hd__or4_2)
     2    0.02    0.15    0.65    5.14 v _08077_/X (sky130_fd_sc_hd__or4_2)
                                         _02704_ (net)
                  0.15    0.00    5.14 v _08078_/B1 (sky130_fd_sc_hd__a211oi_4)
     2    0.02    0.33    0.37    5.51 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
                                         _02705_ (net)
                  0.33    0.00    5.51 ^ _08288_/A3 (sky130_fd_sc_hd__o311ai_4)
     3    0.03    0.23    0.18    5.69 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
                                         _02906_ (net)
                  0.23    0.00    5.69 v _08482_/A2 (sky130_fd_sc_hd__a2111oi_2)
     1    0.01    0.45    0.56    6.25 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
                                         _03092_ (net)
                  0.45    0.00    6.25 ^ _08483_/C1 (sky130_fd_sc_hd__a2111oi_2)
     1    0.01    0.12    0.13    6.38 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
                                         _03093_ (net)
                  0.12    0.00    6.38 v _08484_/B (sky130_fd_sc_hd__xnor2_2)
     1    0.02    0.14    0.21    6.59 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
                                         _03094_ (net)
                  0.14    0.00    6.59 v _08501_/A2 (sky130_fd_sc_hd__a211oi_4)
    17    0.13    1.35    1.12    7.71 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
                                         _03111_ (net)
                  1.35    0.03    7.74 ^ _09874_/A1 (sky130_fd_sc_hd__o21ai_0)
     1    0.00    0.19    0.23    7.97 v _09874_/Y (sky130_fd_sc_hd__o21ai_0)
                                         _00981_ (net)
                  0.19    0.00    7.97 v rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                  7.97   data arrival time

                  0.00   11.55   11.55   clock clk (rise edge)
                          3.00   14.55   clock network delay (ideal)
                         -0.58   13.97   clock uncertainty
                          0.00   13.97   clock reconvergence pessimism
                                 13.97 ^ rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
                         -0.19   13.79   library setup time
                                 13.79   data required time
-----------------------------------------------------------------------------
                                 13.79   data required time
                                 -7.97   data arrival time
-----------------------------------------------------------------------------
                                  5.82   slack (MET)



==========================================================================
detailed place report_checks -unconstrained
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
            (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_
          (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                  0.00    0.00    0.00   clock clk (rise edge)
                          3.00    3.00   clock network delay (ideal)
                  0.00    0.00    3.00 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
     3    0.01    0.13    0.35    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                         rvmyth.CPU_src1_value_a3[11] (net)
                  0.13    0.00    3.35 ^ _05952_/A (sky130_fd_sc_hd__inv_1)
     2    0.01    0.08    0.11    3.45 v _05952_/Y (sky130_fd_sc_hd__inv_1)
                                         _05526_ (net)
                  0.08    0.00    3.45 v _11479_/B (sky130_fd_sc_hd__ha_4)
     9    0.06    0.09    0.30    3.75 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
                                         _05528_ (net)
                  0.09    0.00    3.75 v _08072_/A (sky130_fd_sc_hd__or4_2)
     2    0.01    0.14    0.74    4.49 v _08072_/X (sky130_fd_sc_hd__or4_2)
                                         _02699_ (net)
                  0.14    0.00    4.49 v _08077_/D (sky130_fd_sc_hd__or4_2)
     2    0.02    0.15    0.65    5.14 v _08077_/X (sky130_fd_sc_hd__or4_2)
                                         _02704_ (net)
                  0.15    0.00    5.14 v _08078_/B1 (sky130_fd_sc_hd__a211oi_4)
     2    0.02    0.33    0.37    5.51 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
                                         _02705_ (net)
                  0.33    0.00    5.51 ^ _08288_/A3 (sky130_fd_sc_hd__o311ai_4)
     3    0.03    0.23    0.18    5.69 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
                                         _02906_ (net)
                  0.23    0.00    5.69 v _08482_/A2 (sky130_fd_sc_hd__a2111oi_2)
     1    0.01    0.45    0.56    6.25 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
                                         _03092_ (net)
                  0.45    0.00    6.25 ^ _08483_/C1 (sky130_fd_sc_hd__a2111oi_2)
     1    0.01    0.12    0.13    6.38 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
                                         _03093_ (net)
                  0.12    0.00    6.38 v _08484_/B (sky130_fd_sc_hd__xnor2_2)
     1    0.02    0.14    0.21    6.59 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
                                         _03094_ (net)
                  0.14    0.00    6.59 v _08501_/A2 (sky130_fd_sc_hd__a211oi_4)
    17    0.13    1.35    1.12    7.71 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
                                         _03111_ (net)
                  1.35    0.03    7.74 ^ _09874_/A1 (sky130_fd_sc_hd__o21ai_0)
     1    0.00    0.19    0.23    7.97 v _09874_/Y (sky130_fd_sc_hd__o21ai_0)
                                         _00981_ (net)
                  0.19    0.00    7.97 v rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                  7.97   data arrival time

                  0.00   11.55   11.55   clock clk (rise edge)
                          3.00   14.55   clock network delay (ideal)
                         -0.58   13.97   clock uncertainty
                          0.00   13.97   clock reconvergence pessimism
                                 13.97 ^ rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
                         -0.19   13.79   library setup time
                                 13.79   data required time
-----------------------------------------------------------------------------
                                 13.79   data required time
                                 -7.97   data arrival time
-----------------------------------------------------------------------------
                                  5.82   slack (MET)



==========================================================================
detailed place report_check_types -max_slew -max_cap -max_fanout -violators
--------------------------------------------------------------------------

==========================================================================
detailed place max_slew_check_slack
--------------------------------------------------------------------------
0.019938606768846512

==========================================================================
detailed place max_slew_check_limit
--------------------------------------------------------------------------
1.5

==========================================================================
detailed place max_slew_check_slack_limit
--------------------------------------------------------------------------
0.0133

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
0.000956510251853615

==========================================================================
detailed place max_capacitance_check_limit
--------------------------------------------------------------------------
0.43305400013923645

==========================================================================
detailed place max_capacitance_check_slack_limit
--------------------------------------------------------------------------
0.0022

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
hold violation count 1254

==========================================================================
detailed place report_checks -path_delay max reg to reg
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
            (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_
          (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

  Delay    Time   Description
---------------------------------------------------------
   0.00    0.00   clock clk (rise edge)
   3.00    3.00   clock network delay (ideal)
   0.00    3.00 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
   0.35    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
   0.11    3.45 v _05952_/Y (sky130_fd_sc_hd__inv_1)
   0.30    3.75 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
   0.74    4.49 v _08072_/X (sky130_fd_sc_hd__or4_2)
   0.65    5.14 v _08077_/X (sky130_fd_sc_hd__or4_2)
   0.37    5.51 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
   0.18    5.69 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
   0.56    6.25 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
   0.13    6.38 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
   0.21    6.59 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
   1.12    7.71 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
   0.26    7.97 v _09874_/Y (sky130_fd_sc_hd__o21ai_0)
   0.00    7.97 v rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
           7.97   data arrival time

  11.55   11.55   clock clk (rise edge)
   3.00   14.55   clock network delay (ideal)
  -0.58   13.97   clock uncertainty
   0.00   13.97   clock reconvergence pessimism
          13.97 ^ rvmyth.CPU_Xreg_value_a4[8][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
  -0.19   13.79   library setup time
          13.79   data required time
---------------------------------------------------------
          13.79   data required time
          -7.97   data arrival time
---------------------------------------------------------
           5.82   slack (MET)



==========================================================================
detailed place report_checks -path_delay min reg to reg
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_imm_a2[11]$_DFF_P_
            (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_imm_a3[11]$_DFF_P_
          (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: min

  Delay    Time   Description
---------------------------------------------------------
   0.00    0.00   clock clk (rise edge)
   3.00    3.00   clock network delay (ideal)
   0.00    3.00 ^ rvmyth.CPU_imm_a2[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
   0.28    3.28 ^ rvmyth.CPU_imm_a2[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
   0.00    3.28 ^ rvmyth.CPU_imm_a3[11]$_DFF_P_/D (sky130_fd_sc_hd__dfxtp_1)
           3.28   data arrival time

   0.00    0.00   clock clk (rise edge)
   3.00    3.00   clock network delay (ideal)
   0.92    3.92   clock uncertainty
   0.00    3.92   clock reconvergence pessimism
           3.92 ^ rvmyth.CPU_imm_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
  -0.04    3.89   library hold time
           3.89   data required time
---------------------------------------------------------
           3.89   data required time
          -3.28   data arrival time
---------------------------------------------------------
          -0.61   slack (VIOLATED)



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
7.9685

==========================================================================
detailed place critical path slack
--------------------------------------------------------------------------
5.8173

==========================================================================
detailed place slack div critical path delay
--------------------------------------------------------------------------
73.003702

==========================================================================
detailed place report_power
--------------------------------------------------------------------------
Group                  Internal  Switching    Leakage      Total
                          Power      Power      Power      Power (Watts)
----------------------------------------------------------------
Sequential             4.93e-03   9.74e-04   1.04e-08   5.90e-03  48.5%
Combinational          1.76e-03   4.52e-03   1.22e-08   6.28e-03  51.5%
Clock                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
----------------------------------------------------------------
Total                  6.68e-03   5.49e-03   2.26e-08   1.22e-02 100.0%
                          54.9%      45.1%       0.0%
```

## Clock Tree Synthesis

```
sudo make DESIGN_CONFIG=./designs/sky130hd/VSDBabySoC/config.mk cts
```
![image](https://github.com/user-attachments/assets/19deb7b7-c3e7-43d3-9057-4c8c449eaba3)


![image](https://github.com/user-attachments/assets/13a31545-97cf-4eae-82c1-ff9e433fe659)
```
make gui_cts
```
![image](https://github.com/user-attachments/assets/2b2100a6-ac28-4587-b2e4-1b082b9f6cb3)


![image](https://github.com/user-attachments/assets/c1463caa-33eb-4171-8c77-b3b2b70945dd)


![image](https://github.com/user-attachments/assets/722f515a-0571-48f8-947b-8e8cad4cfec5)

![image](https://github.com/user-attachments/assets/4e6d8ff5-5ad3-4d81-a64b-e38623ac8b5d)

The detailed routing file is as follows:-


![image](https://github.com/user-attachments/assets/41036b4e-1574-46ca-a118-48ee261c4695)

Content of Constraint Files
```
set_units -time ns
set PERIOD 10.25
create_clock [get_pins {pll/CLK}] -name clk -period $PERIOD
set_clock_uncertainty [expr 0.05 * $PERIOD] -setup [get_clocks clk]
set_clock_uncertainty [expr 0.08 * $PERIOD] -hold [get_clocks clk]
set_clock_transition [expr 0.05 * $PERIOD] [get_clocks clk]

set_input_transition [expr $PERIOD * 0.08] [get_ports ENb_CP]
set_input_transition [expr $PERIOD * 0.08] [get_ports ENb_VCO]
set_input_transition [expr $PERIOD * 0.08] [get_ports REF]
set_input_transition [expr $PERIOD * 0.08] [get_ports VCO_IN]
set_input_transition [expr $PERIOD * 0.08] [get_ports VREFH]
```
Merge File:

![image](https://github.com/user-attachments/assets/8a4d7012-b7bd-4aeb-854d-109dfab05310)

The final report.log file is as follows:-

![image](https://github.com/user-attachments/assets/5557150f-552e-4be8-9916-e3148b34d85a)

The synthesis statistics is as follows:

![image](https://github.com/user-attachments/assets/f9175a63-598c-42c1-84a7-90a58a8186fe)



final routing:

![image](https://github.com/user-attachments/assets/e2210f06-9bb8-4715-a514-31bd387250aa)


Heatmaps:

![image](https://github.com/user-attachments/assets/52b8fd17-e2bc-486f-b4a3-821a70d78184)

![image](https://github.com/user-attachments/assets/890d7562-f2cc-45d8-a662-4679d1f0c1af)

![image](https://github.com/user-attachments/assets/519f094c-7842-4f9d-9955-236c5b33bbe3)

![image](https://github.com/user-attachments/assets/3e5fd40f-afbd-4f3d-9981-bab15133a067)

![image](https://github.com/user-attachments/assets/5a14564d-b973-48bd-b830-3507a008922c)

IR drop

![image](https://github.com/user-attachments/assets/63a84bf7-a4e7-4b3a-868a-7ea1a6784268)



QoR:

![image](https://github.com/user-attachments/assets/f760b4d0-c2e7-4957-b82d-3e8f8d7f1ede)

![image](https://github.com/user-attachments/assets/a49a1dbe-df23-490b-a35d-f6243ca9c504)

![image](https://github.com/user-attachments/assets/1c98259e-0ab7-4c90-a9d9-fc1ad8d822d4)



Routing
![image](https://github.com/user-attachments/assets/657f331f-4145-437e-ac73-96e3223c13e4)


![image](https://github.com/user-attachments/assets/7ea4e566-8789-4423-952c-7cd85ebed5f6)


```
==========================================================================
global route report_tns
--------------------------------------------------------------------------
tns 0.00

==========================================================================
global route report_wns
--------------------------------------------------------------------------
wns 0.00

==========================================================================
global route report_worst_slack
--------------------------------------------------------------------------
worst slack 5.62

==========================================================================
global route report_clock_skew
--------------------------------------------------------------------------
Clock clk
  2.98 source latency rvmyth.CPU_src1_value_a3[20]$_DFF_P_/CLK ^
 -2.91 target latency rvmyth.CPU_Xreg_value_a4[8][26]$_SDFFE_PP0P_/CLK ^
  0.58 clock uncertainty
  0.00 CRPR
--------------
  0.65 setup skew


==========================================================================
global route report_checks -path_delay min
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_
           (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_src1_value_a3[21]$_DFF_P_
         (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: min

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                         0.00    0.00   clock clk (rise edge)
                         2.00    2.00   clock source latency
    2    0.20    0.00    0.00    2.00 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01    2.01 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00    2.21 ^ clkbuf_2_0_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.14    0.16    0.25    2.46 ^ clkbuf_2_0_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_0_0_clk_har (net)
                 0.16    0.01    2.46 ^ clkbuf_4_0__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.17    0.18    0.27    2.73 ^ clkbuf_4_0__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_0__leaf_clk_har (net)
                 0.18    0.00    2.74 ^ clkbuf_leaf_1_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    9    0.04    0.06    0.19    2.92 ^ clkbuf_leaf_1_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_1_clk_har (net)
                 0.06    0.00    2.92 ^ rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
    3    0.01    0.11    0.36    3.29 ^ rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                        rvmyth.CPU_Xreg_value_a4[1][21] (net)
                 0.11    0.00    3.29 ^ _10331_/B2 (sky130_fd_sc_hd__a22oi_1)
    1    0.00    0.06    0.08    3.37 v _10331_/Y (sky130_fd_sc_hd__a22oi_1)
                                        _04437_ (net)
                 0.06    0.00    3.37 v _10332_/C (sky130_fd_sc_hd__nand3_1)
    1    0.01    0.12    0.13    3.50 ^ _10332_/Y (sky130_fd_sc_hd__nand3_1)
                                        _04438_ (net)
                 0.12    0.00    3.50 ^ _10333_/B2 (sky130_fd_sc_hd__o22ai_4)
    1    0.05    0.14    0.15    3.65 v _10333_/Y (sky130_fd_sc_hd__o22ai_4)
                                        _04439_ (net)
                 0.14    0.01    3.66 v _10336_/A2 (sky130_fd_sc_hd__o21ai_0)
    1    0.00    0.08    0.20    3.87 ^ _10336_/Y (sky130_fd_sc_hd__o21ai_0)
                                        rvmyth.CPU_src1_value_a2[21] (net)
                 0.08    0.00    3.87 ^ rvmyth.CPU_src1_value_a3[21]$_DFF_P_/D (sky130_fd_sc_hd__dfxtp_2)
                                 3.87   data arrival time

                         0.00    0.00   clock clk (rise edge)
                         2.00    2.00   clock source latency
    2    0.20    0.00    0.00    2.00 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01    2.01 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00    2.21 ^ clkbuf_2_2_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.15    0.24    2.45 ^ clkbuf_2_2_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_2_0_clk_har (net)
                 0.15    0.00    2.46 ^ clkbuf_4_8__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   13    0.21    0.22    0.30    2.75 ^ clkbuf_4_8__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_8__leaf_clk_har (net)
                 0.22    0.01    2.76 ^ clkbuf_leaf_26_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.05    0.07    0.21    2.97 ^ clkbuf_leaf_26_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_26_clk_har (net)
                 0.07    0.00    2.97 ^ rvmyth.CPU_src1_value_a3[21]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_2)
                         0.92    3.89   clock uncertainty
                         0.00    3.89   clock reconvergence pessimism
                        -0.04    3.86   library hold time
                                 3.86   data required time
-----------------------------------------------------------------------------
                                 3.86   data required time
                                -3.87   data arrival time
-----------------------------------------------------------------------------
                                 0.01   slack (MET)



==========================================================================
global route report_checks -path_delay max
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
           (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_
         (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                         0.00    0.00   clock clk (rise edge)
                         2.00    2.00   clock source latency
    2    0.20    0.00    0.00    2.00 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01    2.01 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00    2.21 ^ clkbuf_2_3_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.24    2.45 ^ clkbuf_2_3_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_3_0_clk_har (net)
                 0.14    0.00    2.46 ^ clkbuf_4_13__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   12    0.20    0.21    0.29    2.74 ^ clkbuf_4_13__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_13__leaf_clk_har (net)
                 0.21    0.01    2.75 ^ clkbuf_leaf_95_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.05    0.07    0.20    2.95 ^ clkbuf_leaf_95_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_95_clk_har (net)
                 0.07    0.00    2.95 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
    3    0.02    0.16    0.40    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                        rvmyth.CPU_src1_value_a3[11] (net)
                 0.16    0.00    3.35 ^ _05952_/A (sky130_fd_sc_hd__inv_1)
    2    0.02    0.10    0.13    3.47 v _05952_/Y (sky130_fd_sc_hd__inv_1)
                                        _05526_ (net)
                 0.10    0.00    3.48 v _11479_/B (sky130_fd_sc_hd__ha_4)
    9    0.06    0.10    0.31    3.78 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
                                        _05528_ (net)
                 0.10    0.00    3.79 v _08072_/A (sky130_fd_sc_hd__or4_2)
    2    0.01    0.14    0.74    4.53 v _08072_/X (sky130_fd_sc_hd__or4_2)
                                        _02699_ (net)
                 0.14    0.00    4.53 v _08077_/D (sky130_fd_sc_hd__or4_2)
    2    0.02    0.15    0.65    5.18 v _08077_/X (sky130_fd_sc_hd__or4_2)
                                        _02704_ (net)
                 0.15    0.00    5.18 v _08078_/B1 (sky130_fd_sc_hd__a211oi_4)
    2    0.02    0.34    0.38    5.56 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
                                        _02705_ (net)
                 0.34    0.00    5.56 ^ _08288_/A3 (sky130_fd_sc_hd__o311ai_4)
    3    0.03    0.24    0.18    5.75 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
                                        _02906_ (net)
                 0.24    0.00    5.75 v _08482_/A2 (sky130_fd_sc_hd__a2111oi_2)
    1    0.01    0.49    0.60    6.35 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
                                        _03092_ (net)
                 0.49    0.00    6.35 ^ _08483_/C1 (sky130_fd_sc_hd__a2111oi_2)
    1    0.01    0.13    0.14    6.49 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
                                        _03093_ (net)
                 0.13    0.00    6.49 v _08484_/B (sky130_fd_sc_hd__xnor2_2)
    1    0.02    0.15    0.22    6.71 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
                                        _03094_ (net)
                 0.15    0.00    6.71 v _08501_/A2 (sky130_fd_sc_hd__a211oi_4)
   17    0.12    1.31    1.09    7.80 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
                                        _03111_ (net)
                 1.31    0.03    7.83 ^ _09030_/A1 (sky130_fd_sc_hd__o21ai_0)
    1    0.00    0.21    0.28    8.11 v _09030_/Y (sky130_fd_sc_hd__o21ai_0)
                                        _00693_ (net)
                 0.21    0.00    8.11 v rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                 8.11   data arrival time

                        11.55   11.55   clock clk (rise edge)
                         2.00   13.55   clock source latency
    2    0.20    0.00    0.00   13.55 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01   13.56 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20   13.76 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00   13.76 ^ clkbuf_2_0_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.14    0.16    0.25   14.01 ^ clkbuf_2_0_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_0_0_clk_har (net)
                 0.16    0.01   14.01 ^ clkbuf_4_0__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.17    0.18    0.27   14.28 ^ clkbuf_4_0__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_0__leaf_clk_har (net)
                 0.18    0.00   14.29 ^ clkbuf_leaf_3_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    8    0.05    0.07    0.19   14.48 ^ clkbuf_leaf_3_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_3_clk_har (net)
                 0.07    0.00   14.48 ^ rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
                        -0.58   13.90   clock uncertainty
                         0.00   13.90   clock reconvergence pessimism
                        -0.18   13.72   library setup time
                                13.72   data required time
-----------------------------------------------------------------------------
                                13.72   data required time
                                -8.11   data arrival time
-----------------------------------------------------------------------------
                                 5.62   slack (MET)



==========================================================================
global route report_checks -unconstrained
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
           (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_
         (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

Fanout     Cap    Slew   Delay    Time   Description
-----------------------------------------------------------------------------
                         0.00    0.00   clock clk (rise edge)
                         2.00    2.00   clock source latency
    2    0.20    0.00    0.00    2.00 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01    2.01 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00    2.21 ^ clkbuf_2_3_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.24    2.45 ^ clkbuf_2_3_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_3_0_clk_har (net)
                 0.14    0.00    2.46 ^ clkbuf_4_13__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   12    0.20    0.21    0.29    2.74 ^ clkbuf_4_13__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_13__leaf_clk_har (net)
                 0.21    0.01    2.75 ^ clkbuf_leaf_95_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.05    0.07    0.20    2.95 ^ clkbuf_leaf_95_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_95_clk_har (net)
                 0.07    0.00    2.95 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
    3    0.02    0.16    0.40    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
                                        rvmyth.CPU_src1_value_a3[11] (net)
                 0.16    0.00    3.35 ^ _05952_/A (sky130_fd_sc_hd__inv_1)
    2    0.02    0.10    0.13    3.47 v _05952_/Y (sky130_fd_sc_hd__inv_1)
                                        _05526_ (net)
                 0.10    0.00    3.48 v _11479_/B (sky130_fd_sc_hd__ha_4)
    9    0.06    0.10    0.31    3.78 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
                                        _05528_ (net)
                 0.10    0.00    3.79 v _08072_/A (sky130_fd_sc_hd__or4_2)
    2    0.01    0.14    0.74    4.53 v _08072_/X (sky130_fd_sc_hd__or4_2)
                                        _02699_ (net)
                 0.14    0.00    4.53 v _08077_/D (sky130_fd_sc_hd__or4_2)
    2    0.02    0.15    0.65    5.18 v _08077_/X (sky130_fd_sc_hd__or4_2)
                                        _02704_ (net)
                 0.15    0.00    5.18 v _08078_/B1 (sky130_fd_sc_hd__a211oi_4)
    2    0.02    0.34    0.38    5.56 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
                                        _02705_ (net)
                 0.34    0.00    5.56 ^ _08288_/A3 (sky130_fd_sc_hd__o311ai_4)
    3    0.03    0.24    0.18    5.75 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
                                        _02906_ (net)
                 0.24    0.00    5.75 v _08482_/A2 (sky130_fd_sc_hd__a2111oi_2)
    1    0.01    0.49    0.60    6.35 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
                                        _03092_ (net)
                 0.49    0.00    6.35 ^ _08483_/C1 (sky130_fd_sc_hd__a2111oi_2)
    1    0.01    0.13    0.14    6.49 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
                                        _03093_ (net)
                 0.13    0.00    6.49 v _08484_/B (sky130_fd_sc_hd__xnor2_2)
    1    0.02    0.15    0.22    6.71 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
                                        _03094_ (net)
                 0.15    0.00    6.71 v _08501_/A2 (sky130_fd_sc_hd__a211oi_4)
   17    0.12    1.31    1.09    7.80 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
                                        _03111_ (net)
                 1.31    0.03    7.83 ^ _09030_/A1 (sky130_fd_sc_hd__o21ai_0)
    1    0.00    0.21    0.28    8.11 v _09030_/Y (sky130_fd_sc_hd__o21ai_0)
                                        _00693_ (net)
                 0.21    0.00    8.11 v rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
                                 8.11   data arrival time

                        11.55   11.55   clock clk (rise edge)
                         2.00   13.55   clock source latency
    2    0.20    0.00    0.00   13.55 ^ avsdpll/CLK (avsdpll)
                                        clk_har (net)
                 0.02    0.01   13.56 ^ clkbuf_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.13    0.14    0.20   13.76 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_0_clk_har (net)
                 0.14    0.00   13.76 ^ clkbuf_2_0_0_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    4    0.14    0.16    0.25   14.01 ^ clkbuf_2_0_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_2_0_0_clk_har (net)
                 0.16    0.01   14.01 ^ clkbuf_4_0__f_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
   10    0.17    0.18    0.27   14.28 ^ clkbuf_4_0__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_4_0__leaf_clk_har (net)
                 0.18    0.00   14.29 ^ clkbuf_leaf_3_clk_har/A (sky130_fd_sc_hd__clkbuf_16)
    8    0.05    0.07    0.19   14.48 ^ clkbuf_leaf_3_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
                                        clknet_leaf_3_clk_har (net)
                 0.07    0.00   14.48 ^ rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
                        -0.58   13.90   clock uncertainty
                         0.00   13.90   clock reconvergence pessimism
                        -0.18   13.72   library setup time
                                13.72   data required time
-----------------------------------------------------------------------------
                                13.72   data required time
                                -8.11   data arrival time
-----------------------------------------------------------------------------
                                 5.62   slack (MET)



==========================================================================
global route report_check_types -max_slew -max_cap -max_fanout -violators
--------------------------------------------------------------------------

==========================================================================
global route max_slew_check_slack
--------------------------------------------------------------------------
0.08847511559724808

==========================================================================
global route max_slew_check_limit
--------------------------------------------------------------------------
1.5

==========================================================================
global route max_slew_check_slack_limit
--------------------------------------------------------------------------
0.0590

==========================================================================
global route max_fanout_check_slack
--------------------------------------------------------------------------
1.0000000150474662e+30

==========================================================================
global route max_fanout_check_limit
--------------------------------------------------------------------------
1.0000000150474662e+30

==========================================================================
global route max_capacitance_check_slack
--------------------------------------------------------------------------
0.015918675810098648

==========================================================================
global route max_capacitance_check_limit
--------------------------------------------------------------------------
0.021067000925540924

==========================================================================
global route max_capacitance_check_slack_limit
--------------------------------------------------------------------------
0.7556

==========================================================================
global route max_slew_violation_count
--------------------------------------------------------------------------
max slew violation count 0

==========================================================================
global route max_fanout_violation_count
--------------------------------------------------------------------------
max fanout violation count 0

==========================================================================
global route max_cap_violation_count
--------------------------------------------------------------------------
max cap violation count 0

==========================================================================
global route setup_violation_count
--------------------------------------------------------------------------
setup violation count 0

==========================================================================
global route hold_violation_count
--------------------------------------------------------------------------
hold violation count 0

==========================================================================
global route report_checks -path_delay max reg to reg
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_src1_value_a3[11]$_DFF_P_
           (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_
         (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: max

 Delay    Time   Description
---------------------------------------------------------
  0.00    0.00   clock clk (rise edge)
  2.00    2.00   clock source latency
  0.00    2.00 ^ avsdpll/CLK (avsdpll)
  0.21    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.24    2.45 ^ clkbuf_2_3_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.29    2.74 ^ clkbuf_4_13__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.21    2.95 ^ clkbuf_leaf_95_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.00    2.95 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_1)
  0.40    3.35 ^ rvmyth.CPU_src1_value_a3[11]$_DFF_P_/Q (sky130_fd_sc_hd__dfxtp_1)
  0.13    3.47 v _05952_/Y (sky130_fd_sc_hd__inv_1)
  0.31    3.78 v _11479_/SUM (sky130_fd_sc_hd__ha_4)
  0.75    4.53 v _08072_/X (sky130_fd_sc_hd__or4_2)
  0.65    5.18 v _08077_/X (sky130_fd_sc_hd__or4_2)
  0.38    5.56 ^ _08078_/Y (sky130_fd_sc_hd__a211oi_4)
  0.18    5.75 v _08288_/Y (sky130_fd_sc_hd__o311ai_4)
  0.60    6.35 ^ _08482_/Y (sky130_fd_sc_hd__a2111oi_2)
  0.14    6.49 v _08483_/Y (sky130_fd_sc_hd__a2111oi_2)
  0.22    6.71 v _08484_/Y (sky130_fd_sc_hd__xnor2_2)
  1.09    7.80 ^ _08501_/Y (sky130_fd_sc_hd__a211oi_4)
  0.31    8.11 v _09030_/Y (sky130_fd_sc_hd__o21ai_0)
  0.00    8.11 v rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/D (sky130_fd_sc_hd__dfxtp_1)
          8.11   data arrival time

 11.55   11.55   clock clk (rise edge)
  2.00   13.55   clock source latency
  0.00   13.55 ^ avsdpll/CLK (avsdpll)
  0.21   13.76 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.25   14.01 ^ clkbuf_2_0_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.27   14.28 ^ clkbuf_4_0__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.20   14.48 ^ clkbuf_leaf_3_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.00   14.48 ^ rvmyth.CPU_Xreg_value_a4[14][29]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
 -0.58   13.90   clock uncertainty
  0.00   13.90   clock reconvergence pessimism
 -0.18   13.72   library setup time
         13.72   data required time
---------------------------------------------------------
         13.72   data required time
         -8.11   data arrival time
---------------------------------------------------------
          5.62   slack (MET)



==========================================================================
global route report_checks -path_delay min reg to reg
--------------------------------------------------------------------------
Startpoint: rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_
           (rising edge-triggered flip-flop clocked by clk)
Endpoint: rvmyth.CPU_src1_value_a3[21]$_DFF_P_
         (rising edge-triggered flip-flop clocked by clk)
Path Group: clk
Path Type: min

 Delay    Time   Description
---------------------------------------------------------
  0.00    0.00   clock clk (rise edge)
  2.00    2.00   clock source latency
  0.00    2.00 ^ avsdpll/CLK (avsdpll)
  0.21    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.25    2.46 ^ clkbuf_2_0_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.27    2.73 ^ clkbuf_4_0__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.19    2.92 ^ clkbuf_leaf_1_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.00    2.92 ^ rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_/CLK (sky130_fd_sc_hd__dfxtp_1)
  0.36    3.29 ^ rvmyth.CPU_Xreg_value_a4[1][21]$_SDFFE_PP0P_/Q (sky130_fd_sc_hd__dfxtp_1)
  0.08    3.37 v _10331_/Y (sky130_fd_sc_hd__a22oi_1)
  0.13    3.50 ^ _10332_/Y (sky130_fd_sc_hd__nand3_1)
  0.15    3.65 v _10333_/Y (sky130_fd_sc_hd__o22ai_4)
  0.21    3.87 ^ _10336_/Y (sky130_fd_sc_hd__o21ai_0)
  0.00    3.87 ^ rvmyth.CPU_src1_value_a3[21]$_DFF_P_/D (sky130_fd_sc_hd__dfxtp_2)
          3.87   data arrival time

  0.00    0.00   clock clk (rise edge)
  2.00    2.00   clock source latency
  0.00    2.00 ^ avsdpll/CLK (avsdpll)
  0.21    2.21 ^ clkbuf_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.25    2.45 ^ clkbuf_2_2_0_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.30    2.75 ^ clkbuf_4_8__f_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.21    2.97 ^ clkbuf_leaf_26_clk_har/X (sky130_fd_sc_hd__clkbuf_16)
  0.00    2.97 ^ rvmyth.CPU_src1_value_a3[21]$_DFF_P_/CLK (sky130_fd_sc_hd__dfxtp_2)
  0.92    3.89   clock uncertainty
  0.00    3.89   clock reconvergence pessimism
 -0.04    3.86   library hold time
          3.86   data required time
---------------------------------------------------------
          3.86   data required time
         -3.87   data arrival time
---------------------------------------------------------
          0.01   slack (MET)



==========================================================================
global route critical path target clock latency max path
--------------------------------------------------------------------------
0

==========================================================================
global route critical path target clock latency min path
--------------------------------------------------------------------------
0

==========================================================================
global route critical path source clock latency min path
--------------------------------------------------------------------------
0

==========================================================================
global route critical path delay
--------------------------------------------------------------------------
8.1059

==========================================================================
global route critical path slack
--------------------------------------------------------------------------
5.6176

==========================================================================
global route slack div critical path delay
--------------------------------------------------------------------------
69.302607

==========================================================================
global route report_power
--------------------------------------------------------------------------
Group                  Internal  Switching    Leakage      Total
                         Power      Power      Power      Power (Watts)
----------------------------------------------------------------
Sequential             4.83e-03   8.99e-04   1.04e-08   5.73e-03  30.3%
Combinational          2.06e-03   4.80e-03   2.40e-08   6.86e-03  36.4%
Clock                  3.28e-03   3.00e-03   2.82e-09   6.28e-03  33.3%
Macro                  0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
Pad                    0.00e+00   0.00e+00   0.00e+00   0.00e+00   0.0%
----------------------------------------------------------------
Total                  1.02e-02   8.69e-03   3.72e-08   1.89e-02 100.0%
                         53.9%      46.1%       0.0%

```


























</details>

























































































































































































































































































































































































































































































    
































































































































































































































































