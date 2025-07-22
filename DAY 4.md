# Sky130 DAY 4 - Pre-layout timing analysis and importance of good clock tree
## Timing modelling using delay tables
### 55 - Lab steps to convert grid info to track info

<img width="209" height="375" alt="image" src="https://github.com/user-attachments/assets/1871c4a5-bd0b-472f-9717-9ccf3996e373" />

This is where lef comes in because it has all the information. The guidelines to be followed while making a standard cell are -:

- The input and output ports must lie at the intersection of the horizontal and vertical tracks (this is to ensure the routes can reach the ports).
- The width and height of the standard cell must be odd multiples of the track's horizontal and vertical pitch respectively



<img width="201" height="279" alt="image" src="https://github.com/user-attachments/assets/081bafcf-ceb6-440a-8d9f-85da906ff4d4" />

Tracks are used during the counting stages. Routes (metal traces) can go over the tracks. You have to specify where you want your routes to go. X is horizontal track and Y is vertical track. The numbers after are the spacing.

You have to ensure A and Y are on the horizontal vertical track.

Press G to see the grids

<img width="564" height="380" alt="image" src="https://github.com/user-attachments/assets/7f3ce620-26c2-4c7c-868c-15e7df665b5c" />

<img width="671" height="243" alt="image" src="https://github.com/user-attachments/assets/7b01c89e-f4e5-4791-9cbe-9b426b0d6f2d" />

How to change dimension of grid

<img width="849" height="528" alt="image" src="https://github.com/user-attachments/assets/09db21a4-b45b-45e0-95ea-38f4b21daba7" />

<img width="541" height="493" alt="image" src="https://github.com/user-attachments/assets/0974c344-ab09-4f22-b678-81277eff9a42" />

Pins lie at the intersection of the grid in A and Y

<img width="513" height="607" alt="image" src="https://github.com/user-attachments/assets/5d3b0a7c-7c57-4fa2-804b-42b09bf4e129" />


### 56 - Lab steps to convert magic layout to std cell LEF

<img width="589" height="470" alt="image" src="https://github.com/user-attachments/assets/78129eb8-8461-463b-a67f-6d82879d9748" />


This white line define the area boundry and there are 3 boxes between the white lines

<img width="595" height="393" alt="image" src="https://github.com/user-attachments/assets/08403920-a2e8-4364-9451-d5c3d27b5d7e" />


Other guideline is it should be in the odd multiple of the x pinch

Same thing is required for the height of the standard cell

<img width="817" height="550" alt="image" src="https://github.com/user-attachments/assets/29c606d4-7974-44f3-b82f-3e09cdd7fe96" />

Port definition is required when you want to extract from lef file

So when you extract the lef file, these ports are the pins of the macro

How to convert your label 

- select your label -> edit -> text

<img width="650" height="553" alt="image" src="https://github.com/user-attachments/assets/71260a4a-a64e-4b84-b456-5258d7429e63" />

A and Y - locali layer
GND and power - metal1

Next we have to define the purpose of the port

<img width="847" height="748" alt="image" src="https://github.com/user-attachments/assets/8a469ce7-7823-464a-afd0-fa513a4a9f2c" />

Now we will extract the lef file

before we do that let's give it a name:

<img width="378" height="300" alt="image" src="https://github.com/user-attachments/assets/683f9d39-fac9-4cf9-8cd4-80877d0c2da2" />


<img width="810" height="282" alt="image" src="https://github.com/user-attachments/assets/c632b8fb-f244-4b0f-81a8-f6102180507c" />


<img width="435" height="479" alt="image" src="https://github.com/user-attachments/assets/9e00dddc-de6d-49d9-903f-a1bca39cf562" />

pin a is first because we set it to 0 earlier

### 57 - Introduction to timing libs and steps to include new cell in synthesis

<img width="970" height="345" alt="image" src="https://github.com/user-attachments/assets/4344453e-13f6-4459-8cf8-ae9924ed2378" />

we need to synthesize our custom cell and for that we need a library

<img width="973" height="486" alt="image" src="https://github.com/user-attachments/assets/bb5bb189-4335-4242-bcaf-89fed4424102" />

library for every cell

theres a fast, slow, and typical for different temperatures. it is the first line of each lib file:
- type / temperature / voltage

<img width="978" height="63" alt="image" src="https://github.com/user-attachments/assets/54d9a430-9f7e-4e81-815e-6b95db9b3e14" />

we need to modify config.tcl file

<img width="977" height="393" alt="image" src="https://github.com/user-attachments/assets/96298a51-d7e7-4017-98f6-49bce733d6a5" />

<img width="693" height="247" alt="image" src="https://github.com/user-attachments/assets/9e20faa2-868d-47b5-b325-248bff8c34da" />

<img width="883" height="396" alt="image" src="https://github.com/user-attachments/assets/1ec3f6b4-7109-4843-b9d9-e1e961fc511e" />

<img width="479" height="70" alt="image" src="https://github.com/user-attachments/assets/0642e7d0-6f9f-4510-88ab-20e77681e07e" />


then run_synthesis

<img width="321" height="80" alt="image" src="https://github.com/user-attachments/assets/218e9437-65b7-425c-b6c9-66fb5e4ac40b" />

### 58 - Introduction to delay tables

<img width="468" height="295" alt="image" src="https://github.com/user-attachments/assets/ae8adf48-3f2d-4888-bb4d-35f40bb49550" />

AND gate:
- when top is 1, clock will be propagated
- when the top pin is 0, the clock will be blocked
OR gate:
- when 0, propagated
- when 1, blocked

Advantage: There will be no switching or short circuit power that will be consumed by the clock tree during that period of time 

<img width="315" height="254" alt="image" src="https://github.com/user-attachments/assets/adcb818e-8dba-47fd-a33d-826ce8d03e2a" />

<img width="289" height="254" alt="image" src="https://github.com/user-attachments/assets/4ebade4c-7b20-46e6-9e71-85e2c06dafca" />

Will everything still work if we swtich it? Well, we have to look at the timing.

<img width="787" height="278" alt="image" src="https://github.com/user-attachments/assets/4095641f-df79-49b2-9f28-33410a62bc47" />

The load of the output will vary at each level. -> and that's why we use delay tables

There's a delay table for each cell and those became the timing model for the respective buffers

<img width="395" height="237" alt="image" src="https://github.com/user-attachments/assets/c207b664-831a-46f1-8b9b-0116b6013716" />


### 59 - Delay table usage Part 1

<img width="388" height="452" alt="image" src="https://github.com/user-attachments/assets/b6d73c91-3dd8-4ce7-a6a9-de3f293e95c3" />

We take the input slew and then look at the output load and wherever intersect is the delay

<img width="383" height="230" alt="image" src="https://github.com/user-attachments/assets/a88a6e2a-b781-4002-8cfa-40cd6993b6ab" />

pmos nmos size will correlate to the size of the number of the delay table

as you increase the size of the nmos pmos, you reduce resistance and by varying resistance you have varying rc(delay output).

<img width="343" height="460" alt="image" src="https://github.com/user-attachments/assets/423229da-8aae-4a55-be76-385e7b12a5a7" />

<img width="310" height="160" alt="image" src="https://github.com/user-attachments/assets/7eeee53d-6972-4042-b433-4a165cfa43cc" />

We're going to call A x9' because it lies between 50fF and 70fF so it lies between x9 and x10


### 60 - Delay table usage Part 2

<img width="382" height="229" alt="image" src="https://github.com/user-attachments/assets/de6f6640-e211-4ac8-b4d8-b7287ac589b5" />

<img width="262" height="240" alt="image" src="https://github.com/user-attachments/assets/09d38831-f7a7-4326-a60e-c1ce2a2574a6" />

<img width="462" height="237" alt="image" src="https://github.com/user-attachments/assets/0c7089d6-ca81-4e2c-8d40-4db77e6612b2" />

Skew is 0 because each node is driving the same load otherwise it will have different delays for each output

It is important to setup the two observations early on so that it doesn't propagate through your big circuit in the future.

### 61 - Lab steps to configure synthesis settings to fix slack and include vsdinv

<img width="315" height="65" alt="image" src="https://github.com/user-attachments/assets/8ad90972-f4e3-4a18-bcc0-5763d45e7051" />

wns is the maximum slack
tns is the total layer slack

let's make the synthesis more time driven

<img width="330" height="274" alt="image" src="https://github.com/user-attachments/assets/c71a56de-2a74-48de-9ac1-7ef77abbcfa5" />

<img width="318" height="82" alt="image" src="https://github.com/user-attachments/assets/d170b70d-4ee8-4de0-a0c7-3c84d102eab6" />

The slack should have been reduced and now we will run floorplan.

'''run_floorplan'''

<img width="991" height="285" alt="image" src="https://github.com/user-attachments/assets/a217a6de-8579-4af7-b5c4-612985b5a079" />

confirms placement can be run

'''run_placement'''

OVFL should decrease to 0

<img width="982" height="145" alt="image" src="https://github.com/user-attachments/assets/79758ca1-b4e0-4de7-ad6c-6326552670dc" />

<img width="950" height="78" alt="image" src="https://github.com/user-attachments/assets/53e1ec62-29b7-40ad-83ab-a9c09102763f" />

<img width="399" height="412" alt="image" src="https://github.com/user-attachments/assets/046781b2-4f83-496a-8aaf-30bb496b7cdf" />

then in terminal enter the command expand after selecting a cell

<img width="765" height="457" alt="image" src="https://github.com/user-attachments/assets/67fa5e88-4100-4241-adce-c771f3fb6275" />

## Timing analysis with ideal clocks using openSTA
### 62 - Setup timing analysis and introduction to flip-flop setup time
### 63 - Introduction to clock jitter and uncertainty
### 64 - Lab steps to configure OpenSTA for post-synth timing analysis
### 65 - Lab steps to optimize synthesis to reduce setup violations
### 66 - Lab steps to do basic timing ECO
## Clock tree synthesis TritonCTS and signal integrity
### 67 - Clock tree routing and buffering using H-Tree algorithm
### 68 - Crosstalk and clock net shielding
### 69 - Lab steps to run CTS using TritonCTS
### 70 - Lab steps to verify CTS runs
## Timing analysis with real clocks using openSTA
### 71 - Setup timing analysis using real clocks
### 72 - Hold timing analysis using real clocks
### 73 - Lab steps to analyze timing with real clocks using OpenSTA
### 74 - Lab steps to execute OpenSTA with right timinig libraries and CTS assignment
### 75 - Lab steps to observe impact of bigger CTS buffers on setup and hold timing
