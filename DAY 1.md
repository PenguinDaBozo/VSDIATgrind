# Sky130 DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
## How to talk to computers

### 0 - Introduction to QFN-48 Package, chip, pads, core, die and IPs

A very common Arduino board, yet there's a whole industry that lies within that chip.
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/0a49e86c-5ae0-4750-ad90-fffbb5ea83a8" /><br>

This board can also be described in the form of a block diagram:
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/9f84f641-6a83-483a-a2df-b5ca90e514c0" /><br>
The center is a processor and around it is all the programs that go into the processor. This is a typical diagram of a board.

But the other stuff ain't that important, so let's dive deeper into the chip. 
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/ffa30fdb-2e30-44f8-b65f-2dacf8c8cece" /><br>
This is a chip or in more technical terms: a package. 

The chip is sitting at the center. Wire bunch connects the pins to the boundary of the chip, which allows signals to travel to the chip. 

<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/27edb3b3-3b65-4788-aa43-47074990fb0d" /><br>

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

There is another interface that has to be present with RISC-V and layout which is the hardware description language. ou have to implement this architecutre in some rdl which in this case is picorv32 cpu core. This rdl implements specifications of RISC-V architecture and finally from implementaiton to layout it is a standard gds flow. 

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

## SoC design and OpenLANE

### 3 - Introduction to all components of open-source digital asic design
ASIC requires certain elements that must be present always.
- RTL IP's: hardware description language register transfer model, all the functions we want to implement
- EDA Tools: CAD tools used for electronic automation
- PDK DATA or Process Design Kit: The interface betweem FAB amd designers. Collection of files used to model fabrication process for EDA tools used to design an IC.

<img width="405" height="450" alt="image" src="https://github.com/user-attachments/assets/7a7fb7ba-08a5-4fdd-b7ef-22c6efb92bd5" /><br>

Back in the days, the design of an IC was coupled by only a few companies. Lynn Conway and Carver Mead envisioned need for separating design from technology, pioneering the "structured" design methodolody. This sparked Pure Play Fabs and Fabless design companies.

Until June 30, 2020, there were no open sourced PDK. In June 30, 2020, Google and Skywater made an agreement to open source the FOSS 130nm Production PDK. The PDK had all the information needed for successful ASIC implementation.

Now, we have all three elements for open-source. But isn't 130nm production an old one given it has been around for 20 years? Well, surprisingly the 130nm still works. The cutting edge process node is 5nm. The current market share for a 130nm is 7%.

Attributes:
- civil applications does not need a performance of an advanced node
- fabrication for 130nm is cheaper when compared to advanced nodes

<img width="517" height="370" alt="image" src="https://github.com/user-attachments/assets/c4a22b73-d944-4f48-b54e-77b686c3d553" /><br>

130 nm is indeed fast! 
- Example 1: Intel Pentium 4, which was released in 2004, ran at almost 3.46 GHz.
- Example 2: OSU team reported 327 MHz post-layout clock

### 4 - Simplified RTL2GDS flow
ASIC design flow:
<img width="568" height="369" alt="image" src="https://github.com/user-attachments/assets/0214c12b-14e7-49ab-a358-3ca12bc78b11" />

Synthesis: 
<img width="553" height="381" alt="image" src="https://github.com/user-attachments/assets/a25f8dba-4267-46b8-ac4b-c25f832a6850" /><br>
- Converts RTL to a circuit out of componetns from the standard cell library (SCL)

FP+PP (Floor and Power Planning): 
<img width="540" height="394" alt="image" src="https://github.com/user-attachments/assets/b2539179-2485-44ff-8c17-4fc7b2a5c4fc" /><br>
- Chip Floor-Planning: partition the chip die btwn different system building blocks and place the I/O Pads
<img width="552" height="384" alt="image" src="https://github.com/user-attachments/assets/1b8cfe21-2bf8-4bb0-a677-64881d472625" /><br>
- Macro Floor-Planning: Dimensions, pin locations, rows definition
<img width="562" height="375" alt="image" src="https://github.com/user-attachments/assets/9d0a39bf-c03d-4e62-8a85-9c5ac669f046" /><br>
- Power Planning: Each chip is powered by multiple VDD VSS pins. The power pins are connected through all rings and vertical horizontal straps. Parallel structures reduces resistance. The distribution network uses upper metal layers as they are thicker than lower metal layers and have less resistance. 

Place:
<img width="537" height="200" alt="image" src="https://github.com/user-attachments/assets/a6cd8180-134c-4fe0-85c9-802d0408aebc" /><br>
For macros, place the cells on the floorplan rows, aligned with the sites. Connected cells should be palced close to each other to reduce the interconnected delay. Also to enable successful routing afterward.
<img width="502" height="202" alt="image" src="https://github.com/user-attachments/assets/6b7334f2-946f-405a-b59d-2303adc8ccc6" /><br>
- Done in 2 Steps: Global and Detailed
- Global: find optimal position for all cells
- Detailed: Postitions from global are minimally altered

CTS:
<img width="557" height="198" alt="image" src="https://github.com/user-attachments/assets/024c60af-e3d0-4868-9694-420e599a985e" /><br>
Creates a clock distribution network, which looks like a tree. Clock deliver signal to all components with minimal latency.

Route:
Implement the interconnect using the available metal layers. The router uses available metal layers as defined by PDK. PDK defines the width, minimun tract, pitch, vias, and thickness. 
<img width="538" height="226" alt="image" src="https://github.com/user-attachments/assets/7ba97f20-6977-4d39-bf09-91032a68c3cb" /><br>
The Sky130 defines 6 layers: Interconnect layer(lowest), 5 aluminum layers after

Most routers are grid routers. They construct routing grids out of the metal layer tracts. The routing grid is huge and uses a divide and conquer method to cover the area. 
- Global Routing: generates routing guides
- Detailed Routing: Uses the routing gudies to implement the actual wiring

Sign Off:
Once done with routing, we can construct the final layout, which undergoes verifications. 

Physical Verifications
- Design Rules Checking (DRC)
- Layout vs Schematic (LVS)

Timing Verification
- Static Timing Analysis (STA)







### 5 - Introduction to OpenLANE and Strive chipsets
### 6 - Introduction to OpenLANE detailed ASIC design flow












