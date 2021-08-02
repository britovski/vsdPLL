# vsdPLL

PLL Design Workshop repo

## Description
This repository is a summary of the 2-day workshop of PLL Design using sky130 provided by VSD. It is organized day-by-day as follows:

## Day 1

First day is used to introduce the cloud based structure of the workshop. The learning platform is divided in assessments (MCQs) and learning skills (DXSKXs). Also, a web based linux virtual machine is provided to labs hands-on execution.

Cloud based learning is guided through learning skils. On the first day, the focus was on PLL theory and components, as well as workarea and tools setup.

### Fundamentals
Why PLL?
- To get precise clock signals without phase or frequency noise.
- VCO (flexible , implemented on-chip);
- Quartz crystal (as a precise reference);
- Phase noise definition.

### PLL Components
An introduction to the PLL Components is done.
- PFD
*used to compare frequency/phase deviations
- CP
- LPF
- VCO
*previous three are used to adjust frequency to match ref. signal
- FD
*if some frequency division are needed.

### Some terms
- Lock range
- capture range
- settling time

### Design tools
A brief introduction to tools and design flows are performed.

For tools setup, is needed:
- ngspice for simulation;
- magic for layout and extraction;
- PDK (primitive cells and tech file);

The development flow is defined as:
- SPICE level circuit development;
- Pre-Layout sims;
- Layout development;
- Parasitics extraction;
- Post-Layout sims.

Some additional PDK content explanation was given from skywater-pdk github.

### PLL specs
PLL specifications for the workshop are presented:
- corner typical (TT);
- room temperature;
- power supply 1.8 V;
*previous three specs are PVT.
- VCO mode and PLL mode;
- input fmin=5 MHz, fmax=12.5 MHz;
- multiplier = 8x
- jitter RMS < ~20 ns
- duty cycle 50%.

Some circuit topologies are presented and workarea is setting up:
- install ngspice;
- setup libraries (nmos and pmos from pr sky130 lib);
- install magic and get tech file from open_pdks.

## Day 2

Second day presents a walkthrough on the PLL Design previously performed by Lakshmi, available on: https://github.com/lakshmi-sathi/avsdpll_1v8

### Circuit design
Ngspice circuit description was done using FD example.
- Some SPICE structures describes as subcircuits and include/control statements.
- Ngspice simulation performed with FD example (showing 2T output).
After that, other designed blocks was presented, as CP (showing .ic statement) and VCO, as well as simulations are performed.
Least, combination of the blocks are presented to perform PRE-LAYOUT SIMULATION.
- create a new circuit using the individual blocks are subcircuits and instantiate them
- pre-layout simulation is performed.


**What to do if doesn´t work?**

Some tips are provided to:
- observe what kind of issue is faced;
- always debug individual component fully before moving combined simulation;
- if some signals coming up flat or if simulation is crashing: check nodes, names, component sizes, etc...
- if signals are right but mimicking not happening: check sim. range and parameters,...

### Layout Design
Magic walkthrough is presented:
- basic MOSFET painting;
- basic commands;
- showing layers;
- DRC issues;
- labels (namimg convention) & ports (I/O ports definition).

Block layouts are presented (no layout techniques were used such as transistor orientation).

### Parasitics extraction and Post-layout sims
Parasitics extraction are presented using PFD example on magic.
- extract all and ext2spice commands;
- adjust scale on extracted spice file;

Post-layout sims are performed by including extracted SPICE file and re-sim (PFD example was shown).

### Combine layouts and generate GDS
"Combine layouts" are perfomed:
- use "place instance" on magic to instantiate each layout block;
- perform manual routing using wire tool;
- after finish, write GDS file.

### Tapeout
Tapeout theory is presented as the final act to the send our design to the fab.
- Preparation is needed: I/O pads, peripherals, memory, test structures, etc...
- efabless provide a SoC to address some tapeout issues, named "caravel"
- caravel has two versions, analog and digital

A brief caravel walkthrough is shown:
- download gds wrapper;
- open magic and see I/Os;
- instantiate PLL and perform connections to the caravel I/Os.

## Final notes

Good to learn PLL design aspects and to practice using skills related to sky130 design including tapeout tips.

## Acknowledgement

Kunal Ghosh, Co-founder (VSD Corp. Pvt. Ltd)
Lakshmi S, MS ECE
