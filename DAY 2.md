# Sky130 DAY 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells
## Chip Floor planning considerations
### 12 - Utilization factor and aspect ratio
1) The first step of the floor planning process is to define the width and height of the core and die.
  - Start with a netlist, which describes connectivity of an electronic design

<img width="553" height="216" alt="image" src="https://github.com/user-attachments/assets/941ec159-57b2-4e35-83c4-2bcf20467291" />

The design is dependent on the size of logic ages and flip flops so lets convert the symbols to physical dimensions:
<img width="545" height="367" alt="image" src="https://github.com/user-attachments/assets/b5ab57ae-8cbe-4bf9-9e81-b46413772b58" />

Right now, the dimensions of the standard cell are important so we can ignore the wires. Let's assume the areas of the cells and flipflops.
<img width="533" height="415" alt="image" src="https://github.com/user-attachments/assets/52c0c8a8-b3e3-4a09-acf4-c5060ef5a2e2" />

With the help of the dimensions, we will calculate the area occupied by the netlist on a Silicon Wafer by simplifying the netlist to blocks without wires and putting them together like this:

<img width="248" height="203" alt="image" src="https://github.com/user-attachments/assets/9413daf6-35b6-48ef-9938-d3f043ce234e" />

minimum area occupied by netlist

**What is the 'core' and 'die' Section of a chip?**

<img width="344" height="281" alt="image" src="https://github.com/user-attachments/assets/d19c7d4d-301f-4290-b548-f31db65e032a" />

<img width="193" height="172" alt="image" src="https://github.com/user-attachments/assets/225ac459-2865-4403-a0bd-2ab706f44dc1" />

<img width="209" height="193" alt="image" src="https://github.com/user-attachments/assets/c3088e8e-2bb7-4e0c-9820-3f10c8ddc062" />

- Core (second image): section of the chip where fundamental logic of design is place and is located inside a die
- Die (third image): small semiconductor material specimen on which the fundamental cirucit is fabricated. We put multiple die on a wafter to increase its input. 

Lets put the netlist inside the core, and boom, the netlist occupies the complete area of the core, so we can say that it is 100% occupied or utilized.

<img width="225" height="240" alt="image" src="https://github.com/user-attachments/assets/2972311f-e4d6-43d3-a1f6-3b3c4155c8a3" />

100% utilization is when the whole core area is occupied. We can also calculate the **Utilization Factor** by 
  (AREA OCCUPIED BY NETLIST)/(TOTAL AREA OF THE CORE)

When utilization factor = 1, you can't add additional cells because the area is fully occupied. In practice you should go for 50 - 60% utilization or 0.5 - 0.6 ultitization factor.

Another important aspect is the aspect ratio, which determines the shape of the die. We can calculate this by 
  HEIGHT/WIDTH

Whenever the aspect ratio is 1, it's a square. Anything else means a rectange. 

Another example: 

<img width="733" height="443" alt="image" src="https://github.com/user-attachments/assets/52206b86-4e9f-4490-a3f8-5466d835cc9d" />


### 13 - Concept of pre-placed cells
2) The next step of floor planning is to define the locations of preplaced cells.

So what is floorplanning? It is the arrangement of the  IP's in a chip. And Pre-placed cells are IP's/blocks that have user-defined locations are placed in a chip before automated placement and routing. 

To define locations, let's start with this circuit. This circuit is pretty big:

<img width="628" height="162" alt="image" src="https://github.com/user-attachments/assets/288d8ae5-3609-44db-b928-e3dd0a1bef8d" />

We can break this circuit down into two parts. We separate both of the blocks and then when they are conected to each other, they will perform some function. 

<img width="656" height="197" alt="image" src="https://github.com/user-attachments/assets/f44000cc-4fc2-4391-9f16-bb84e976c104" />

Now lets extend the IO pins

<img width="346" height="140" alt="image" src="https://github.com/user-attachments/assets/42cf2dd2-e92b-4aee-a0e4-4b363b1441f1" />

Black box the boxes, which makes the blocks invisible to top netlist. 

<img width="320" height="117" alt="image" src="https://github.com/user-attachments/assets/da986ed3-dbc9-49f4-bd24-a9062d734640" />


<img width="510" height="142" alt="image" src="https://github.com/user-attachments/assets/8bed4482-109f-4ca8-8a29-94d254b3ade2" />

*The 4 yellow lines will now behave like outputs for block 1 and inputs for block 2.*

The blocks will be implemented separately and the advantage of this is resuability and are preplaced cells. 

<img width="472" height="152" alt="image" src="https://github.com/user-attachments/assets/cb9b268d-ad6b-4a50-ae22-5c9e64f0a7e9" />

There are also other IP's available like memory, clock-gating cell, comparator, mux...

These pre-placed cells will only be implemented once and can be reused. Then, automated placement and routing tools will place the remaining logical cells in the design onto the chip. Once these cells are placed onto a floorplan, they are fixed and not touched by automated placement and routing tools.


So, how do we define the location of these cells?

<img width="508" height="372" alt="image" src="https://github.com/user-attachments/assets/cb0ecbaa-6b4c-4dff-bccd-26bfc559bbe0" />

We define the location of the cells based on the design scenario. For this case, we know the blocks are communciating more with the input so we put it close to the input side. Once they're placed here, they can't be moved. 

### 14 - De-coupling capacitors

3) Surround pre-placed cells with Decoupling capacitors

This piece of circuit is part of block a, block c, and block b. When the output switches from 0 to 1, there is an amount of current needed. Whenever there is a transition, this capacitance has to completely charge to respresent 1, so the amount of capacitance charge is sent by the supply voltage. It is the responsibility of the supply voltage to supply the logic. Whenever 1 to 0, it is vss responsibilty to take that charge, so in theory all the capacitance will get discharged which should be handled by GND. 

<img width="711" height="344" alt="image" src="https://github.com/user-attachments/assets/dc9b5613-5b11-43aa-9f7a-6538136857e7" />

In reality, when power supply flows to glogic, there is a drop because of physical dimensions. Anything that has physical dimensions has some resistance. Whenever when this supply tries to flow from + to the gates, there will be voltage drops. VDD- is not always 1 volt because of voltage drops. The .7 volt will go into cicuit and will go into logic and if there is an output for 0 to 1, it will be 0.7 volts because thats the amount of supply available. The 0.7 volts should be within the noise margin range. 

<img width="614" height="374" alt="image" src="https://github.com/user-attachments/assets/a88c9a17-5220-4647-85b4-edea720881e9" />

If 0.7V lies in the 1 area, we're good, but if its in the undefined region, then it is unpredictable and we can't guarantee power supply so what should we do? That's where decoupling capacitors come in. 

<img width="706" height="389" alt="image" src="https://github.com/user-attachments/assets/6093a945-9525-4659-8ba7-04b1fdca3d22" />

Decoupling capacitors are huge capacitors. Whenever circuit switches it gets power from Cd, it deocouples ciruit from main power supply.  And since it is placed close to circuit, there will be hardly any voltage drop. When switching is happenning, the capacitor loses charge, but when switching is not happening, it is resupplying charge using power supply. 

In the chip it will look like this: 

<img width="500" height="387" alt="image" src="https://github.com/user-attachments/assets/163ac17a-d5ef-4295-8219-fe508cb411fc" />

Now there won't be any missing 1 or 0 because the capacitor will make sure it will never go in the undefined region. 

### 15 - Power planning

4) Power Planning 

We have another problem. If this particular macro is repeated multiple times, there will be curernt demands for each and every element of the macro. Lets say this is a complete chip. There is a signal from driver to load. We have to make sure this line maintains the same signal the whole time. 

<img width="388" height="305" alt="image" src="https://github.com/user-attachments/assets/1f74d059-308f-4d80-b607-d8c0074a1324" />

These blocks have been tapped to VDD and all the block GND lines area tapped to GND. Assume this particular line is a 16-bit bus. This line has to maintain this particular scenario the whole time so load can recieve the same signal.

<img width="469" height="378" alt="image" src="https://github.com/user-attachments/assets/22611588-4a5f-4ad5-a608-8fbd561f95d1" />

For this line to maintain the same scenario, it should obtain adequate power from supply, but there's not decoupling capacitors that will take care of this particular scenario. The power supply is the one to supply this line, but it's a bit far so there is a possibility of volatage drop. 

Let's dive deeper. This is a 16-bit bus:

<img width="558" height="361" alt="image" src="https://github.com/user-attachments/assets/1b0e6aa7-927a-4a30-8680-3119e8aa795e" />

Each line is a logic bit. When 1, it is charged to VDD. When 0, it is charged to GND.

<img width="564" height="205" alt="image" src="https://github.com/user-attachments/assets/2a74c3d9-5729-411e-b0f7-3fc72827e377" />

When you pass this particular logic to the inverter, it will be inverted. All the charged to VDD will be charged to 0 all at the same time and vice versa. But this will cause a problem since it all happens at the same time. A ground bounce will occur. If the size of this ground bounce exits the noise margin level, it might eneter into an undefined state, which is bad. 

For 0 to 1, it is basically the same and creates a voltage droop and if it enters undefined state, then it is also bad.

<img width="548" height="195" alt="image" src="https://github.com/user-attachments/assets/59cd7b0d-8077-4d56-a5bc-99fb7e2ecf7e" />

This problem stems from the fact that power is supplied at one point. If there were multiple supplies, then this problem would not happen since each one would take power from closest supply. 

Instead of a single power supply, we should have multiple like this: 

<img width="559" height="402" alt="image" src="https://github.com/user-attachments/assets/831f291b-1504-4090-8858-8284e154b759" />

If some logic demands power, it will tap power from the nearest line. This is called a mesh. Now let's apply to our die.

<img width="664" height="385" alt="image" src="https://github.com/user-attachments/assets/d941a5f6-06aa-47ee-99c1-2490bc621cc8" />

<img width="649" height="385" alt="image" src="https://github.com/user-attachments/assets/6052dc89-b2c6-4837-8200-d6b229b45683" />

### 16 - Pin placement and logical cell placement blockage

5) Pin Placement

Example Circuit: 

<img width="550" height="336" alt="image" src="https://github.com/user-attachments/assets/e99ecc8a-7c25-46af-9aff-291a97f2a3f0" />

<img width="524" height="344" alt="image" src="https://github.com/user-attachments/assets/be3b2f93-e0b9-4609-bfec-b83b3b007501" />

We put them together and connect the respective outputs with each other and this is our complete design:

<img width="574" height="407" alt="image" src="https://github.com/user-attachments/assets/e820bf61-5065-4c85-85d5-377c63666869" />

Most designs usually have the input on the left and the outputs on the rigt. It is up to designer's preference. 

<img width="644" height="379" alt="image" src="https://github.com/user-attachments/assets/489e4a4c-8d32-4fc2-be33-dd5a6b8712c0" />

The placement of the pins is pretty simple since the pins will be placed according to where the corresponding cells are placed.

If you notice, CLK ports are bigger than Din because this is the port that is sending signal to the flip flops and drives the whole chip, which would require less resistance, explaining its big size.

6) Logical Cell Placement Blockage

Next step is to make sure none of automated stuff is placed in the die. The edge should be blocked off to make sure the automated placement doesn't get placed outside. 

<img width="506" height="381" alt="image" src="https://github.com/user-attachments/assets/6eac5001-fd97-4da8-bd83-5b4da42cfbfb" />

### 17 - Steps to run floorplan using OpenLANE

Set Area -> Set Aspect Ratio -> Localization factor -> Input/Output Cell -> Power Distribution Network -> Macro Placement Standard cells are not placed in floor plan. 

If you open up the README.md file in openLANE directory, you can check the variables of each design step. 

<img width="928" height="435" alt="image" src="https://github.com/user-attachments/assets/4713bba1-efa1-4c68-869c-d72c22cd9620" />

<img width="768" height="67" alt="image" src="https://github.com/user-attachments/assets/349d4942-a822-408a-a338-8e0247a0bfde" />

*FP stands for floor  plan. Core is the area of cell.*

If you open up the floorplan.tcl you can see the parameters that floor plan has been set to. 

<img width="722" height="505" alt="image" src="https://github.com/user-attachments/assets/22949bea-43d8-43b5-8ccf-98d7cf5c20d5" />

Priority (highest to lowest): floorplan.tcl, config.tcl, sky130A_sky130_fd_sc_hd_config.tcl

If we open up the config.tcl, you can see the IO_VMETAL and IO_HMETAL. In the flow, it will be one more than what config is set to. 

In openlane, after Synthesis, we should run_floorplan to create a floor plan.  

<img width="915" height="379" alt="image" src="https://github.com/user-attachments/assets/0d1dd1ee-8600-4c87-b46c-4d795a29b9f6" />

### 18 - Review floorplan files and steps to view floorplan

<img width="1357" height="160" alt="image" src="https://github.com/user-attachments/assets/c69b4124-c0b9-4cdd-aa47-33a80b3835cb" />

<img width="356" height="29" alt="image" src="https://github.com/user-attachments/assets/4db2249d-2d20-4643-bb20-a774cc5e206f" />

The Vertical Metal Layer and Horizontal layer is indeed 1 more than config.tcl, which means floorplan has overwritten config.tcl. The sky130A file overrided the config.tcl for core util.

<img width="986" height="105" alt="image" src="https://github.com/user-attachments/assets/70be3c7a-88dd-48cb-9ac0-b230243cb4eb" />

<img width="611" height="20" alt="image" src="https://github.com/user-attachments/assets/8dda328d-e856-48fb-b4bb-0f27e42f2149" />

Using the two numbers, we can calculate the area of the design. 

<img width="976" height="57" alt="image" src="https://github.com/user-attachments/assets/97903c0d-aa5d-4f3a-9a7b-e1222be6f3d8" />

We can open magic using this command. -T is for tech file and the file is the tech file location. With the magic tech file we need the lef file and that's why we move 2 directories up. Finally we do def read and we don't have to put the def file because we're in the def file. And an & to move next prompt when magic launches. 

### 19 - Review floorplan layout in Magic

To select: press S 
To center: S then V 

<img width="1226" height="763" alt="image" src="https://github.com/user-attachments/assets/3855a147-e700-47f4-b93d-588e756fd002" />

To zoom: left-click and then right-click to creat the window you want to zoom to and press Z

<img width="1223" height="734" alt="image" src="https://github.com/user-attachments/assets/e0595fba-66e9-4e02-a3ca-c9109a1fd471" />

We can select a cell by hovering over it and clicking S. Then we can go in the terminal and ask what, which tells us the details. 

<img width="827" height="503" alt="image" src="https://github.com/user-attachments/assets/2bb83101-e7c2-4d0f-913c-e4264a8fe4d4" />

*this one is metal 3*

<img width="930" height="650" alt="image" src="https://github.com/user-attachments/assets/fd243807-e655-47f9-a801-1ed3ebd4d25d" />

*this one is metal 2*
These should be what is set in one of the tcl files. 

<img width="350" height="227" alt="image" src="https://github.com/user-attachments/assets/1ff35b55-d173-4010-b47b-130331f46819" />

*tax cells: avoid latch up that occur in CMOS devices. Connect the attach ember to vdv and the substrate to the GND, which prevents latch up.*
If you open the README.md, you can see which tax cell is set. 

Floor plan does not take into consideration the placement of standard cells but standard cells are present here (bottom left). 

<img width="1131" height="566" alt="image" src="https://github.com/user-attachments/assets/45b29047-7939-4d1a-965a-cbf0b0502ff8" />

## Library Binding and Placement

### 20 - Netlist binding and initial place design

**Placement and Routing**

1) Bind netlist with physical cells

Shape of this gate represents functionality of the gate. For example, or gate. 

<img width="498" height="430" alt="image" src="https://github.com/user-attachments/assets/7f2cdc49-cbc8-4b2e-b775-60411898a0eb" />

We don't have specific shapes but we do have boxes. Take the components and give physical dimentsions.

<img width="662" height="438" alt="image" src="https://github.com/user-attachments/assets/7af895db-1a96-4d9c-b468-23c27aace26c" />

<img width="156" height="279" alt="image" src="https://github.com/user-attachments/assets/7a4fb3e9-21e1-4b0a-91dd-2900789a8462" />

*This is a shelf called library. The library also has the timing, width, height, required conditions of cell, and particular shapes of cell.*

<img width="811" height="281" alt="image" src="https://github.com/user-attachments/assets/4acf7aa1-dd6e-4d41-885d-cebffb65e2a0" />
*library got different flavors. bigger = faster since less resistance*

2) Placement: Once we have given proper shape and sizes to the gates, we have to place them. 

<img width="835" height="345" alt="image" src="https://github.com/user-attachments/assets/22f9b1b6-e2b7-4521-8e0f-47c03fc48f11" />

We have to place the netlist to the floorplan. 

<img width="588" height="411" alt="image" src="https://github.com/user-attachments/assets/2ac43299-ed6e-49fa-8f1f-c6704ca83b68" />

This is our floor plan we previously created.

<img width="848" height="428" alt="image" src="https://github.com/user-attachments/assets/6b7cdade-26f6-4067-95ba-da4582d03597" />

You place the cells close to its respective input/output so the delay is mininal. 

### 21 - Optimize placement using estimated wire-length and capacitance

<img width="848" height="415" alt="image" src="https://github.com/user-attachments/assets/98b95bcd-6ec1-42c8-a514-61a8de8fa377" />

The input/output is kind of far but is diagonal, so we place diagonally.

<img width="837" height="409" alt="image" src="https://github.com/user-attachments/assets/672455d8-7a77-4766-911c-9981f7a53a29" />

There's a bunch of preplaced cells blocking so we have to sort of wrap around it while making sure the cells are close to their respective input/output. 

And this arises a question of distance.

The solution is...

3) Optimize Placement

Now we shall perform estimations. This is the part where we estimate wire length and capacitance and, based on that, insert repeaters. Repeaters are buffers that will recondition your original signal by making a new signal that replicates original signal. More and more repeaters will take up area. Slew, time of signal transition, is dependent upon the value of capacitor and is used to decide the placement of the repeaters. 

<img width="841" height="367" alt="image" src="https://github.com/user-attachments/assets/a2a032bd-9bd8-4d82-ae57-0f0ccabae7d1" />

The distances btwn each cell is pretty reasonable so we don't need to add repeaters.

<img width="842" height="419" alt="image" src="https://github.com/user-attachments/assets/b96e1345-60a0-4890-825c-ee0ca92b413c" />

We placed buffers since the distance would be too large. The buffers will recieve the signal and replicate it to the next. The yellow blocks are close to each other, which means minimum delay. 

### 22 - Final placement optimization

<img width="838" height="413" alt="image" src="https://github.com/user-attachments/assets/9e660021-98f9-408b-9ed6-962fd5d05471" />

Placed a buffer between FF2 and 2 because the distance is a bit far. 

<img width="847" height="412" alt="image" src="https://github.com/user-attachments/assets/d4925bf2-687e-4418-a5ab-9aa58c3123a9" />

The connection btwn FF1 and 1 criss cross with the blue blocks, which does cause a problem that we will address latter. Same with the yellow and green blocks but that can be solved by putting the green blocks on a different layer than yellow blocks. 

### 23 - Need for libraries and characterization

<img width="763" height="431" alt="image" src="https://github.com/user-attachments/assets/0fe9772c-e476-45c5-b479-0ea41547efbe" />

LOGIC SYNTHESIS: First part of IC design flow is logic synthesis.

<img width="760" height="352" alt="image" src="https://github.com/user-attachments/assets/590a3ab1-c9c4-4be7-943b-cadd18e1eebe" />

FLOOR PLANNING: Next step is the floorplanning in which we decide the dimensions of the core and the die, which are dependent on the size of the gates. 

<img width="752" height="364" alt="image" src="https://github.com/user-attachments/assets/fb7317ec-6274-42ce-a0b2-206b41b8548f" />

PLACEMENT: Then, we have the placement and we place the cells close to its respective pin so that we get the best timing possible. But if it is not possible to keep them close, then we add buffers. 

<img width="664" height="288" alt="image" src="https://github.com/user-attachments/assets/cacd3210-aae3-420e-b2e9-32d23a8c7a29" />

CTS: Next, we have the clock tree synthesis (CTS), which is the cells recieve logic at an equal time because of the clock being spread across. It is an edge tree that will take care of each and every clock endpoints. The buffers (triangles) will make sure that the clock signals have equal rise and fall.

<img width="754" height="288" alt="image" src="https://github.com/user-attachments/assets/b01a25f1-70e8-46fa-ad16-d1a48f2aedd2" />

ROUTING: Routes the stuff together. Dependent on the characters of the cells. 

<img width="507" height="342" alt="image" src="https://github.com/user-attachments/assets/8c64dc24-a841-4439-a39a-2e09ccd7c60f" />

STATIC TIMING ANALYSIS: You see the setup time, arrival time, max achievable frequency of a circuit. 

One thing is common across all stages: the Cells or Gates.

<img width="200" height="243" alt="image" src="https://github.com/user-attachments/assets/5a326941-a001-440c-b17c-12f126ee1fac" />

If you place any of this gate in some area, then it is referred to as your library. These gates have to be placed in a way the EDA understands them but how?

How do we design, characterize or model these cells?

### 24 - Congestion aware placement using Replace

Placement in OpenLANE occurs in two stages: global and detailed. 

Global: a course placement; no legalizations happening. Legalization makes sure the standard cells are placed in rows and are exactly inside them with no overlap. 

run_placement runs global placement and the main objective is to reduce wire length.

<img width="911" height="403" alt="image" src="https://github.com/user-attachments/assets/3fc2e5c6-80b0-4653-816b-dd467418f1b9" />

<img width="892" height="70" alt="image" src="https://github.com/user-attachments/assets/20eb6d82-9583-44fc-a91b-74e1c9ba457d" />

<img width="966" height="589" alt="image" src="https://github.com/user-attachments/assets/f78dd242-2d37-41be-810e-b236671c4614" />

<img width="812" height="551" alt="image" src="https://github.com/user-attachments/assets/5d3bebf4-0bf6-4daa-bd8b-cc84d497792c" />
*all the standard cells are now placed in rows*

The power distribution network is created during floor plan. But in OpenFLOW, the order is a little different so the floor plan does not create PDN. Post floor plan and post placement CTS create power ground condition. Power ground is not done currently. 

## Cell Design and Characterization Flows
### 25 - Inputs for cell design flow
### 26 - Circuit design step
### 27 - Layout design step
### 28 - Typical characterization flow

## General Timing Characterization Parameters
### 29 - Timing threshold definitions
### 30 - Propagation delay and transition time
