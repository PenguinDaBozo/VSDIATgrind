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

<img width="711" height="344" alt="image" src="https://github.com/user-attachments/assets/dc9b5613-5b11-43aa-9f7a-6538136857e7" />

This piece of circuit is part of block a, block c, block b, when the output swicthes from 0 to 1, there is an amount of current needed. whenever there is a transition from 0 to 1, this capacitance has to completely charge to respsernt 1. So the amount of capacitance charge is sent by the supplyu voltage. So it is the responsibility of the supply voltage to supply the logic. 

Whenver 1 to 0 it is vss responsibilty to take that charge. So all the capacitance will get discharged which should be handled by GND. 

In reality, when power supply flows to glogic, there is a drop because of physical dimensions. Anythibng that has physical dimensions has some resistance. Wheenver when this supply tries to flow from + to the gates, there will be voltage drops. VDD- not possible always 1 volt if power supply is 1V and is less. The .7 volt will go into cicuit and will go into logic and if there is an output for 0 to 1, it will be 0.7 volts because thats the amount of supply available. The .7 volts should be wihtin th enoice margin range. 

<img width="614" height="374" alt="image" src="https://github.com/user-attachments/assets/a88c9a17-5220-4647-85b4-edea720881e9" />

If 0.7V lies in the 1 area, we're good but if its in the undefined region, then it is bad. So we can't guarantee power supply so we can solve this using decoupling capacitors.

<img width="706" height="389" alt="image" src="https://github.com/user-attachments/assets/6093a945-9525-4659-8ba7-04b1fdca3d22" />

Decoupling capacitors are huge capacitors. Whenever circuit switches it gets power from Cd and it deocouples ciruit from main power supply.  And since it is placed clsoe to circuit, there will be hardly any voltage drop. When switching is happenning, the capacitor loses charge but when siwtching is not happening, it is resupplying charge using power supply. 

In the chip it will look like this: 

<img width="500" height="387" alt="image" src="https://github.com/user-attachments/assets/163ac17a-d5ef-4295-8219-fe508cb411fc" />

Now there won't be any missing 1 or 0 because the capacitor will make sure it will never go in the undefined region. 

### 15 - Power planning

4) Power Planning 








### 16-Pin placement and logical cell placement blockage
### 17-Steps to run floorplan using OpenLANE
### 18-Review floorplan files and steps to view floorplan
### 19-Review floorplan layout in Magic

## Library Binding and Placement
### 20-Netlist binding and initial place design
### 21- Optimize placement using estimated wire-length and capacitance
### 22-Final placement optimization
### 23-Need for libraries and characterization
### 24-Congestion aware placement using Replace

## Cell Design and Characterization Flows
### 25-Inputs for cell design flow
### 26-Circuit design step
### 27-Layout design step
### 28-Typical characterization flow

## General Timing Characterization Parameters
### 29-Timing threshold definitions
### 30-Propagation delay and transition time
