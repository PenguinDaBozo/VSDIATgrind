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

<img width="679" height="450" alt="image" src="https://github.com/user-attachments/assets/2ef5667a-9234-43e9-ad30-940a35477f73" />

The green box is picorv32a. The yellow boxes are IO pads. The corners are the corner pads. The red pad is the power pad and the blue pad is the ground pad. 

The power is coming into the blue and red pads. From the pads, the power gets supplied to the ring. The places where there are x's are plces where the vias are connecting the pads to the ring. Similarly, the ground pad has an inner ring. 

Now the power can reach the ring from the pads, but we have to ensure that the power reaches from the pads to the chip. For that, we have the straps which are the blue and red lines in the green area. 

Power goes from pads to the ring and from ring to the straps. After the power reaches the picorv32a, we have to make sure it reaches the standard cells. 

There are the power and ground rails:

<img width="549" height="34" alt="image" src="https://github.com/user-attachments/assets/cd22290b-aa49-4ea3-9e16-103834bed7f9" />

<img width="513" height="71" alt="image" src="https://github.com/user-attachments/assets/489ea35b-118a-4a4f-88a7-9ea663d01adf" />

Similarly, for macro

<img width="134" height="208" alt="image" src="https://github.com/user-attachments/assets/22394673-7acf-46b4-99d6-e49becf62e50" />

<img width="700" height="201" alt="image" src="https://github.com/user-attachments/assets/401c9fa3-75be-471f-a347-0431b53fe790" />


The cts.def has changed into a pdn.def and this includes both cts and pdn

<img width="681" height="42" alt="image" src="https://github.com/user-attachments/assets/8b312883-6a4c-4645-aaa8-6ea03ac6b059" />


### 81 - Basics of global and detail routing and configure TritonRoute

The last thing is routing with **run_routing**

> *Note: from the video, which is a bit outdated and as such there is no routing strategy no more*

<img width="1161" height="550" alt="image" src="https://github.com/user- attachments/assets/34d827b4-b0de-462f-a243-eaf8345b32ab" />

> We will focus on routing strategy. There are 4 routing strategies. 
>
> For the purpose of this workshop we will use ROUTING_STRATEGY 0

<img width="133" height="28" alt="image" src="https://github.com/user-attachments/assets/7ce3bdf8-f5e1-4753-ad55-274b48430671" />

This will take a while... in the meantime



<img width="1029" height="457" alt="image" src="https://github.com/user-attachments/assets/412afa55-0ca3-4b7c-8335-a0f91f826c1d" />

Routing is divided into two steps (fast/global route and detail route)
- global route is done by fast route
- detail route is done by TritonRoute

In global route, the entire routing region is divided into grid cells (top left) . Then it is converted to a graph (top right). The fast route is followed by the detail route. The detail route should ensure that the segments and vias are in accordance to the global route. 

The four dots are four pins (bottom left). Detail route creates a routing guide after fast route. In detail route, we use some algorithm to find the best connectivity among these points, which is one of the strategy. 

Global route output is a set of routing guides for each of the nets. Detail route uses that global route and do connectivity between the points. 


## TritonRoute Features
### 82 - TritonRoute feature 1 - honors pre-processed route guides

TritonRoute is the engine used for Detail routing.

<img width="924" height="481" alt="image" src="https://github.com/user-attachments/assets/cc7fcc37-29e0-4bbb-a62c-262fcee8af27" />


1)
<img width="893" height="603" alt="image" src="https://github.com/user-attachments/assets/e4137614-091a-45be-afff-b1efdeada1e5" />

After the fast routing, we have a connectivity between A and B. Blue is metal 1 and pink is M2. The preferred direction for M1 is vertical but the initial route guide isn't, so we split the non-vertical route guide. Then some of the pieces that has an edge touching with a vertical routing guide will merge with the vertical routes. Then we bridge horizontally with metal 2. And finally we make the nonpreferred direction to the preferred direction.

The benefit of this is that the route guide will be in parallel with metal 2. This will form a parallel connection with capacitor and will result in greater signals. 

### 83 - TritonRoute Feature 2 & 3 - Inter-guide connectivity and intra - & inter-layer routing

2) 
<img width="882" height="479" alt="image" src="https://github.com/user-attachments/assets/44641079-f494-46e2-8584-abe842db1e14" />

Bullet 1 refers to earlier where when splitting occured, the pieces had to be merged back together. The purple box is the common non-vertical overlapped area and metal 1 and metal 2 is connected that way. The via is to be placed here. 

Bullet 2 refers to this image. The dots are pins of standard cells and needs to be overlapped by route guides. This is the reason why we wanted the routes to be vertical and horizontal. It will have the pins on the intersecting horizontal and vertical.

<img width="172" height="168" alt="image" src="https://github.com/user-attachments/assets/582979b3-fa89-4661-9171-420dcd68d130" />


3) 
<img width="843" height="474" alt="image" src="https://github.com/user-attachments/assets/5735ebab-ad32-4995-a93a-1b8f40a10d22" />

Each layer is divided into dashed lines. Metal 2 is vertical so the dashed lines are also vertical. These dashed lines is called panel. Each routing guide is assigned to one panel. When arrows are gray, routing is completed. 

Intra layer means within the layer, panel routing is parallel. Inter layer means between layers, panel routing is sequential. Via placement will only happen when upper routing placement.

Routing will first happen in parallel on the even index panels and then the odd index panels.  It is happening in parallel for a vertical layer. 


### 84 - TritonRoute Method to handle connectivity

<img width="899" height="473" alt="image" src="https://github.com/user-attachments/assets/e6a6d5c4-b003-4695-8a16-be2fdb0110d9" />

<img width="1021" height="613" alt="image" src="https://github.com/user-attachments/assets/4299fb22-6550-48f5-bc9e-b38f34282b3b" />

In figure a, the metals are in their preferred direction and the dashed lines are the routing tracks and the solid line is the routing which has been completed for metal 1. We connect 2 guides using vias that are placed in intersections of the solid and dashed lines. There are 5 points where vias can be placed and are referred to as access points. In figure b, the pins are connected. In figure c, it is connecting upper layer to bottom layer. There are 15 access points in C. Collection of access points are called access point cluster.

The goal of MILP is to find the opotimal solution to connect two APCs.

### 85 - Routing topology algorithm and final files list post-route

<img width="783" height="521" alt="image" src="https://github.com/user-attachments/assets/bcf7c33f-b85f-49de-8de9-1a4b23177768" />

This is the algorithm for the APCs. For each APC, find the common cost associated with APCs and then do a minimum spanning tree (MST) between the APCs and COSTs. Essentially, this algorithm is saying that I have to find the minimum and the most optimal point between two APCs. 

<img width="1002" height="452" alt="image" src="https://github.com/user-attachments/assets/e37ced43-edb8-47fd-8d45-83df0c35819a" />

TritonRoute does many iterations to optimize so that the violations are minialized. Higher version will result in lower violations but will take longer. 

<img width="986" height="590" alt="image" src="https://github.com/user-attachments/assets/e85fe180-5da2-410e-b834-b088c5f7e157" />

The violations decrease as iterations increase

<img width="800" height="594" alt="image" src="https://github.com/user-attachments/assets/9ae93ea4-fd80-4996-917e-74de0b245952" />

To find the errors, read **/openLANE_flow/designs/picorv32a/runs/RUN/reports/routing/74-tritonRoute.drc**

<img width="1196" height="45" alt="image" src="https://github.com/user-attachments/assets/2282fbd6-a05d-4b4d-ab00-50552cceee0a" />

**Parasitic extraction**

The extractor has not been included in OpenLANE so we will do extraction outside of openLANE. We need to go to work/tools/openlane/scripts to go to extractor.

<img width="867" height="164" alt="image" src="https://github.com/user-attachments/assets/ecf803ad-164a-4dcd-a8ca-02e74a06dc6f" />

<img width="866" height="147" alt="image" src="https://github.com/user-attachments/assets/80a55992-3ef2-408a-9749-c9d925fe7e0c" />

To generate the SPEF, you need to specify the lef and the def. This will create the SPEF file which will be in the same location as the def file. 

<img width="893" height="170" alt="image" src="https://github.com/user-attachments/assets/8e6dd44d-c780-4002-b662-2817f0385dea" />

We have to create a new db. You need to use the verilog file that was created preroute. 

<img width="867" height="210" alt="image" src="https://github.com/user-attachments/assets/d8e77166-a18d-4fcb-9035-df007745fa15" />

We will use this as the read_verilog netlist in the post sta analysis. Then we use the same sdc file. Then we need to read_spef for reading the parasetics. 


The last stage will be to extract the GDSII file ready for fabrication run_magic

This uses Magic to stream the GDSII file and creates picorv32a.gds. This GDSII file can then be read by Magic




