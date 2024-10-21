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





































































































































































































































































































































































































































































































    
































































































































































































































































