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


