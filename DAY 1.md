# Sky130 DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
## How to talk to computers

### 0 - Introduction to QFN-48 Package, chip, pads, core, die and IPs

A very common Arduino board, yet there's a whole industry that lies within that chip.

<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/0a49e86c-5ae0-4750-ad90-fffbb5ea83a8" /><br>

This board can also be described in the form of a block diagram:

<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/9f84f641-6a83-483a-a2df-b5ca90e514c0" /><br>

The center is a processor and around it is all the programs that go into the processor. This is a typical diagram of a board. But the other stuff ain't that important, so let's dive deeper into the chip. 

<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/ffa30fdb-2e30-44f8-b65f-2dacf8c8cece" /><br>

This is a chip or in more technical terms: a package. The chip is sitting at the center. Wire bunch connects the pins to the boundary of the chip, which allows signals to travel to the chip. 

<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/27edb3b3-3b65-4788-aa43-47074990fb0d" /><br>

- PADS: Signal travels through the pads and into the pins and vice versa.
- CORE: Place where digital logic sits.
- DIE: Silicon that the circuit is fabricated on.

<img width="517" height="275" alt="image" src="https://github.com/user-attachments/assets/59581eb8-a8c5-4f12-b1da-0b3b7a7aaae6" /><br>

The core includes some components like the RISCV SoC, SRAM, adc0, adc1, dac, PLE, and SPI. All performances depend on the foundry, the place where chips get manufactured. Engineers contact foundries.
- Foundry IP's or Intelligent Property: This need some amount of integllegine to build this block.
- Macros: Pure digital logic.

### 1 - Introduction to RISC-V
RISC-V is a language of the computer and a way of communication to the computer. 

<img width="1706" height="650" alt="image" src="https://github.com/user-attachments/assets/741e0621-afe7-4afd-a5ad-58ea7ccf7fd3" /><br>

If you want a C program to run on this particular layout, the C program is first compiled in its assembly language program. which is converted to machine program which is binary program, which is understood in computers. Finally, the sketch gets converted to the particular layout.


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
Now applying the ASIC design flow, is it easy to build one? Well, kinda if you know what you are doing and have access to industry level applications. 

The problem is tougher when using Open Source EDA. You need to worry about missing tools, tools qualifications, and tools calibration. With the release of open source PDK, EFABEE decided to create an open source ASIC implementation flow: OpenLANE. 

OpenLANE comes with the Apache version 2.0 license. You can use as long as you acknowledge credits and copyrights. OpenLANE started as an Open-Source flow for a true open source tape-out experiment. 

<img width="495" height="375" alt="image" src="https://github.com/user-attachments/assets/dcb58eb3-6fe4-4e4a-9565-f5efb8263053" /><br>

striVe is a family of open everything SoCs. This family has several members. 

OpenLANE:
- Main Goal: produce a clean GDSII with no human intervention. By clean, it means no LVS violations, no DRC violations, and possibly no timing violations.
- Tuned for SkyWater 130nm Open PDK and also supports XFAB180 and GF130G
- Containerized: functional outside of box. Instructions to build and run natively will follow
- can be used to harden(generate gds tool/final layout of) macros and chips
- two modes of operation: autonomous(push button flow, we configure flow and wait) or interactive(evntually run cmd one by one)
- Design Space Exploration: find best set of flow configs
- comes with large # of design ex: 43 with best configs and more will be added soon


### 6 - Introduction to OpenLANE detailed ASIC design flow
OpenLANE ASIC Flow

<img width="549" height="334" alt="image" src="https://github.com/user-attachments/assets/3f84e6c1-47c7-4caf-9039-b9c0620da385" /><br>

OpenLANE is based on several open source projects.

RTL Synthesis: Flow starts with RTL Synthesis. The RTL is fed to Yosys with time constraints. Yosys translate the RTL into a logic circuit using generic components. This circuit can then be optimized and mapped into cells by abc. abc has to be guided during optimization and this guidance comes in the form of abc script (synthesis strategies).

STA: strategies that targets the least area and best timing. Different designs can use different strategies to achieve objectives, and for that, we have synthesis exploration that can be used to generate plots.<br>

<img width="529" height="272" alt="image" src="https://github.com/user-attachments/assets/cb355e0b-ad03-496e-bb67-e781dd021b0c" /><br>

These plots show how the area and delay is affected by the synthesis strategy. Based on this plot, we can decide the best strategy.

Design Exploration: Used to sweep the design configs. There are more than 16 of them and generates reports like this one: <br>

<img width="527" height="278" alt="image" src="https://github.com/user-attachments/assets/c22f176c-0769-4337-86a3-1065e344adf1" /><br> 

This report shows different design metrics and violations after generating final layout. Useful for finding best config for design.

Regression Testing: Design exploration can also be used for regression testing. The openLANE team already is running ~70 designs and comparing the results to the best known ones. This will generate a report that shows the design metrics given the configurations and also the number of violations, which will be compared to the bets known results.<br>

<img width="228" height="236" alt="image" src="https://github.com/user-attachments/assets/c26873b1-3074-4533-ab18-99661a4c435c" /><br>

Design for testing(DFT): Optional; Scan insertion, automatic test pattern generation(ATPG), test patterns compaction, fault coverage, fault simulation. This step adds extra logic and this logic scans catchain as fabrication for testing. It can add digitack control, which enables external access to internet catchain.

Physical Implementation: Several steps done by OpenROAD app. Perform
- floor/power planning
- end decoupling capacitors and tap cells insertion
- placement: global and detailed
- post placement optimization
- clock tree synthesis (CTS)
- routing: global and detailed

Logic Equivalent Checking (LEC): every time the netlist is modified, a verification must be performed. CTS modifies the netlist while post placement optimizationss modifiies the netlist. LEC is used to formally confirm that the function did not change after modifying the netlist. Makes sure what we started with is what we end with. 

Dealing with Antenna Rules Violations: When a metal wire segment is fabricated, it can act as an antenna. Reactive ion etching causes charge to accumulate on the wire, and thus transistor gates can be damaged during fabrication. So transistors should be limited to address this issue -> job of router. If the router fails to do so, two solutions
- Bridging, which attaches a higher layer intermediary
- add antenna diode to leak away charges
With openLANE, they added a fake antenna diode next to every cell input after placement and run the antenna checker(Magic) on the routed layout. If the checker reports a violation on the cell input pin, then replace the Fake Diode cell with a real cell.

<img width="243" height="194" alt="image" src="https://github.com/user-attachments/assets/1c91c69d-57fa-4b6b-a7c5-a80fcb6f75e7" /><br>

Static Timing Analysis:
- RC extraction: DEF2SPEF
- STA: OpenSTA (OpenROAD)
This step highlights timing violations

Physical Verification DRC & LVS: 
- Magic is used for DRC and SPICE Extraction from layout
- magic and netgen are used for LVS, extracted SPICE by Magic vs verilog netlist

## Get familiar to open-source EDA tools
### 7 - OpenLANE Directory structure in detail
OpenLANE is a flow which comprises of many multiple open source EDA tools.The aim of openlane is to automate the entire RTL to GSII flow and make it clean and open source. 

------Linux commands-------

cd: change directory

<img width="419" height="63" alt="image" src="https://github.com/user-attachments/assets/e1c885fd-d510-4692-8036-2b82783ce763" /><br>

ls -ltr: list stuff in chronological order

<img width="608" height="99" alt="image" src="https://github.com/user-attachments/assets/7f423327-6318-43ed-9abd-872d8feb5245" /><br>

cmd name --help: instructions on how to use command

<img width="747" height="632" alt="image" src="https://github.com/user-attachments/assets/62ac67da-68ef-4783-b3b0-8f2e1dfb3f23" /><br>

clear: clears terminal

<img width="462" height="31" alt="image" src="https://github.com/user-attachments/assets/c5f5a1e9-b5f2-43e9-8e92-0ea43ff34820" /><br>

cd ../: exit out of current directory

-----Exploring OpenLANE tools-----

<img width="652" height="280" alt="image" src="https://github.com/user-attachments/assets/efcfaf9f-631a-4486-a9cd-e369c70de11f" /><br>

Skywater.pdk: folder that has all the PDK related files (timing libraries, left...)
open.pdks: scripts and files that migitates issue of open source and foundry compatibility (magic, netgen...)
sky130A: pdk that is compatible with open source involvement

*inside sky130A*

<img width="755" height="139" alt="image" src="https://github.com/user-attachments/assets/74d5a1d7-7b01-4f64-b8a2-459c700d89d5" /><br>

libs.ref: contains all the process specific files
libs.tech: files specific to the tools

*inside libs.ref*

<img width="845" height="274" alt="image" src="https://github.com/user-attachments/assets/a150d43e-9793-48ef-bc08-978b736167a7" />

*inside libs.tech*

<img width="844" height="243" alt="image" src="https://github.com/user-attachments/assets/0d8ef984-b33c-4828-a316-75ddaff33fd0" />

-----Get to OpenLANE-----

<img width="673" height="41" alt="image" src="https://github.com/user-attachments/assets/c966db82-041b-45a5-86f0-a01ab2e3ea94" /><br>

### 8 - Design Preparation Step
1) After getting into the openLane directory, run docker

<img width="400" height="423" alt="image" src="https://github.com/user-attachments/assets/20f49e8d-2a01-4cc1-b1fa-757bd89c2437" /><br>

2) Run flow interactive:
 - interactive: step by step process details and compares
 - without: runs complete rule

<img width="568" height="237" alt="image" src="https://github.com/user-attachments/assets/e0aa168c-d747-480f-98da-c68d606bdee0" /><br>

3) Download packages

<img width="597" height="258" alt="image" src="https://github.com/user-attachments/assets/7a7a243e-d299-4fa9-80eb-bf3583f1caa9" /><br>

OpenLANE has several designs and for this part, we're going to use picorv32. 

<img width="917" height="273" alt="image" src="https://github.com/user-attachments/assets/2152df09-8f72-41fe-8e67-92408f5c4fff" /><br>

config.tcl: bypasses any contributions that has been done already into a plane
priority: default, config.tcl, hd_config.tcl

4) Need to prep design because designs only has the 3 default files. Need to set up files specific to the flow; that location needs to be created.

<img width="734" height="417" alt="image" src="https://github.com/user-attachments/assets/be97b09f-402e-4d52-ae09-26a076bdb009" />

<img width="729" height="435" alt="image" src="https://github.com/user-attachments/assets/d535dec6-8ff9-41d8-bb6e-73540682320a" />

Changes after prep

<img width="887" height="196" alt="image" src="https://github.com/user-attachments/assets/d3287e37-24c7-4bc9-a363-28c68b73b0df" />

<img width="928" height="236" alt="image" src="https://github.com/user-attachments/assets/cd3c52d4-106c-4aa3-b6cb-e26ec36fcbb1" />

<img width="934" height="394" alt="image" src="https://github.com/user-attachments/assets/1577a65a-eb3b-4083-a234-7575cdd48ff2" />

### 9 - Review files after design prep and run synthesis

<img width="931" height="259" alt="image" src="https://github.com/user-attachments/assets/b479a722-fe71-4dca-b98e-02ad72dde9f8" /><br>

Layout; Synthesis is empty right now because nothing has been synthesized. Let's change that!

5) ```%run_synthesis``` to run synthesis

<img width="913" height="420" alt="image" src="https://github.com/user-attachments/assets/d828a8e0-5b34-4d76-8836-08992f7a6d55" /><br>


### 10 - OpenLANE Project Git Link Description
Github is a remote repository (project) collection and people can access it.
https://github.com/efabless/openlane 
Has all the documentation you need

### 11 - Steps to characterize synthesis results

Chip area

<img width="470" height="30" alt="image" src="https://github.com/user-attachments/assets/04277398-7543-4d4f-8a61-964de8e6d34c" /><br>

Number of cells

<img width="349" height="126" alt="image" src="https://github.com/user-attachments/assets/e83c5a58-815b-4deb-a5ac-8c77a1d2859c" /><br>

Number of D-flip flops

<img width="350" height="212" alt="image" src="https://github.com/user-attachments/assets/82bab485-0389-43e6-8109-1ab7c40c3347" /><br>

Using number of flip flops we can calculate our flip flop ratio, which is:
FLIP FLOP RATIO = # OF DFFs / # OF CELLS * 100

Results of synthesis

<img width="923" height="127" alt="image" src="https://github.com/user-attachments/assets/531c0c6a-b731-493c-8168-64d78e6726b5" />
<img width="928" height="302" alt="image" src="https://github.com/user-attachments/assets/b88a30ed-7014-4022-9b16-b948ccb813b4" />









