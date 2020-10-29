# Advanced-Physical-Design-using-OpenLANE-Sky130
This repository contains all the information needed on SoC design planning in Openlane flow using the latest Google-SkyWater 130nm process node. One can design and characterize their own standard cell and generate a full GDSII from a RTL netlist.

## Table of Contents
* Introduction to Openlane and sky130 PDK
* Overview of Physical Design Flow
* Introduction to Openlane Flow
   Opensource Tools at each step
* Build and Invoke Openlane
* openlane Directory structure
* Build your Design in openlane
   Preparation
   Synthesis
   Floorplan
   Placement
* Standard cell design and characterization
   Extracting lef file from magic file
   Plugging Custom LEF to openlane flow
* Adjusting the timing violation
* openlane flow after plugging custom cell


### Introduction to Openlane and sky130 PDK

OpenLANE is an automated RTL to GDSII flow which includes in it several open source tools such as OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor and custom methodology scripts for design exploration and optimization.Full ASIC implementation steps from RTL to GDSII can be performed using this flow.


The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility.

#### Overview of Physical Design Flow
The Backend flow is transforms the RTL circuit description into a physical design,composed by gates and its interconnections. The below flow chart gives a better picture of physical design flow.

* Synthesis

During synthesis the RTL description is converted into a structural gate level based netlist which instantiates standard cells and macros that compose the circuit and its connections.In this step,Translation + Optimization + Mapping are performed.

* Floor/Power Planning

1) Width and height of core, Die are defined 2) Location of preplaced cells is defined and these cells are surrounded with Decoupling capacitors 3) Multiple VDD ,VSS lines are defined 4) Pin placement, logical cell placement blockage is done

* Placement

During this step, netlist is binded with physical cells and these are placed on floorplan rows aligned with the sites.Standard cell placement happens here.
Clock Tree Synthesis

During this step, a clock distribution network is created to deliver clock to all the sequential elements with minimum skew.

* Routing

During this step, interconnects are implemented using available metal layers , routing grid is formed using metal tracks.Routing is done in two stages 1) Global routing - Generates Routing guides 2) Detailed routing - This routes within the proprocessed route guides provided from Global routing step. So routing basically finds out the best possible connection between two end points ,one being the source and the other being target.

* Sign Off

During this step, Physical verifications like Design Rule Check(DRC), Layout Versus Schematic(LVS) and Timing verification like Static Timing Analysis(STA) are done.
