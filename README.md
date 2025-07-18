# VSDIATgrind
GitHub for my VSDIAT adventure!

[Sky130 DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#sky130-day-1---inception-of-open-source-eda-openlane-and-sky130-pdk)
- [How to Talk to Computers](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#how-to-talk-to-computers)
    - [0 - Introduction to QFN-48 Package, chip pads, core, die and IPs](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#0---introduction-to-qfn-48-package-chip-pads-core-die-and-ips)
    - [1 - Introduction to RISC-V](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#1---introduction-to-risc-v)
    - [2 - From Software Applications to Hardware](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#2---from-software-applications-to-hardware)
- [SoC Design and OpenLANE](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#soc-design-and-openlane)
    - [3 - Introduction to all components of open-source digital asic design](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#3---introduction-to-all-components-of-open-source-digital-asic-design)
    - [4 - Simplified RTL2GDS flow](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#4---simplified-rtl2gds-flow)
    - [5 - Introduction to OpenLANE and Strive chipsets](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#5---introduction-to-openlane-and-strive-chipsets)
    - [6 - Introduction to OpenLANE detailed ASIC design flow](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#6---introduction-to-openlane-detailed-asic-design-flow)
- [Get Familiar to Open Source EDA Tools](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#get-familiar-to-open-source-eda-tools)
    - [7 - OpenLANE Directory in Detail](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#7---openlane-directory-structure-in-detail)
    - [8 - Design Preparation Step](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#8---design-preparation-step)
    - [9 - Review Files After Design Prep and Run Synthesis](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#9---review-files-after-design-prep-and-run-synthesis)
    - [10 - OpenLANE Project Git Link Description](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#10---openlane-project-git-link-description)
    - [11 - Steps to Characterize Synthesis Results](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%201.md#11---steps-to-characterize-synthesis-results)

[Sky130 DAY 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#sky130-day-2---good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)
- [Chip Floor planning considerations](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#chip-floor-planning-considerations)
    - [12 - Utilization factor and aspect ratio](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#12---utilization-factor-and-aspect-ratio)
    - [13 - Concept of pre-placed cells](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#13---concept-of-pre-placed-cells)
    - [14 - De-coupling capacitors](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#14---de-coupling-capacitors)
    - [15 - Power planning](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#15---power-planning)
    - [16 - Pin placement and logical cell placement blockage](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#16---pin-placement-and-logical-cell-placement-blockage)
    - [17 - Steps to run floorplan using OpenLANE](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#17---steps-to-run-floorplan-using-openlane)
    - [18 - Review floorplan files and steps to view floorplan](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#18---review-floorplan-files-and-steps-to-view-floorplan)
    - [19 - Review floorplan layout in Magic](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#19---review-floorplan-layout-in-magic)
- [Library Binding and Placement](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#library-binding-and-placement)
    - [20 - Netlist binding and initial place design](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#20---netlist-binding-and-initial-place-design)
    - [21 - Optimize placement using estimated wire-length and capacitance](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#21---optimize-placement-using-estimated-wire-length-and-capacitance)
    - [22 - Final placement optimization](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#22---final-placement-and-optimization)
    - [23 - Need for libraries and characterization](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#23---need-for-libraries-and-characterization)
    - [24 - Congestion aware placement using RePlAce](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#24---congestion-aware-placement-using-replace)
- [Cell Design and Characterization Flows](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#cell-design-and-characterization-flows)
    - [25 - Inputs for cell design flow](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#25---inputs-for-cell-design-flow)
    - [26 - Circuit design step](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#26---circuit-design-step)
    - [27 - Layout design step](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#27---layout-design-step)
    - [28 - Typical characterization flow](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#28---typical-characterization-flow)
- [General Timing Characterization Parameters](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#general-timing-characterization-parameters)
    - [29 - Timing threshold definitions](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#29---timing-threshold-definitions)
    - [30 - Propagation delay and transition time](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%202.md#30---propagation-delay-and-transition-time)

[Sky130 DAY 3 - Design library cell using Magic Layout and ngspice characterization](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#sky130-day-3---design-library-cell-using-magic-layout-and-ngspice-characterization)
- [Labs for CMOS inverter ngspice simulations](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#labs-for-cmos-inverter-ngspice-simulations)
    - [31 - IO placer revision](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#31---io-placer-revision)
    - [32 - SPICE deck creation for CMOS inverter](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#32---spice-deck-creation-for-cmos-inverter)
    - [33 - SPICE simulation lab for CMOS inverter](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#32---spice-deck-creation-for-cmos-inverter)
    - [34 - Swtiching Threshold Vm](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#34---swtiching-threshold-vm)
    - [35 - Static and dynamic simulation of CMOS inverter](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#35---static-and-dynamic-simulation-of-cmos-inverter)
    - [36 - Lab steps to git clone vsdstdcelldesign](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#36---lab-steps-to-git-clone-vsdstdcelldesign)
- [Inception of Layout - CMOS fabrication process](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#inception-of-layout---cmos-fabrication-process)
    - [37 - Create Active regions](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#37---create-active-regions)
    - [38 - Formation of N-well and P-well](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#38---formation-of-n-well-and-p-well)
    - [39 - Formation of gate terminal](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#39---formation-of-gate-terminal)
    - [40 - Lightly doped drain(LDD) formation](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#40---lightly-doped-drainldd-formation)
    - [41 - Source - drain formation](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#41---source---drain-formation)
    - [42 - Local interconnect formation](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#41---source---drain-formation)
    - [43 - Higher level metal formation](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#43---higher-level-metal-formation)
    - [44 - Lab introduction to Sky130 basic layers layout and LEF using inverter](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#44---lab-introduction-to-sky130-basic-layers-layout-and-lef-using-inverter)
    - [45 - Lab steps to create std cell layout and extract spice netlist](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#45---lab-steps-to-create-std-cell-layout-and-extract-spice-netlist)
- [Sky130 Tech File](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#sky130-tech-file)
    - [46 - Lab steps to create final SPICE deck using Sky130 tech](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#46---lab-steps-to-create-final-spice-deck-using-sky130-tech)
    - [47 - Lab steps to characterize inverter using sky130 model files](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#47---lab-steps-to-characterize-inverter-using-sky130-model-files)
    - [48 - Lab introduction to Magic tool options and DRC rules](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#48---lab-introduction-to-magic-tool-options-and-drc-rules)
    - [49 - Lab introduction to Sky130 pdk's and steps to download labs](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#49---lab-introduction-to-sky130-pdks-and-steps-to-download-labs)
    - [50 - Lab introduction to Magic and steps to load Sky130 tech-rules](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#50---lab-introduction-to-magic-and-steps-to-load-sky130-tech-rules)
    - [51 - Lab exercise to fix poly.9 error in Sky130 tech-file](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#51---lab-exercise-to-fix-poly9-error-in-sky130-tech-file)
    - [52 - Lab exercise to implement poly resistor spacing to diff and tap](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#52---lab-exercise-to-implement-poly-resistor-spacing-to-diff-and-tap)
    - [53 - Lab challenge exercise to describe DRC error as geometrical construct](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#53---lab-challenge-exercise-to-describe-drc-error-as-geometrical-construct)
    - [54 - Lab challenge to find missing or incorrect rules and fix them](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%203.md#54---lab-challenge-to-find-missing-or-incorrect-rules-and-fix-them)
  
[Sky130 DAY 4 - Pre-layout timing analysis and importance of good clock tree](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%204.md#sky130-day-4---pre-layout-timing-analysis-and-importance-of-good-clock-tree)
- [Timing modelling using delay tables](https://github.com/PenguinDaBozo/VSDIATgrind/blob/main/DAY%204.md#timing-modelling-using-delay-tables)
    - 55 - Labs steps to convert grid info to track info
    - 56 - Lab steps to convert magic layout to std cell LEF
    - 57 - Intoduction to timing libs and steps to include new cell in synthesis
    - 58 - Introduction to delay tables
    - 59 - Delay table usage Part 1
    - 60 - Delay table usage Part 2
    - 61 - Lab steps to configure synthesis settings to fix slack and include vsdinv
- Timing analysis with ideal clocks using openSTA
    - 62 - Setup timing analysis and introduction to flip-flop setup time
    - 63 - Introduction to clock jitter and uncertainty
    - 64 - Lab steps to configure OpenSTA for post-synth timing analysis
    - 65 - Lab steps to optimize synthesis to reduce setup violations
    - 66 - Lab steps to do basic timing ECO
- Clock tree synthesis TritonCTS and signal integrity
    - 67 - Clock tree routing and buffering using H-Tree algorithm
    - 68 - Crosstalk and clock net shielding
    - 69 - Lab steps to run CTS using TritonCTS
    - 70 - Lab steps to verify CTS runs
- Timing analysis with real clocks using openSTA
    - 71 - Setup timing analysis using real clocks
    - 72 - Hold timing analysis using real clocks
    - 73 - Lab steps to analyze timing with real clocks using OpenSTA
    - 74 - Lab steps to execute OpenSTA with right timinig libraries and CTS assignment
    - 75 - Lab steps to observe impact of bigger CTS buffers on setup and hold timing

Sky130 DAY 5 - Final steps for RTL2GDS using tritonRoute and openSTA
