# Sky130 DAY 4 - Pre-layout timing analysis and importance of good clock tree
## Timing modelling using delay tables
### 55 - Lab steps to convert grid info to track info

<img width="765" height="536" alt="image" src="https://github.com/user-attachments/assets/e92c6d60-f378-44b1-8bfb-26654f460845" />


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

<img width="759" height="539" alt="image" src="https://github.com/user-attachments/assets/5423b4c2-c10a-4e39-897b-2797c4fd9346" />

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

<img width="956" height="40" alt="image" src="https://github.com/user-attachments/assets/ed270ea3-37a2-452c-b4f1-5330c56ee2f8" />

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

<img width="950" height="78" alt="image" src="https://github.com/user-attachments/assets/53e1ec62-29b7-40ad-83ab-a9c09102763f" />

<img width="472" height="417" alt="image" src="https://github.com/user-attachments/assets/85272a85-654a-4773-8280-79586a4d591b" />

then in terminal enter the command expand after selecting a cell

<img width="764" height="512" alt="image" src="https://github.com/user-attachments/assets/49c39940-deae-441d-9ef3-70b72601de05" />

## Timing analysis with ideal clocks using openSTA
### 62 - Setup timing analysis and introduction to flip-flop setup time

<img width="192" height="132" alt="image" src="https://github.com/user-attachments/assets/62ac4e3a-e9cf-4732-986e-f88094ce45b3" />

<img width="737" height="492" alt="image" src="https://github.com/user-attachments/assets/57e9f392-c2f5-4989-8b3c-26bf07ddae65" />

Send the edge to the launch flop and on the t it reaches capture flop

Assume the delay has theta which is less than T

<img width="174" height="282" alt="image" src="https://github.com/user-attachments/assets/56b8e530-fd71-4c7f-9f58-04c8aa3aadda" />

<img width="514" height="277" alt="image" src="https://github.com/user-attachments/assets/08defefc-33ef-4cf6-8e23-96d91eda2107" />

At logic 1, it doesn't go back to mux 1 and goes to mux 2

<img width="820" height="518" alt="image" src="https://github.com/user-attachments/assets/7aebd212-bcec-42b9-b251-f92ec3d2b94b" />

There is some amount of time s, setup time, the amount of time needed to set up capture flop

| theta < (T-S)

<img width="918" height="525" alt="image" src="https://github.com/user-attachments/assets/81fb3c03-4d64-4fa5-b554-eb4bf93be729" />

### 63 - Introduction to clock jitter and uncertainty

There is a clock source expected to send clock but it has variations so it might notbe able to produce clock signal exactly at 0 or T

<img width="920" height="470" alt="image" src="https://github.com/user-attachments/assets/f0acff1b-54b2-4c88-bbff-e6e5d9ab0bbd" />

Jitter - temporary variation of clock period

<img width="875" height="484" alt="image" src="https://github.com/user-attachments/assets/4c0f7b5c-f524-46e7-924a-b3154f6dbd6b" />

It sends a clock signal at the edges near 0 or T so we have to model

<img width="674" height="230" alt="image" src="https://github.com/user-attachments/assets/f87990ac-de9c-479e-909f-927c5a33305b" />

<img width="961" height="478" alt="image" src="https://github.com/user-attachments/assets/d523ffc2-396f-41f7-99c0-05e93d374d45" />

<img width="912" height="504" alt="image" src="https://github.com/user-attachments/assets/d4a5b234-8a2e-46ba-a1d2-4123ec3fbe51" />

<img width="912" height="441" alt="image" src="https://github.com/user-attachments/assets/b545186c-ce91-4027-9aa7-bbd47825cb85" />

*Combinational delays*

### 64 - Lab steps to configure OpenSTA for post-synth timing analysis

We need to ensure slack is reduced. If there is a timing violation, we carry out the analysis in a separate tool for synthesis prime time. 



<img width="1405" height="219" alt="image" src="https://github.com/user-attachments/assets/ad1b158f-3058-4d29-be80-736098fb40eb" />

This is where the libraries come into play

You will see a new verilog file here

<img width="1399" height="587" alt="image" src="https://github.com/user-attachments/assets/d7fcc6a3-09fe-433b-8d62-367efda10b4c" />

<img width="1250" height="79" alt="image" src="https://github.com/user-attachments/assets/c36a91ff-018d-4af9-bb79-8ba2773f25ff" />

<img width="1023" height="116" alt="image" src="https://github.com/user-attachments/assets/3f4b23f6-415a-4101-bc63-8783092c04dd" />

<img width="1007" height="576" alt="image" src="https://github.com/user-attachments/assets/e95012ee-0f27-48e6-a500-1f192c87971d" />

<img width="568" height="40" alt="image" src="https://github.com/user-attachments/assets/00991558-91fb-4033-812e-962f34afb8d6" />

We need the capacitance load

<img width="766" height="243" alt="image" src="https://github.com/user-attachments/assets/e2d7aa4b-55d9-4158-a9fe-45e99ddc0820" />

And then put the capacitance load next to SYNTH_CAP_LOAD

Where he got the commands from
<img width="931" height="53" alt="image" src="https://github.com/user-attachments/assets/a065ae94-7625-41d6-b158-2f03ed36be1b" />

<img width="1027" height="509" alt="image" src="https://github.com/user-attachments/assets/3c7ed99a-314d-46ee-b3cc-669501bd7e09" />

<img width="1244" height="367" alt="image" src="https://github.com/user-attachments/assets/715e1e04-dfac-4af4-bfa2-1d50d5fafe56" />

<img width="825" height="23" alt="image" src="https://github.com/user-attachments/assets/ca4ac13e-c9a0-41b0-adb9-5d7da5db5241" />

<img width="677" height="369" alt="image" src="https://github.com/user-attachments/assets/e36fbc9e-a4b0-4dd5-9b17-bff0355f003d" />

### 65 - Lab steps to optimize synthesis to reduce setup violations

Look for places where the delays are high, which are contributed to fanout.

<img width="1328" height="263" alt="image" src="https://github.com/user-attachments/assets/791099a7-2142-45a7-8210-d471d54cb724" />

<img width="343" height="90" alt="image" src="https://github.com/user-attachments/assets/d68f0956-fc2c-4b37-aed0-afc892b3adcb" />

<img width="619" height="186" alt="image" src="https://github.com/user-attachments/assets/8847d4d3-d523-4cdf-8428-fc3dc6f3f669" />

<img width="440" height="86" alt="image" src="https://github.com/user-attachments/assets/83bafcd6-3ff5-419f-b72f-8b2e44f12424" />

<img width="666" height="39" alt="image" src="https://github.com/user-attachments/assets/41f5496a-66c6-415c-9215-5a8e3af3df37" />

expands the report to more decimal points

### 66 - Lab steps to do basic timing ECO

try to get slack as closet to 0 as possible by altering the buffers and stuff

## Clock tree synthesis TritonCTS and signal integrity
### 67 - Clock tree routing and buffering using H-Tree algorithm

<img width="1048" height="535" alt="image" src="https://github.com/user-attachments/assets/cf0e5ad7-03fc-45f5-954c-6b51e43d3dec" />

<img width="864" height="452" alt="image" src="https://github.com/user-attachments/assets/86a35c5f-c593-47ef-a7e3-f10576f8cdd9" />

<img width="1015" height="530" alt="image" src="https://github.com/user-attachments/assets/389b1bfe-aecb-4150-a1d2-e4c1b26c2ae3" />

It's a bad tree because t1 and t2 are not very close to each other

we want skew as close to 0 as possible to reduce latency

Midpoint strategy

<img width="1031" height="577" alt="image" src="https://github.com/user-attachments/assets/b03a4df0-3147-4af0-9217-33117957440b" />

<img width="1025" height="546" alt="image" src="https://github.com/user-attachments/assets/d28608fc-1363-4550-a9bb-193e86b42f9d" />

Now we have to do buffering because of distance which causes resistance and voltage drops

<img width="551" height="217" alt="image" src="https://github.com/user-attachments/assets/b2be3260-a46d-4e7d-8364-a81c5e431110" />

<img width="742" height="519" alt="image" src="https://github.com/user-attachments/assets/f688cacc-7109-4134-bb8e-2e04fc2a0c51" />

### 68 - Crosstalk and clock net shielding

We have to shield the clock net to protect from outside so it doesnt couple 

<img width="715" height="506" alt="image" src="https://github.com/user-attachments/assets/285c1fab-935f-4471-b17a-8a0aa7710a4f" />

If it does couple then there are problems

1) glitch - any activity happening at a will happen at v, which causes a dip in the voltage

<img width="556" height="306" alt="image" src="https://github.com/user-attachments/assets/26665d52-f820-4d7d-b9b7-766aa10893dd" />

<img width="581" height="373" alt="image" src="https://github.com/user-attachments/assets/0567e010-e322-450a-b3bb-bcbe5f1ba24e" />

By shielding, we break the coupling capacitor link

2) Crosstalk

<img width="973" height="542" alt="image" src="https://github.com/user-attachments/assets/ccc082ff-2740-4429-8b9c-8048a3eb3e5e" />

As it tries to go from 0 to 1, theres a drop and this will cause a bumpy delay

### 69 - Lab steps to run CTS using TritonCTS
### 70 - Lab steps to verify CTS runs


## Timing analysis with real clocks using openSTA
### 71 - Setup timing analysis using real clocks

<img width="856" height="491" alt="image" src="https://github.com/user-attachments/assets/0e9f1b50-97d7-4227-ad94-d40abcfef1af" />

<img width="841" height="474" alt="image" src="https://github.com/user-attachments/assets/807c2ccb-67c9-4345-8e3c-87a71add8af8" />

<img width="885" height="482" alt="image" src="https://github.com/user-attachments/assets/3af92145-fce5-4f89-8af3-68dd4a23c453" />

delta1 = 1 + 2
delta2 = 3 + 4 - from 1 to capture flop

<img width="874" height="548" alt="image" src="https://github.com/user-attachments/assets/06d999ed-ad50-40cf-97cf-bb84d2b89d71" />

<img width="154" height="114" alt="image" src="https://github.com/user-attachments/assets/e5735bbe-1bc5-4a9a-97e0-3c096ea33309" />

<img width="211" height="65" alt="image" src="https://github.com/user-attachments/assets/7f4351ee-e399-42bf-a28c-fb98a41de0d3" />

<img width="527" height="121" alt="image" src="https://github.com/user-attachments/assets/56c87bf8-9611-45ac-9795-b91ea7a326d4" />

<img width="571" height="119" alt="image" src="https://github.com/user-attachments/assets/5c46bd41-5c7c-4506-9b2c-cf6041e7c716" />

It's ready tfor 1GHz.

left is data arrival time and the right is data required time

data required time - data arrival time = slack (should be +ve or 0)

**Hold analysis**

<img width="878" height="476" alt="image" src="https://github.com/user-attachments/assets/63cbcad5-3389-4e54-a6b9-4391db6d6282" />

Hold refers to second mux 

<img width="818" height="337" alt="image" src="https://github.com/user-attachments/assets/2b6c188f-a68b-433b-bb1d-f2c2261b8a6f" />

The time required to send this capture delay out is mux2. Capture flop doesnt expect any data to arrive while it is sending data out and sends message to hold data until it sends out data.

<img width="875" height="532" alt="image" src="https://github.com/user-attachments/assets/6084808c-b65d-4639-971e-4270b56e16af" />

<img width="230" height="78" alt="image" src="https://github.com/user-attachments/assets/9bb32849-24a6-4e45-ac4b-7a88dcba9ec3" />

### 72 - Hold timing analysis using real clocks

<img width="165" height="173" alt="image" src="https://github.com/user-attachments/assets/75cc6df9-1ab4-4362-85e6-7609dd0cd195" />

<img width="270" height="73" alt="image" src="https://github.com/user-attachments/assets/aa2a74b5-149b-4d42-8abb-1a0fef045ae4" />

Need to mention a uncertainty value (U) so the capture flop holds data for hold time plus some uncertainty value

<img width="403" height="92" alt="image" src="https://github.com/user-attachments/assets/15134541-d7bb-445d-9fde-ef8a297ba8ac" />

<img width="259" height="154" alt="image" src="https://github.com/user-attachments/assets/4e9c1e2f-64fd-42f4-b463-8b32eff997b6" />

Slack should be +ve or '0'

If it is negative it means the delay is very fast and we need to slow that down

Single Clock

<img width="1035" height="594" alt="image" src="https://github.com/user-attachments/assets/71d28846-d385-4fb9-a985-c62ee973b793" />

<img width="1012" height="589" alt="image" src="https://github.com/user-attachments/assets/c639b736-4477-43a0-b5f4-839acd3ee52c" />


delta2 is the basically delta 1 but flipped

<img width="1031" height="623" alt="image" src="https://github.com/user-attachments/assets/c7e55cab-f9f1-462c-a3de-63f68eef4d1a" />

### 73 - Lab steps to analyze timing with real clocks using OpenSTA
### 74 - Lab steps to execute OpenSTA with right timing libraries and CTS assignment
### 75 - Lab steps to observe impact of bigger CTS buffers on setup and hold timing
