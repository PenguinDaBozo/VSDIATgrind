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

<img width="731" height="424" alt="image" src="https://github.com/user-attachments/assets/3d91c9f0-a009-4a58-a35d-ff02f0621558" />

This white line define the area boundry and there are 3 boxes between the white lines

<img width="731" height="424" alt="image" src="https://github.com/user-attachments/assets/0be6080c-5a0b-47d3-b660-0b7ecb18c281" />

Other guideline is it should be in the odd multiple of the x pinch

Same thing is required for the height of the standard cell

<img width="817" height="550" alt="image" src="https://github.com/user-attachments/assets/29c606d4-7974-44f3-b82f-3e09cdd7fe96" />

Port definition is required when you want to extract from lef file

So when you extract the lef file, these ports are the pins of the macro

How to convert your label 

- select your label -> edit -> text

<img width="847" height="505" alt="image" src="https://github.com/user-attachments/assets/caa0e683-8059-438b-97e0-d9458270e25e" />

A and Y - locali layer
GND and power - metal1

Next we have to define the purpose of the port

<img width="847" height="748" alt="image" src="https://github.com/user-attachments/assets/8a469ce7-7823-464a-afd0-fa513a4a9f2c" />

Now we will extract the lef file

before we do that let's give it a name:

<img width="919" height="489" alt="image" src="https://github.com/user-attachments/assets/0d596813-e9a2-499b-9cb3-7e65217439e7" />

well guess we can't anyways

<img width="937" height="500" alt="image" src="https://github.com/user-attachments/assets/788ec757-b52d-42b7-bd7d-97e5c86bf591" />

<img width="889" height="245" alt="image" src="https://github.com/user-attachments/assets/672ab0dc-3151-457d-9bad-2454ef8e33ef" />

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

<img width="883" height="396" alt="image" src="https://github.com/user-attachments/assets/1ec3f6b4-7109-4843-b9d9-e1e961fc511e" />

<img width="782" height="268" alt="image" src="https://github.com/user-attachments/assets/92857f79-0462-4073-a823-174d383b93f4" />

then run_synthesis

<img width="321" height="80" alt="image" src="https://github.com/user-attachments/assets/218e9437-65b7-425c-b6c9-66fb5e4ac40b" />






### 58 - Introduction to delay tables
### 59 - Delay table usage Part 1
### 60 - Delay table usage Part 2
### 61 - Lab steps to configure synthesis settings to fix slack and include vsdinv
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
