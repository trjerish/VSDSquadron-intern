 # VSD-Internship 
### PROJECT
Clock Cycle Divider - Crafting A Digital Clock Divider Circuit
***
### VICTO JERISH I
B.E Electronics And Communication Engineering
R.M.K Engineering College
## Features Of RISC-V
+ Open Standard: Freely available and open-source ISA.
+ Modular Design: Highly customizable with optional extensions.
+ Simplicity: Simplified instruction set for efficient execution.
+ Scalability: Suitable for a wide range of applications from microcontrollers to supercomputers.
+ Community Support: Strong backing from a global community of developers and companies.
***
## Task 1
### C Code implementation in Leafpad
In this section, we'll explore how C code is reprsented in the instruction set of the RISC-V tool. We'll start by testing the GCC compiler with a simple program that counts the sum of numbers from 1 to n. STEP 1: Write the C program that counts the sum of numbers from 1 to n in the Leafpad editor(open source graphical text editor) and save the code.
### Command
     Initially the cd command is given in the terminal.
     After which the leafpad _filename_ & is given which is the command for opening the leafpad.
     Now the leafpad is opened in which the required code for the title is typed respectively.
![Picture 1](https://github.com/trjerish/VSD-Internship/assets/155642455/4560e034-d41c-4417-987d-0b58a7e5f41a)
To check the output in leafpad use this
![Picture 2](https://github.com/trjerish/VSD-Internship/assets/155642455/5549d252-8100-4cb3-8ea2-3cbfec7ce9e2)
### Command
     The terminal is opened to obtain the output.
     The gcc _filename_.c is given with the extension of .c 
     After which the ouput is viewed through the command of ./a.out respectively.
### C Code implementation in RISC-V
where lp is the long point integer of 64 bit -O1 is the options to compile the code using gcc compiler march is the architecture type -o is the output file rv64 is the RISC-V of 64 bit
### Command
           riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
![Picture 3](https://github.com/trjerish/VSD-Internship/assets/155642455/d398423b-96b4-4fea-9491-4249fb7aa1eb)
### To Generate Assembly Code
To generate assembly code is generated in the risc v compiler
### Command
         riscv64-unknown-elf-objdump -d sum1ton.o
This assemby code then can be further reduced to some extend by the command
### Command
         riscv64-unknown-elf-objdump -d sum1ton.o | less
![Picture 4](https://github.com/trjerish/VSD-Internship/assets/155642455/f2037656-4701-48d1-b906-683efef4fb39)

Task 1 is Completed
***

## Task 2
In this task 2 then you create a new directory and the use the clockdivider then find the programm for the clock divider check the output 
![Screenshot (498)](https://github.com/trjerish/VSD-Internship/assets/155642455/52a530d3-847a-4cd5-8f6b-3b6480268b9f)

Programm for the clock divider signal crafting


    #include <stdio.h>
    #include <stdbool.h>

    // Define the clock divider factor
    #define CLOCK_DIVIDER 1000

    // Function to simulate the clock divider
    void clock_divider(int divider, int max_cycles) {
    int counter = 0;
    bool clock_out = false;
    
    for (int i = 0; i < max_cycles; ++i) {
        counter++;
        if (counter >= divider) {
            counter = 0;
            clock_out = !clock_out; // Toggle the clock output
            printf("Clock cycle %d: Clock out state = %d\n", i, clock_out);
        }
    }
    }

     int main() {
     int max_cycles = 10000; // Number of clock cycles to simulate
     clock_divider(CLOCK_DIVIDER, max_cycles);
     return 0;
     }
![Screenshot (499)](https://github.com/trjerish/VSD-Internship/assets/155642455/9d938098-28cd-48f8-a955-110166268c82)

output for the programm is

![Screenshot (497)](https://github.com/trjerish/VSD-Internship/assets/155642455/aaebf56e-92ee-4762-9c52-21f9f5979769)

Generate the assembly code in risc v compiler

![Screenshot (501)](https://github.com/trjerish/VSD-Internship/assets/155642455/1d1cb7ce-6094-4dae-aebb-69ddcf829b02)

Calculate the value by the calculator in programming mode in hexadecimal

![Screenshot (500)](https://github.com/trjerish/VSD-Internship/assets/155642455/9adf7d96-afca-4061-86d7-debc2f27058f)
Task 2 is Completed
***

## Task 3
Execution of SPIKE Simulation and verification with O1 and Ofast command along with running the RISC-V Objdmp.
The task 3 involves the execution of spike simulation and also consisting of debug of the Assembly code that is generated for the previous program.
Verifying the outputs
## command
      gcc clkdiv.c
      ./a.out
      riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o clkdiv.o clkdiv.c
      spike pk clkdiv.o
![Screenshot (506)](https://github.com/trjerish/VSD-Internship/assets/155642455/7ae4e1fe-6af8-488e-95dc-37d114472f4e)

Debugging the instruction
Before Debugging, open the assembly code of your project in a newtab and enter the below command to view the assembly code.
## command
       riscv64-unknown-elf-objdump -d clkdiv.o | less

![Screenshot (507)](https://github.com/trjerish/VSD-Internship/assets/155642455/74fcf9a5-9c22-4bfe-8255-3f6fd552061e)

We can also enter a command from where the instruction needed to be debugged (i.e) All the instruction before that address will be executed.
(spike) until pc 0 100b0 // we can start debugging from this address
## command
       (spike) until pc 0 100b0 // we can start debugging from this address
       (spike) reg 0 a5 // the content before executing the instruction will be displayed

![Screenshot (508)](https://github.com/trjerish/VSD-Internship/assets/155642455/f78d909a-f0ee-4ae5-b4f9-b1f45dd1adce)

Now press enter to view the instruction of the given first address and follow the above command to view the content of a5 after execution,
similarly the contents of stack pointer before and after execution of that instruction can also viewed as shown below.Similarly continue pressing the ENTER to view the next significant instruction.

![Screenshot (509)](https://github.com/trjerish/VSD-Internship/assets/155642455/a5994ef2-4e10-4231-b259-7c8e78de78ad)

Task 3 is Completed
***

## Task 4
Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions
To identify and construct the 32-bit instruction codes for the given RISC-V instructions, we need to follow the RISC-V instruction format for each type (R, I, S, B, U, J).

Here are the steps:
+ Identify the instruction type for each instruction.
+ Determine the opcode, funct3, and funct7 (if applicable) values for each instruction.
+ Fill in the fields (opcode, rd, funct3, rs1, rs2, funct7, imm) to construct the 32-bit binary instruction.

## Instructions
+ For R-type:
 
       opcode[6:0] | rd[11:7] | funct3[14:12] | rs1[19:15] | rs2[24:20] | funct7[31:25]
+ For I-type:
  
       opcode[6:0] | rd[11:7] | funct3[14:12] | rs1[19:15] | imm[31:20]
+ For S-type:

       opcode[6:0] | imm[4:0][11:7] | funct3[14:12] | rs1[19:15] | rs2[24:20] | imm[11:5][31:25]
+ For B-type:
  
       opcode[6:0] | imm[11][7] | imm[4:1][11:8] | funct3[14:12] | rs1[19:15] | rs2[24:20] | imm[10:5][31:25] | imm[12][31]
+ For U-type:
  
       opcode[6:0] | rd[11:7] | imm[31:12]
+ For J-type:
  
       opcode[6:0] | rd[11:7] | imm[19:12][20] | imm[10:1][11] | imm[31:21]

## 1.ADD r1, r2, r3
+ Type: R

Opcode: 0110011       Funct3: 000          Funct7: 0000000

rs1: r2 = 00010       rs2: r3 = 00011      rd: r1 = 00001

32-bit: 0000000 00011 00010 000 00001 0110011

     ADD r1, r2, r3: 0000000 00011 00010 000 00001 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |ADD r1, r2, r3 |     R       |
      
## 2. SUB r3, r1, r2
+ Type: R

Opcode: 0110011      Funct3: 000           Funct7: 0100000

rs1: r1 = 00001      rs2: r2 = 00010       rd: r3 = 00011

32-bit: 0100000 00010 00001 000 00011 0110011

    SUB r3, r1, r2: 0100000 00010 00001 000 00011 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |SUB r3, r1, r2 |     R       |

## 3. AND r2, r1, r3
+ Type: R

Opcode: 0110011      Funct3: 111           Funct7: 0000000

rs1: r1 = 00001      rs2: r3 = 00011       rd: r2 = 00010

32-bit: 0000000 00011 00001 111 00010 0110011

    AND r2, r1, r3: 0000000 00011 00001 111 00010 0110011
    
   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |AND r2, r1, r3 |     R       |

## 4. OR r8, r2, r5
+ Type: R

Opcode: 0110011      Funct3: 110          Funct7: 0000000

rs1: r2 = 00010      rs2: r5 = 00101      rd: r8 = 01000

32-bit: 0000000 00101 00010 110 01000 0110011

    OR r8, r2, r5: 0000000 00101 00010 110 01000 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |OR r8, r2, r5  |     R       |

## 5. XOR r8, r1, r4
+ Type: R

Opcode: 0110011      Funct3: 100          Funct7: 0000000

rs1: r1 = 00001      rs2: r4 = 00100      rd: r8 = 01000

32-bit: 0000000 00100 00001 100 01000 0110011

    XOR r8, r1, r4: 0000000 00100 00001 100 01000 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |XOR r8, r1, r4 |     R       |
     

## 6. SLT r10, r2, r4
+ Type: R

Opcode: 0110011      Funct3: 010          Funct7: 0000000

rs1: r2 = 00010      rs2: r4 = 00100      rd: r10 = 01010

32-bit: 0000000 00100 00010 010 01010 0110011

    SLT r10, r2, r4: 0000000 00100 00010 010 01010 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |SLT r10, r2, r4|     R       |

## 7. ADDI r12, r3, 5
+ Type: I

Opcode: 0010011      Funct3: 000          rs1: r3 = 00011

rd: r12 = 01100      imm: 000000000101

32-bit: 000000000101 00011 000 01100 0010011

     ADDI r12, r3, 5: 000000000101 00011 000 01100 0010011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   | ADDI r12, r3,5|     I       |
     

## 8. SW r3, r1, 4
+ Type: S

Opcode: 0100011      Funct3: 010         rs1: r1 = 00001

rs2: r3 = 00011      imm: 0000000 | 4 (00000 | 00100)

32-bit: 0000000 00011 00001 010 00100 0100011

    SW r3, r1, 4: 0000000 00011 00001 010 00100 0100011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |  SW r3, r1, 4	|     S       |

## 9. SRL r16, r11, r2
+ Type: R

Opcode: 0110011      Funct3: 101        Funct7: 0000000

rs1: r11 = 01011     rs2: r2 = 00010    rd: r16 = 10000

32-bit: 0000000 00010 01011 101 10000 0110011

    SRL r16, r11, r2: 0000000 00010 01011 101 10000 0110011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |SRL r16,r11, r2|     R       |

## 10. BNE r0, r1, 20
+ Type: B

Opcode: 1100011      Funct3: 001       rs1: r0 = 00000

rs2: r1 = 00001      imm: 20 (00000 | 00101 | 0 | 0000)

32-bit: 00000 00101 000 00000 00001 1100011

    BNE r0, r1, 20: 00000 00101 000 00000 00001 1100011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |BNE r0, r1, 20	|     B       |

## 11. BEQ r0, r0, 15
+ Type: B

Opcode: 1100011      Funct3: 000       rs1: r0 = 00000

rs2: r0 = 00000      imm: 15 (0000 | 0011 | 1 | 0000)

32-bit: 00000 00111 000 00000 00000 1100011

    BEQ  r0, r0, 15_: 00000 00000 000 00000 00011 111100011.

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |BEQ r0, r0, 15	|     B       |

## 12. LW r13, r11, 2
+ Type: I

Opcode: 0000011      Funct3: 010       rs1: r11 = 01011

rd: r13 = 01101     imm: 000000000010

32-bit: 000000000010 01011 010 01101 0000011

    LW   r13, r11, 2_: 00000 00000 100 10110 10001 100100011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |LW r13, r11, 2	|     I      |

## 13. SLL r15, r11, r2
+ Type: R

Opcode: 0110011     Funct3: 001       Funct7: 0000000

rs1: r11 = 01011    rs2: r2 = 00010   rd: r15 = 01111

32-bit: 0000000 00010 01011 001 01111 0110011

    SLL  r15, r11, r2_: 00000 00000 100 10110 00001 111010011

   |  Instruction  |    Type     |
   | ------------- | ----------- |
   |SLL r15, r11,R2|     R       |

## Reference
[Reference](https://drive.google.com/file/d/1uviu1nH-tScFfgrovvFCrj7Omv8tFtkp/view).

Task 4 is Completed
***

## Task 5
The task is to generate Verilog and testbench using RISC-V and verify the functional simulation for instruction and waveform

## Steps to perform functional simulation:

First to run the Verilog we need a tool called iverilog to install iverilog commands are 
     sudo apt-get update 
     sudo apt-get install iverilog
To get the waveform we need a tool called gtkwave command is 
     sudo apt-get install gtkwave
Create a directory using the command 
     mkdir jerish
Create files using the touch command as 
   touch jerish_rv32i.v 
   touch jerish_rv32i_tb.v
Writing Verilog code and testbench is not part of the internship we will be taking references from the repo https://github.com/vinayrayapati/rv32i/
Now copy the code from the 
   iiitb_rv32i.v  
   iiitb_rv32i_tb.v 
paste the code in 
   Nehith_rv32i.v
   Nehith_rv32i_tb.v 
in leaf pad and save the file
To run the code and simulate use the command 
   iverilog -o jerish_rv32i jerish_rv32i.v jerish_rv32i_tb.v 
to get the output 
  ./jerish_rv32i
To get the wave from use the command 
  gtkwave iiitb_rv32i.vcd


