# Sky130 DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
## How to talk to computers

### 0 - Introduction to QFN-48 Package, chip, pads, core, die and IPs

A very common Arduino board, yet there's a whole industry that lies within that chip.
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/0a49e86c-5ae0-4750-ad90-fffbb5ea83a8" /><br>

This board can also be described in the form of a block diagram:
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/9f84f641-6a83-483a-a2df-b5ca90e514c0" /><br>
The center is a processor and around it is all the programs that go into the processor. This is a typical diagram of a board.

But the other stuff ain't that important, so let's dive deeper into the chip. 
<img width="456" height="443" alt="image" src="https://github.com/user-attachments/assets/ffa30fdb-2e30-44f8-b65f-2dacf8c8cece" /><br>
This is a chip or in more technical terms: a package. 

The chip is sitting at the center. Wire bunch connects the pins to the boundary of the chip, which allows signals to travel to the chip. 

<img width="411" height="257" alt="image" src="https://github.com/user-attachments/assets/27edb3b3-3b65-4788-aa43-47074990fb0d" /><br>

- PADS: Signal travels through the pads and into the pins and vice versa.
- CORE: Place where digital logic sits.
- DIE: Silicon that the circuit is fabricated on.

<img width="517" height="275" alt="image" src="https://github.com/user-attachments/assets/59581eb8-a8c5-4f12-b1da-0b3b7a7aaae6" /><br>
The core includes some components like the RISCV SoC, SRAM, adc0, adc1, dac, PLE, and SPI. All performances depend on the foundry, the place where chips get manufactured. Engineers contact foundries.
- Foundry IP's or Intelligent Property: This need some amount of integllegine to build this block.
- Macros: Pure digital logic.

### 1 - Introduction to RISC-V
RISC-V is a language of the computer and a way of communication to the computer. If you want a C program to run on this particular layout.

<img width="1706" height="650" alt="image" src="https://github.com/user-attachments/assets/741e0621-afe7-4afd-a5ad-58ea7ccf7fd3" /><br>

The C program is first compiled in its assembly language program. which is converted to machine program which is binary program, which is understood in computers. Finally, the sketch gets converted to the particular layout.


<img width="798" height="504" alt="image" src="https://github.com/user-attachments/assets/456d4298-3031-4403-8679-ae0152f6079d" /><br>

There is another interface that has to be present with RISC-V and layout which is th eahrdware description language. ou have to implement this architecutre in some rdl which in this case is picorv32 cpu core. This rdl implements specifications of RISC-V architecture and finally from implementaiton to layout it is a standard gds flow. 

### 2 - From Software Applications to Hardware
These apps run on hardware but how does all of these processes happen?  

<img width="1744" height="1080" alt="image" src="https://github.com/user-attachments/assets/a6ae9135-1b97-4a5b-bce7-f983e03001d6" /><br>
Application Software -> System Software -> Hardware

It starts from the application software which is programmed in its respective language. Next, the code will be dealt with by the OS. In the OS, the compiler will translate the programming language to some instructions that is set by the hardware's manufacturer. Then, the assembler will take those instructions and translate it to a machine lanuage (binary), which will be fed to the hardware. Finally the hardware processes that information and produces a result. 

System Software
- Compiler: Converts incoming programs to respective instructions
- Assembler: takes the respective instructions to binary language, which is fed to hardware
- OS: translates the app into assembly language into binary so hardware can understand

Hardware
- Whoever owns the hardware will have the instructions implemented by the company.
- understands assembler's inputs and engenders output













