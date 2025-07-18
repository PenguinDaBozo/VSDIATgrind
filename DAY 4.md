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
### 57 - Introduction to timing libs and steps to include new cell in synthesis
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
