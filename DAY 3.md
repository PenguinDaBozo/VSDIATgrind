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

<img width="899" height="471" alt="image" src="https://github.com/user-attachments/assets/e01c5bfe-7442-49c8-a18a-42ba5f1942bb" />

Threshold voltage controls function 

<img width="747" height="394" alt="image" src="https://github.com/user-attachments/assets/f8e4aff5-3f99-4f28-a97e-a260ea0eee5c" />

<img width="677" height="401" alt="image" src="https://github.com/user-attachments/assets/c030a8c2-eaa2-45d4-997e-0e94af019d47" />

Area exposed to boron with low energy 

<img width="635" height="347" alt="image" src="https://github.com/user-attachments/assets/f98f6f7c-5756-42d3-936b-1a32f57b4752" />

<img width="604" height="399" alt="image" src="https://github.com/user-attachments/assets/bc2262f8-da3c-4e07-b324-ac056ac68f44" />

<img width="789" height="329" alt="image" src="https://github.com/user-attachments/assets/9b71f612-6564-4409-9e33-acd5aebdc2d2" />

<img width="783" height="352" alt="image" src="https://github.com/user-attachments/assets/43f84cff-f5e3-4e05-980d-4194e84c7d45" />

Then we put a silicon layer

<img width="760" height="342" alt="image" src="https://github.com/user-attachments/assets/ccc98bdf-1cce-472e-92c1-9eb67e65e212" />

<img width="727" height="399" alt="image" src="https://github.com/user-attachments/assets/09e13871-fc0b-4840-a184-1ca0793bd62c" />

<img width="610" height="395" alt="image" src="https://github.com/user-attachments/assets/aae4b59e-4b7d-45d6-80e2-9eab58ea631a" />

<img width="629" height="340" alt="image" src="https://github.com/user-attachments/assets/8807337e-59ee-449d-a519-1e6d93069034" />

<img width="629" height="289" alt="image" src="https://github.com/user-attachments/assets/306ac059-945c-47be-aa23-951e1a885d78" />

### 40 - Lightly doped drain(LDD) formation
5) Lightly doped drain(LDD) formation

<img width="730" height="294" alt="image" src="https://github.com/user-attachments/assets/b3af52ae-1adf-4694-8cbe-b501f99aca7e" />

Why do we need this P- and N-?
- hot electron effect: when device size reduces, power supply not reduced so electric field increases
  - causes high energy carriers to break Si-Si bonds
  - energy might be so high that it breaks the Si conduction band and enters the oxide layer
- short channel effect: when device size reduces, drain field penetrates channel so gate hard to control

<img width="728" height="376" alt="image" src="https://github.com/user-attachments/assets/e3f13662-0270-44e4-828c-65b4beec20ba" />

<img width="609" height="397" alt="image" src="https://github.com/user-attachments/assets/a18f8f25-3a00-49c1-aa0c-6c46968ca606" />

Use n type impurity to implant to create n doped

<img width="685" height="351" alt="image" src="https://github.com/user-attachments/assets/26454be4-eac7-43a5-9572-fbd884786f58" />

<img width="633" height="389" alt="image" src="https://github.com/user-attachments/assets/e0ca3fa6-0449-4e14-91b6-2e51d923887a" />

Use p type impurity to create p doped

<img width="752" height="343" alt="image" src="https://github.com/user-attachments/assets/46ef65d3-6b2f-4f20-8cb1-4a8534f20bc4" />

<img width="752" height="338" alt="image" src="https://github.com/user-attachments/assets/38f5baeb-8a33-4955-ad8e-b69b948e962b" />

helps prevent extra stuff from being etched away

<img width="752" height="352" alt="image" src="https://github.com/user-attachments/assets/dd87e668-b86a-491f-a66c-b8f320f3d85a" />

these side-wall spacers help to maintain the implants

### 41 - Source - drain formation
6) Source and drain formation

<img width="753" height="363" alt="image" src="https://github.com/user-attachments/assets/5ff9cd5b-6770-420d-baa1-be8f60784da3" />

<img width="738" height="358" alt="image" src="https://github.com/user-attachments/assets/52eebaff-00a0-43e9-92a2-6880a15b2175" />

<img width="683" height="382" alt="image" src="https://github.com/user-attachments/assets/97a6d2e0-e605-4516-941c-c7b74d9efe56" />

Now there's a N+ implant

<img width="617" height="391" alt="image" src="https://github.com/user-attachments/assets/059fdfa5-f40c-4d66-9689-2157db1ee2dc" />

Same thing for other side

<img width="657" height="366" alt="image" src="https://github.com/user-attachments/assets/9224f377-6df2-4fe2-badd-ebea3dbd2f49" />

<img width="703" height="378" alt="image" src="https://github.com/user-attachments/assets/6a588531-1c0b-44fe-8e5c-534c8cbabcfc" />

<img width="603" height="392" alt="image" src="https://github.com/user-attachments/assets/cd1d98b9-a9a8-4b5f-9896-0a411f02a75e" />

<img width="675" height="400" alt="image" src="https://github.com/user-attachments/assets/86b08911-cd55-4e88-9cc5-060c53dc695a" />

High temperature annealing will increase the P+ and N+

<img width="668" height="395" alt="image" src="https://github.com/user-attachments/assets/7aef77ea-dc0e-4dc3-8410-7b03b4212843" />

### 42 - Local interconnect formation

7) Steps to form contacts and interconnects(local)

<img width="767" height="363" alt="image" src="https://github.com/user-attachments/assets/5b44d60a-9368-4e3a-bb40-2aabbb8f3263" />

<img width="737" height="360" alt="image" src="https://github.com/user-attachments/assets/50543ff5-59a9-4c49-b6c7-4333bf4f21bb" />

Now we shall deposit titanium on wafer surface using sputtering, which is the particles of a metal gets depposited out into the substrate after being exposed to another element

<img width="676" height="316" alt="image" src="https://github.com/user-attachments/assets/2e01e14b-a551-4110-bf7c-1678c91dbf75" />

<img width="763" height="376" alt="image" src="https://github.com/user-attachments/assets/b1362a00-fa07-4b73-86d9-9d396f0884ea" />

<img width="732" height="367" alt="image" src="https://github.com/user-attachments/assets/4eb1f278-0788-449b-b824-cad0bd1931fe" />

<img width="594" height="405" alt="image" src="https://github.com/user-attachments/assets/d5e8a09b-9129-4a54-8114-8a01f626a689" />

<img width="623" height="342" alt="image" src="https://github.com/user-attachments/assets/aceb3c5c-7d8a-4293-ac43-ca568d8664af" />

<img width="707" height="385" alt="image" src="https://github.com/user-attachments/assets/b609e7df-3d45-4664-b412-a6e00a490d83" />

<img width="588" height="384" alt="image" src="https://github.com/user-attachments/assets/f37369e6-d3d4-45af-a188-8cd795632a98" />

### 43 - Higher level metal formation
8) Higher level metal formation

<img width="613" height="292" alt="image" src="https://github.com/user-attachments/assets/ebc8185a-0f08-49cd-bc9e-867fae627dbc" />

You can't use this for photography so we have to add some extra stuff

<img width="743" height="398" alt="image" src="https://github.com/user-attachments/assets/e519ff28-eef3-4ed2-a7fa-959a23451594" />

Phosphorous acts as a barrier and boron will reduce temperature of surface. Next we polish

<img width="733" height="383" alt="image" src="https://github.com/user-attachments/assets/e7fc256e-5cea-4248-808e-6350c7d9f10d" />

<img width="629" height="333" alt="image" src="https://github.com/user-attachments/assets/524abeb4-a8f8-471e-acdc-6fc19983e495" />

<img width="627" height="438" alt="image" src="https://github.com/user-attachments/assets/50b7c262-60c0-4099-92aa-e2e7d5af965f" />

<img width="675" height="393" alt="image" src="https://github.com/user-attachments/assets/87b79344-057a-4de8-93ef-d028ce4cc901" />

<img width="613" height="311" alt="image" src="https://github.com/user-attachments/assets/9cb0b000-6c3f-4322-946b-cf9196276f6e" />

<img width="653" height="376" alt="image" src="https://github.com/user-attachments/assets/e662683f-0084-4bf2-b45b-15cc262e6307" />

We add a titanium layer because it acts as a good barrier for the bottom layers and addition layer

<img width="736" height="397" alt="image" src="https://github.com/user-attachments/assets/a159420e-237c-45de-9add-c868ccda736b" />

<img width="751" height="395" alt="image" src="https://github.com/user-attachments/assets/65059f9c-3122-4fa2-83b8-30a67c3aa42c" />

<img width="727" height="379" alt="image" src="https://github.com/user-attachments/assets/85fb3633-de8d-40dd-9edc-7bdc63f4adf5" />

<img width="647" height="461" alt="image" src="https://github.com/user-attachments/assets/7e533e67-3953-4aac-95f7-9295615e62d2" />

<img width="742" height="406" alt="image" src="https://github.com/user-attachments/assets/5f063017-61e8-4a86-a65c-d2de79f22a51" />

<img width="619" height="363" alt="image" src="https://github.com/user-attachments/assets/1e74def3-919c-4bb0-83aa-e5f672999b3c" />

<img width="743" height="397" alt="image" src="https://github.com/user-attachments/assets/5dcb64eb-e95d-492d-8769-ec4044218b62" />

<img width="752" height="397" alt="image" src="https://github.com/user-attachments/assets/5845984e-67c7-4898-9c61-4a74d6ce20a1" />

<img width="730" height="405" alt="image" src="https://github.com/user-attachments/assets/e16476c1-ba6c-49aa-a328-712a72c686ad" />

TiN acts a good barrier and addition

<img width="727" height="396" alt="image" src="https://github.com/user-attachments/assets/3e586faa-7b07-4456-9a52-0c7e1dc0f5d5" />

<img width="718" height="447" alt="image" src="https://github.com/user-attachments/assets/cc0403d1-3f15-4b4c-b7fd-fea0aad5211a" />

As you go from bottom to top the thickness of the metal increases

<img width="743" height="448" alt="image" src="https://github.com/user-attachments/assets/e7e66b99-da51-4f53-ad88-29ad0ab4d00f" />

<img width="740" height="485" alt="image" src="https://github.com/user-attachments/assets/895878d0-dae1-40b4-b553-fae17c4562f0" />

<img width="608" height="481" alt="image" src="https://github.com/user-attachments/assets/137e2203-e590-46a2-b19b-7c36320a4626" />


### 44 - Lab introduction to Sky130 basic layers layout and LEF using inverter

These are the layers. If you hover over them the name appears on the top.

<img width="82" height="553" alt="image" src="https://github.com/user-attachments/assets/570d35ad-9660-4c8b-8ddb-2cbfc2236bb4" />

If you press S two times when hovering over a compoent the connections get highlighted too

<img width="207" height="355" alt="image" src="https://github.com/user-attachments/assets/882483b2-6aa7-401b-be93-f8f2ed74dabd" />


### 45 - Lab steps to create std cell layout and extract spice netlist

If there is an error click DRC and find next error and it will direct you to the area where it has an error. If you want to see the specific error check the magic terminal.

<img width="701" height="113" alt="image" src="https://github.com/user-attachments/assets/698a1f5f-d6fe-44e0-a1aa-5c8d06fcfbff" />

<img width="650" height="169" alt="image" src="https://github.com/user-attachments/assets/8ca55c66-c18d-412e-9b27-2fc535e9e686" />


Doing this command will extract all the parasetic capacitances 

<img width="353" height="57" alt="image" src="https://github.com/user-attachments/assets/e3e57961-c3c0-45a6-933c-61bf23cebc32" />

<img width="389" height="101" alt="image" src="https://github.com/user-attachments/assets/5dfc6d44-3f49-4f81-8a8b-318af0d39968" />

<img width="842" height="193" alt="image" src="https://github.com/user-attachments/assets/35eab44c-13b9-4310-9bc8-0b7880ada486" />

## Sky130 Tech File
### 46 - Lab steps to create final SPICE deck using Sky130 tech

<img width="730" height="484" alt="image" src="https://github.com/user-attachments/assets/a51f41fc-4c77-49b7-8ab7-32ece981022a" />


<img width="481" height="382" alt="image" src="https://github.com/user-attachments/assets/c2f7f365-46dc-4732-b85b-1b2aff7a67c6" />

We want to create extra supply points and do the following using nano or vim and :wq! to exit
<img width="855" height="527" alt="image" src="https://github.com/user-attachments/assets/5160124f-b9ea-4303-a54a-4c7eeb88e06d" />

in libs pshort.lib, we see that its called pshort_model
<img width="678" height="183" alt="image" src="https://github.com/user-attachments/assets/a5262991-5844-4451-b86a-481296389ad2" />
change the names to pshort_model.0 and nshort_model.0
<img width="764" height="508" alt="image" src="https://github.com/user-attachments/assets/db0a8431-438f-4919-b53a-ea633c448057" />

a few other things have to be changed as well

<img width="1219" height="646" alt="image" src="https://github.com/user-attachments/assets/6cbe0e35-a8bc-4cdb-86ba-ac48bea3ecbf" />


### 47 - Lab steps to characterize inverter using sky130 model files

<img width="1067" height="38" alt="image" src="https://github.com/user-attachments/assets/490e8da0-6f3b-49c1-8a47-7e496becd99c" />

This should be what you see after running ngspice

<img width="1052" height="623" alt="image" src="https://github.com/user-attachments/assets/efca61cb-21ee-4d2f-bbad-651c92750f24" />

> ngspice 1 -> plot y vs time a
This will generate a waveform

<img width="656" height="734" alt="image" src="https://github.com/user-attachments/assets/d9787dd6-7a13-4034-914f-b8402f8d81ee" />

<img width="1141" height="690" alt="image" src="https://github.com/user-attachments/assets/c68249a9-23a6-46f5-be9f-9d925e718777" />

So we go edit some stuff

*note: i edited other stuff to match the tutorial*
<img width="991" height="651" alt="image" src="https://github.com/user-attachments/assets/1e484aed-5831-479b-ad3c-e49a027c2498" />

then in ngspice
> plot y vs time a

<img width="1148" height="742" alt="image" src="https://github.com/user-attachments/assets/79678112-4d2b-47e3-a29a-bfa785319ee7" />

and to zoom in right click to create a box and then fullscreen window

<img width="1150" height="734" alt="image" src="https://github.com/user-attachments/assets/846d7594-93ef-4815-9ef6-300bf6f29e49" />

<img width="1110" height="657" alt="image" src="https://github.com/user-attachments/assets/1283e73d-3c81-4349-8c9d-87d9bc74a13c" />

click on a point and it will give the position in terminal

<img width="296" height="53" alt="image" src="https://github.com/user-attachments/assets/fa394814-0692-4485-8186-2864dbcc8ffd" />

this is the 20%

next we are going to find 80%

<img width="267" height="27" alt="image" src="https://github.com/user-attachments/assets/c8a33a88-c216-4720-b296-2618cab31af6" />

the difference between the two x will give you rise time

now we are going to find cell rise delay

<img width="305" height="69" alt="image" src="https://github.com/user-attachments/assets/0585c9f6-1797-429d-876d-d789e08023ef" />

Subtract the two x

### 48 - Lab introduction to Magic tool options and DRC rules

[Magic documentation](http://opencircuitdesign.com/magic/) -> tells you how to use magic


### 49 - Lab introduction to Sky130 pdk's and steps to download labs

[Skywater documentation](https://skywater-pdk.readthedocs.io/en/main/) <- this website might not exist anymore

Magic tech file should be created first. To get the full pdk you need to install the github.

To start the lab you should cd to /home/USER/drc_tests

[we need this for the lab](http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz)

Then we extract the files using tar xfz drc_tests.tgz

And then we go into the directory by cd drc_tests and open magic using magic -d XR

<img width="1193" height="403" alt="image" src="https://github.com/user-attachments/assets/6a7a53d7-0bee-4898-b2e7-aa44e5cac7b1" />

<img width="440" height="39" alt="image" src="https://github.com/user-attachments/assets/a3539410-d026-40ad-949c-a0e66c570157" />

### 50 - Lab introduction to Magic and steps to load Sky130 tech-rules
You can open met3.mag by file -> open -> met3.mag

<img width="947" height="550" alt="image" src="https://github.com/user-attachments/assets/a56fc57c-57b9-4137-a6c8-c3c2d571dd1b" />

On the periphery rules, you can find the rules for each metal

use a colon to enter commands into the terminal

<img width="830" height="891" alt="image" src="https://github.com/user-attachments/assets/971a1e8e-f8db-4c87-a815-eef8ef09e219" />

<img width="184" height="74" alt="image" src="https://github.com/user-attachments/assets/835b633e-0161-4587-b78f-19764c5f2bf7" />

<img width="217" height="89" alt="image" src="https://github.com/user-attachments/assets/163e4d43-96a3-43b2-a287-d152752d8ea0" />

<img width="811" height="943" alt="image" src="https://github.com/user-attachments/assets/2c68e010-2136-4a16-976d-215303d74ac6" />

<img width="536" height="577" alt="image" src="https://github.com/user-attachments/assets/37aee6a0-62a1-4244-a38c-9e82810c7863" />

snap int - aligns the box to the edges
box - can be used to measure distance

### 51 - Lab exercise to fix poly.9 error in Sky130 tech-file

<img width="1026" height="717" alt="image" src="https://github.com/user-attachments/assets/dad47382-8de4-4618-810b-3424c3d4f9b4" />

<img width="791" height="563" alt="image" src="https://github.com/user-attachments/assets/6e7dfcea-1277-43d2-a995-700a07fb602a" />

To see the file go vi sky130A.tech in drc_tests

<img width="802" height="847" alt="image" src="https://github.com/user-attachments/assets/6e8357e6-c561-43e1-99f8-b5b497827a9b" />

to find stuff use / and whatever you want to find

to edit the file, use i to insert stuff

to save press esc and then :wq

<img width="713" height="318" alt="image" src="https://github.com/user-attachments/assets/7da9e9f1-66a8-4931-b685-73e53200a91b" />

<img width="531" height="108" alt="image" src="https://github.com/user-attachments/assets/ecf7543f-1287-4a4b-80d1-defc9adf53a7" />

<img width="1009" height="506" alt="image" src="https://github.com/user-attachments/assets/a208d106-65a4-4de7-a506-c0ae943b1659" />

rerun drc check

### 52 - Lab exercise to implement poly resistor spacing to diff and tap

<img width="680" height="347" alt="image" src="https://github.com/user-attachments/assets/6042545b-cc2d-49fe-93f7-1689990ff435" />

poly.1a - change the size of poly rule

<img width="1437" height="751" alt="image" src="https://github.com/user-attachments/assets/bba38760-2390-4889-97d5-aa715630b754" />


### 53 - Lab challenge exercise to describe DRC error as geometrical construct

cifmaxwidth - part of rule set that check layers exactly as how they are in the gds output even though those layers aren't something you can draw directly in the layout

there are several more cif drc rules with width and spacing but cifmaxwidth is the most convenient

here width is 0 and bend is illegal 

<img width="857" height="353" alt="image" src="https://github.com/user-attachments/assets/0ca9b663-1dc9-4ce4-9a59-258156b87e3f" />

all that matters is using layer name which in this case is nwell_missing dnwell

<img width="808" height="403" alt="image" src="https://github.com/user-attachments/assets/31d202d4-1e22-45fb-9245-3a79e8e7a9ac" />

all the heavy lifting is done in cifoutput

<img width="444" height="377" alt="image" src="https://github.com/user-attachments/assets/bbfc07cc-ca9d-4c7b-8a91-d419b8ed80e3" />

in nwell.mag, you can see that the edge of the deep nwell needs to be covered by a regular ring of nwell
the outside distance rule can be implemented with a surround drc rule but the inside can't be captured with an edge type rule

let's go find where this layer is described in the cif output section

first we need to go find the style called drc

the way the cif max width drc rule is implemented with equalt ot 0 implies that the nwell_missing layer is what's leftover if either the inside or outside dimension of nwell overlapping deep nwell doesn't reach the required distance

*NOTE: everything implemented in the cif is a templayer rather than a layer*

temp layers have the unique feature where they can be used as building blocks of other layers

since the drc file does not produce any gds output theres no point in creating normal layers in it and so everything is a temp layer

<img width="689" height="177" alt="image" src="https://github.com/user-attachments/assets/61ba307c-5333-43fb-8538-4747862987b6" />

the templayer dnwell_shrink is shrunk 1030 nm and is the required distance that the nwell must overlap the well on the inside

dnwell_shrink represents the largest open area that you can have inside the area of deep n well

the nwell_missing templayer starts with the dnwell layer then grows it by 400, which is the distance required by the surround rules in nm -> gives you the smallest nwell area that is needed to cover the deep nwell layer

next the rule does a and-not operation on dnwell_shrink -> contains least possible amount of nwell that satisfy both the outside surround and the inside overlap rules

this means that if any of the area that does not contain nwell then one of the two rules is being violated

so the last operation rule is to do and-not nwell which will result in something leftover if any rules are violated

now that leftover bit gets passed back to the cifmaxwidth rule and if theres anything leftover, that gets flagged as an error

in the layout, by putting cursor box around the nwell.6 drawing 

first you need to do the command cif ostyle drc because you can only see the layers for the cif output layers 

<img width="1155" height="598" alt="image" src="https://github.com/user-attachments/assets/ec2c5054-cc09-4271-81bd-33c7319ae123" />

then cif see dnwell_shrink to see that area

then clear it with feed clear

then cif see nwell_missing

feed clear

<img width="973" height="608" alt="image" src="https://github.com/user-attachments/assets/e36a6e82-ff47-450a-bb62-2c0b9efc32bd" />

make sure use right style because only one can be used at a time 

*NOTE: any edge based rule could in principle be made of the cif operators but also be aware that **generating these layers is very compute intensive** and will slow magic down*

TO keep magic from getting bugged down, it's best to use the drc simple edge based rules whenever possible and to put cif output rules in a separate style variant that can be ran on demand but can be prevented from running most of the time during interactive layout so it doesnt slow things down

those rules are best left to a batch style drc process, but they can be checked by the user from time to time if needed

<img width="540" height="296" alt="image" src="https://github.com/user-attachments/assets/9ed1b191-4f33-49bd-85bf-919ffe022e13" />

in this tech file the two variants are named drc fast and drc full 
- drc fast is intended for backend metal layers and large synthesized digital design without forcing magic to check all layers below 
- drc full will check everything, which can keep up with the interactive use as long as its in a relatively small layout

you can switch between them by using drc style, drc fast, and drc full

### 54 - Lab challenge to find missing or incorrect rules and fix them

<img width="513" height="389" alt="image" src="https://github.com/user-attachments/assets/b6ab85b1-8cfb-47c5-aeb8-5f8fc506a289" />

The rule is stated that all nwell must contain metal contacted taps. The rule only checks licon on tap (every nwell must have a n type layer contact, which in magic is called n contact or nsc inside it somewhere)

Since there's no distance associated with the rule, it's possible to write this as a simple edge based drc rule but does lend itself to a cif output rule very easily

The general idea of the rule is this: 
- take all ntype contacts and expand the area of any nwell beneath

for that, there's a cif output operator called bloat-all

after applying the bloat-all operator, you have a set of all nwell that contains tap so all you ahve to do is take the set of all nwell and remove all nwell that contains tap and whatever is leftover is an error 

<img width="780" height="275" alt="image" src="https://github.com/user-attachments/assets/9657140a-cfff-4f1b-ae42-37be8af3e497" />

<img width="404" height="333" alt="image" src="https://github.com/user-attachments/assets/e5cceb56-d2d6-4f72-8e86-24cd947f2fe8" />

all nwell geometry subtracted by nwell tapped geometry, leaving only those who are untapped

<img width="397" height="32" alt="image" src="https://github.com/user-attachments/assets/9c90c181-53ee-4666-b0a8-c1be63bae89b" />


this rule is only checked when drc style is full, all the rules below it are checked for all drc style

<img width="1033" height="476" alt="image" src="https://github.com/user-attachments/assets/6106f2da-749f-4af7-bdb9-d2da96199304" />

<img width="906" height="407" alt="image" src="https://github.com/user-attachments/assets/8bdccfea-de5c-43c9-802f-5d91799b84e3" />

<img width="686" height="350" alt="image" src="https://github.com/user-attachments/assets/7c37d7b4-6e15-420b-bea7-9e1eb5822cdb" />








