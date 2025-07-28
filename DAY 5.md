# Sky130 DAY 5 - Final steps for RTL2GDS using tritonRoute and openSTA
## Routing and design rule check (DRC)
### 76 - Introduction to Maze-Routing - Lee's Algorithm

Route - path that connects two cells

We are looking for the best routing, which is in a L shape and should not have zigzags

The algorithm creates a grid

<img width="518" height="429" alt="image" src="https://github.com/user-attachments/assets/62b24ae0-1708-4114-9811-c325cf935ddf" />

The algorithm has to find the best possible way to route S to T

It first labels the grids around it: adjacent is 1

<img width="521" height="434" alt="image" src="https://github.com/user-attachments/assets/ffbb95ec-f6fb-4351-bc90-878a4e392a97" />

It will label the next grids as 2

<img width="518" height="434" alt="image" src="https://github.com/user-attachments/assets/9d151fe5-a186-442a-bc80-320cc741af52" />

<img width="528" height="436" alt="image" src="https://github.com/user-attachments/assets/91020faa-f7ce-4216-8cc2-dc8e209a519b" />

### 77 - Lee's Algorithm conclusion

<img width="544" height="454" alt="image" src="https://github.com/user-attachments/assets/9b8fec0f-62c6-47e7-87ad-5909ec769fcb" />

We keep doing this until target. But there's the preplaced cells blocking the top so it doesnt label the grid above.

<img width="528" height="433" alt="image" src="https://github.com/user-attachments/assets/898d032b-5278-4472-960d-fe01c3eca892" />

<img width="526" height="432" alt="image" src="https://github.com/user-attachments/assets/1efc287c-639d-4bb3-b764-f7af17c2768c" />

<img width="513" height="440" alt="image" src="https://github.com/user-attachments/assets/9076bb90-17af-4077-aee3-dc2ea90c0eaa" />

The padding blocks it at the bottom

<img width="532" height="439" alt="image" src="https://github.com/user-attachments/assets/33204b8d-f250-463d-a0fa-6ac0a51160de" />

The algorithm picks a route to start and then goes by order until it hits the target cell. 

Options:

<img width="527" height="431" alt="image" src="https://github.com/user-attachments/assets/5a25b6fb-da7f-4b27-a6af-1726f7595c16" />

<img width="525" height="437" alt="image" src="https://github.com/user-attachments/assets/cc768a72-921d-4c7b-9425-99d05650f6b2" />

<img width="521" height="444" alt="image" src="https://github.com/user-attachments/assets/665757e5-fa40-41f6-8942-2b10cb85425a" />

The L-shape routing will be preferred over the more bends.

This can be time consuming and there are other algorithms that are similar but are more efficient

<img width="537" height="400" alt="image" src="https://github.com/user-attachments/assets/8349960b-f88f-4e69-9564-3d2c1cd98f5c" />

<img width="529" height="435" alt="image" src="https://github.com/user-attachments/assets/7c6a3108-f1db-4d10-86ef-585b3a7b20cf" />

Options: 

<img width="523" height="437" alt="image" src="https://github.com/user-attachments/assets/929ed896-33ee-4992-aecc-5b3ae0abc3ba" />

This is the most preferrable route because it has only one bend

<img width="529" height="436" alt="image" src="https://github.com/user-attachments/assets/758667e8-0e45-4471-acd3-6d1b999c7def" />

### 78 - Design Rule Check

<img width="810" height="439" alt="image" src="https://github.com/user-attachments/assets/092b0b9e-55e1-4418-bec8-4977a4cd58f9" />

Whenever we build two wires there should be a minimum distance between the two wires. 

3 Typical Design Rules for the below pair of wires

<img width="268" height="160" alt="image" src="https://github.com/user-attachments/assets/22101c60-7067-44c0-8b3e-093e6d95347c" />


<img width="249" height="173" alt="image" src="https://github.com/user-attachments/assets/99139d36-6616-49d3-980e-de8664e9bbba" />


It can't be more than this spacing

<img width="268" height="151" alt="image" src="https://github.com/user-attachments/assets/3a01b143-ba84-4788-8cc0-7a895f08c217" />

<img width="794" height="449" alt="image" src="https://github.com/user-attachments/assets/908f167b-e60b-4bc9-bd48-c6da1f3dbe61" />

<img width="290" height="215" alt="image" src="https://github.com/user-attachments/assets/c1efeb73-405b-4b0a-b4a9-28ccd436953c" />

How to solve:

<img width="232" height="218" alt="image" src="https://github.com/user-attachments/assets/a38b16aa-771d-48a3-b446-7724cda42d5c" />

<img width="222" height="231" alt="image" src="https://github.com/user-attachments/assets/64d735f5-d67a-4b12-8701-6dc16d37257e" />

We're just putting vias to fix the issue

<img width="301" height="276" alt="image" src="https://github.com/user-attachments/assets/66a34d3c-d464-400c-bd20-558a9a898b3b" />

<img width="276" height="249" alt="image" src="https://github.com/user-attachments/assets/cfe663f7-0778-4fd5-aafa-411c2245f332" />

## Power Distribution Network and routing
### 79 - Lab steps to build power distribution network

1) go to openlane directory

2) ./flow.tcl -interactive

3) package require openlane 0.9

4) prep -design picorv32a -tag [RUN_NAME]

5) echo $::env(CURRENT_DEF) and it should be the cts.def file

<img width="1033" height="638" alt="image" src="https://github.com/user-attachments/assets/b1fceda5-653c-429d-85df-4ae7f76ccb8b" />

6) gen_pdn

<img width="1177" height="484" alt="image" src="https://github.com/user-attachments/assets/5b7ab5b3-6425-4fa0-ad48-5d05b3a5813b" />

The PDN will read the lef and def file. Then it will create the grid and transfer the power. The standard cells are placed in rows so they need power and ground lines where standard cells are placed.

> If you want your cell to fit between the two rails, you have to set the  pitch to the height of the cell. 

Power goes through the straps and gets distributed to the stdcell rails. 

<img width="1190" height="633" alt="image" src="https://github.com/user-attachments/assets/c29d8680-ffa7-4b74-9554-8a3b0bfbd7f8" />


### 80 - Lab steps from power straps to std cell power
### 81 - Basics of global and detail routing and configure TritonRoute
## TritonRoute Features
### 82 - TritonRoute feature 1 - honors pre-processed route guides
### 83 - TritonRoute Feature 2 & 3 - Inter-guide connectivity adn intra - & inter-layer routing
### 84 - TritonRoute Method to handle connectivity
### 85 - Routing topology algorithm and final files list post-route
