# Sky130 DAY 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells
## Chip Floor planning considerations
### 12 - Utilization factor and aspect ratio

1) Define the width and height of the core and die.
  - Start with a netlist, which describes connectivity of an electronic design
  - <img width="553" height="216" alt="image" src="https://github.com/user-attachments/assets/941ec159-57b2-4e35-83c4-2bcf20467291" />

dependent on the size of logic ages and flip flops

lets convert the symbols to physical dimension
<img width="545" height="367" alt="image" src="https://github.com/user-attachments/assets/b5ab57ae-8cbe-4bf9-9e81-b46413772b58" />

we are interested in the dimensions of the standard cell adn not the wires (still plays important role but not now)

let's assume the areas of the cells and flipflops
<img width="533" height="415" alt="image" src="https://github.com/user-attachments/assets/52c0c8a8-b3e3-4a09-acf4-c5060ef5a2e2" />

with the helpo of the dimensions, we will calculate the area occupoed by the netlist on a Silicon Wafer by simplifying the netlist to blocks without wires and putting them together like this:
<img width="248" height="203" alt="image" src="https://github.com/user-attachments/assets/9413daf6-35b6-48ef-9938-d3f043ce234e" />
minimum area occupied by netlist

<img width="344" height="281" alt="image" src="https://github.com/user-attachments/assets/d19c7d4d-301f-4290-b548-f31db65e032a" />

What is 'core' and 'die' Section of a chip?

<img width="193" height="172" alt="image" src="https://github.com/user-attachments/assets/225ac459-2865-4403-a0bd-2ab706f44dc1" />

Core: section of the chip where fundamental logic of design is place and is located inside a die

<img width="209" height="193" alt="image" src="https://github.com/user-attachments/assets/c3088e8e-2bb7-4e0c-9820-3f10c8ddc062" />

Die: small semiconductor material specimen on which the fundamental cirucit is fabricated. We put multiple die on a wafter to increase its input. 

lets put the netlist inside the core, and boom, the netlist occupies the complete area of the core, so 100%. 
<img width="225" height="240" alt="image" src="https://github.com/user-attachments/assets/2972311f-e4d6-43d3-a1f6-3b3c4155c8a3" />

100% utilization is when the whole core area is occupied. 
We can calculate the Utilization factor by (area occupied by netlist)/(total area of the core)

When ulitilzation facotr is 1, you can't add additional cells because the area is fully occupied. In practice you should go for 50 - 60% utilization or 0.5 - 0.6 ultitization factor.

Aspect ratio is height/width. Wheenver aspect ratio is 1, its a square shape. Other numbers would mean its a rectange. 

Another example: 
<img width="733" height="443" alt="image" src="https://github.com/user-attachments/assets/52206b86-4e9f-4490-a3f8-5466d835cc9d" />


### 13 - Concept of pre-placed cells
### 14 - De-coupling capacitors
### 15 - Power planning
### 16-Pin placement and logical cell placement blockage
### 17-Steps to run floorplan using OpenLANE
### 18-Review floorplan files and steps to view floorplan
### 19-Review floorplan layout in Magic
## Library Binding and Placement
### 20-Netlist binding and initial place design
### 21- Optimize placement using estimated wire-length and capacitance
### 22-Final placement optimization
### 23-Need for libraries and characterization
### 24-Congestion aware placement using RePlAce
## Cell Design and Characterization Flows
### 25-Inputs for cell design flow
### 26-Circuit design step
### 27-Layout design step
### 28-Typical characterization flow
## General Timing Characterization Parameters
### 29-Timing threshold definitions
### 30-Propagation delay and transition time
