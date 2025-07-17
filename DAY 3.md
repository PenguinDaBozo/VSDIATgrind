# Sky130 DAY 3 - Design library cell using Magic Layout and ngspice characterization

## Labs for CMOS inverter ngspice simulations

### 31 - IO placer revision

We can use openLANE to change the layout of the IO. 

<img width="978" height="69" alt="image" src="https://github.com/user-attachments/assets/2480c54d-9562-4a70-ad54-44e2db2dbb31" />

<img width="519" height="487" alt="image" src="https://github.com/user-attachments/assets/943d8f3b-dadd-49a9-ad2c-6b9435667f43" />

This is our core currently.

To modify the floorplan, we can go into floorplan.tcl file and pick the command we want to change. 

<img width="429" height="282" alt="image" src="https://github.com/user-attachments/assets/b63c66b2-4d93-4d5e-be20-29f823a10dd2" />

<img width="244" height="58" alt="image" src="https://github.com/user-attachments/assets/053315ab-67d0-42ec-a744-421e5841cc64" />

<img width="913" height="146" alt="image" src="https://github.com/user-attachments/assets/48de2060-ccaf-4ad5-a14e-c70144cd0551" />

This is our core after we changed the IO pins

<img width="510" height="495" alt="image" src="https://github.com/user-attachments/assets/f2bb3cf9-8a98-4dc3-8574-3c898ee35dbf" />


### 32 - SPICE deck creation for CMOS inverter

Before entering the simulations, 

1) we have to create a SPICE deck, which is a netlist.

<img width="274" height="313" alt="image" src="https://github.com/user-attachments/assets/7b65c65b-9431-433c-83b0-be731f651963" />

2) define the component values

<img width="292" height="329" alt="image" src="https://github.com/user-attachments/assets/db7cfa28-2440-42e5-92d7-279c1a1ea8b3" />

*Ideally PMOS has to be 2 or 3 times bigger than NMOS.*

<img width="364" height="325" alt="image" src="https://github.com/user-attachments/assets/e4939f52-0295-4f48-b49d-c0e8389c012e" />

*Voltage is 10x the channel size. So 0.25x10 = 2.5*

3) Identify the nodes

<img width="486" height="374" alt="image" src="https://github.com/user-attachments/assets/f570c42e-b112-4edf-baa3-3d44f3458f07" />

4) Name nodes

<img width="368" height="331" alt="image" src="https://github.com/user-attachments/assets/6e8a6974-27dd-4365-95e5-f6d49979ebee" />

5) Now we can create a SPICE deck

<img width="855" height="357" alt="image" src="https://github.com/user-attachments/assets/c5dc368d-e791-4524-b1b3-404c7342b2da" />

### 33 - SPICE simulation lab for CMOS inverter

<img width="861" height="354" alt="image" src="https://github.com/user-attachments/assets/ab881870-7d68-43a9-ab2b-e5c9123e0656" />

<img width="867" height="363" alt="image" src="https://github.com/user-attachments/assets/21440c17-743b-49a5-871e-a979a442c235" />

6) Next we can use simulation commands

<img width="340" height="78" alt="image" src="https://github.com/user-attachments/assets/816560d7-5500-4782-9aea-1ff66e0a6d2e" />

*sweeping the Vin from 0-2.5 in steps of 0.05 and measuring output waveform*

7) Finally we describe model file

<img width="418" height="328" alt="image" src="https://github.com/user-attachments/assets/2ea675b5-9d8c-4b12-b746-0d1e0138fab1" />

Let's move to SPICE simulation

<img width="647" height="88" alt="image" src="https://github.com/user-attachments/assets/2cb2bd55-a015-4ad9-b9d7-c612fed36abb" />


<img width="546" height="219" alt="image" src="https://github.com/user-attachments/assets/fba83bca-b7c9-468d-a07b-808b89b01e81" />

<img width="552" height="223" alt="image" src="https://github.com/user-attachments/assets/efd18403-c6bb-4440-b093-12caf4c1501f" />

<img width="549" height="42" alt="image" src="https://github.com/user-attachments/assets/4d80d524-81b0-4070-91f5-dc832fa40a67" />

<img width="549" height="204" alt="image" src="https://github.com/user-attachments/assets/b639b168-510c-4d42-896b-e56a52bbeca3" />

<img width="549" height="204" alt="image" src="https://github.com/user-attachments/assets/b5682446-fecb-4156-967c-ef8e24457613" />

<img width="547" height="199" alt="image" src="https://github.com/user-attachments/assets/c5d6f5ed-c12c-43a6-b431-e6898545caa8" />

<img width="513" height="388" alt="image" src="https://github.com/user-attachments/assets/477f2dfa-4c4c-4c57-807e-9cbe7d42c3af" />

<img width="715" height="95" alt="image" src="https://github.com/user-attachments/assets/8c801da6-5397-40cc-a7d5-5e3f10b36798" />

<img width="526" height="412" alt="image" src="https://github.com/user-attachments/assets/f9a6753e-0588-4037-b822-001c154599cd" />

### 34 - Swtiching Threshold Vm

<img width="846" height="416" alt="image" src="https://github.com/user-attachments/assets/220000f2-c287-478d-bcff-162bcd95cc05" />

The shape is the same and this tells us the CMOS is very robust and the fall and rise is maintained.

Static behavior Evaluation: CMOS inverter Robustness
1. Switching Threshold, Vm, the point where Vin = Vout

<img width="830" height="328" alt="image" src="https://github.com/user-attachments/assets/a53ed522-4b41-4b4b-a885-64cd370c1848" />

<img width="615" height="287" alt="image" src="https://github.com/user-attachments/assets/dcb1923a-1858-4eca-af6d-5a8fdce435c4" />

<img width="645" height="272" alt="image" src="https://github.com/user-attachments/assets/17ddd481-5d4a-4ceb-b812-9a0c857df35f" />

### 35 - Static and dynamic simulation of CMOS inverter

Everything will remain the same and input will have pulse and simulation will have tran

<img width="774" height="365" alt="image" src="https://github.com/user-attachments/assets/02779405-a4e7-4591-9bde-229b83b12542" />

<img width="544" height="434" alt="image" src="https://github.com/user-attachments/assets/68446150-ec1d-4632-a946-9ad1e99ab14c" />

Take the two points: 
<img width="658" height="450" alt="image" src="https://github.com/user-attachments/assets/b4fe3ed6-feba-4bf0-b9a2-0b6feb8e0897" />

<img width="881" height="370" alt="image" src="https://github.com/user-attachments/assets/4406f11d-82ec-4dab-9d96-36005bc02429" />

### 36 - Lab steps to git clone vsdstdcelldesign

<img width="699" height="400" alt="image" src="https://github.com/user-attachments/assets/b11612bb-1ce5-42eb-907d-1895887a8824" />

<img width="455" height="218" alt="image" src="https://github.com/user-attachments/assets/6e09de93-ad9c-43ed-b51b-1dd98d31e8a4" />

<img width="985" height="182" alt="image" src="https://github.com/user-attachments/assets/7fcc0226-c99d-4302-bcbc-80391f8a1a90" />

Before we open the mag file, we need to have the tech file to open this

<img width="960" height="239" alt="image" src="https://github.com/user-attachments/assets/7c6abc48-f326-4821-be7f-da878d0c91a0" />

<img width="973" height="40" alt="image" src="https://github.com/user-attachments/assets/16f2fff0-9c05-4c6e-8c97-80106ff1631c" />

Verify its been copied

<img width="882" height="181" alt="image" src="https://github.com/user-attachments/assets/4aa9081e-6449-41d3-bc20-20ce78450b25" />

<img width="988" height="209" alt="image" src="https://github.com/user-attachments/assets/4bbcc930-f99f-454c-a75a-2dae7e9aa969" />

<img width="969" height="594" alt="image" src="https://github.com/user-attachments/assets/99b42829-335c-47c0-a0c2-64b5f993ca98" />

## Inception of Layout - CMOS fabrication process

### 37 - Create Active regions

16-mask CMOS process

1) Selecting a substrate

<img width="741" height="214" alt="image" src="https://github.com/user-attachments/assets/b37d3f9f-04fc-417c-a76b-5e4a8f9d6a0f" />

2) Creating active region for transistors
- This is the region where you see your PMOS and NMOS

We are going to create some pockets and create isolation between pockets. 

<img width="757" height="347" alt="image" src="https://github.com/user-attachments/assets/3ee237e3-189e-4a9a-9b34-3c3a6f70edcf" />

<img width="745" height="350" alt="image" src="https://github.com/user-attachments/assets/aa193eee-5e45-4fb1-b22a-2b867e9d37d1" />

Photoresist is a film on which we are going to do some process to clearly define region. Any layout is converted to Mask. 

<img width="848" height="402" alt="image" src="https://github.com/user-attachments/assets/07f6ea5f-a394-4817-847d-8e125edae288" />

There will be no chemical reaction under the places where the mask (red) is. Then we wash out the solution not under the mask.

<img width="601" height="359" alt="image" src="https://github.com/user-attachments/assets/425be430-4ef8-4d75-8b76-013d10feb50a" />

Remove mask

<img width="607" height="323" alt="image" src="https://github.com/user-attachments/assets/fb65e1aa-b0e3-4eb2-9924-a430e438240f" />

<img width="713" height="300" alt="image" src="https://github.com/user-attachments/assets/e5ce00f6-a313-49be-bbd6-19b8e3a8b6cf" />

Next is to remove the photoresist layer because the silicon itself will act as a good protection layer to grow oxide area.

<img width="591" height="229" alt="image" src="https://github.com/user-attachments/assets/2a06899e-002f-4be4-8eed-6cab78b2c5a6" />

When we put it in oxidation furnace, only the areas not under a silicion will grow. 

<img width="737" height="311" alt="image" src="https://github.com/user-attachments/assets/e39abba1-4c71-4625-8a45-38ad2f5fbfc5" />

This process is called LOCOS (Local Oxidation of Silicon)

<img width="729" height="372" alt="image" src="https://github.com/user-attachments/assets/2e97204b-0934-4a11-8569-d8b27bbf0e22" />

The next step is to strip the silicon using hot phosphoric acid

<img width="717" height="294" alt="image" src="https://github.com/user-attachments/assets/63751635-fba6-49c2-ab4f-6d3a6fa51094" />

### 38 - Formation of N-well and P-well

3) N-Well and P-Well formation

We need to protect one area while we fabricate other

Cross section

<img width="674" height="354" alt="image" src="https://github.com/user-attachments/assets/a2c74a56-c959-4383-835c-9baccae8b606" />

<img width="624" height="380" alt="image" src="https://github.com/user-attachments/assets/10fef629-f473-445f-afdb-c5b4e76381cc" />

Finally, you have to create a P-Well over here which is done using boron and diffused into it using a prcoess called ion implantation

<img width="785" height="404" alt="image" src="https://github.com/user-attachments/assets/87948f7f-d96a-4000-b58f-01bd1250811c" />

The same thing for N-well happens but we use phosphorous instead

<img width="622" height="398" alt="image" src="https://github.com/user-attachments/assets/6d715d93-eedd-462c-824e-248eee44b637" />

<img width="615" height="323" alt="image" src="https://github.com/user-attachments/assets/713e7215-1ead-4cf5-8426-7bb65732c812" />

Next we take this substrate into a high temperature furnace and that will cause drive-in diffusion

<img width="684" height="411" alt="image" src="https://github.com/user-attachments/assets/2b15aa2b-eb54-4c49-bc29-180e686ab1aa" />

### 39 - Formation of gate terminal

4) Formation of "gate"

### 40 - Lightly doped drain(LDD) formation
### 41 - Source - drain formation
### 42 - Local interconnect formation
### 43 - Higher level metal formation
### 44 - Lab introduction to Sky130 basic layers layout and LEF using inverter
### 45 - Lab steps to create std cell layout and extract spice netlist
## Sky130 Tech File
### 46 - Lab steps to create final SPICE deck using Sky130 tech
### 47 - Lab steps to characterize inverter using sky130 model files
### 48 - Lab introduction to Magic tool options and DRC rules
### 49 - Lab introduction to Sky130 pdk's and steps to download labs
### 50 - Lab introduction to Magic and steps to load Sky130 tech-rules
### 51 - Lab exercise to fix poly.9 error in Sky130 tech-file
### 52 - Lab exercise to implement poly resistor spacing to diff and tap
### 53 - Lab challenge exercise to describe DRC error as geometrical construct
### 54 - Lab challenge to find missing or incorrect rules and fix them
