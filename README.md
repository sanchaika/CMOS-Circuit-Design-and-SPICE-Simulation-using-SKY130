# CMOS Circuit Design and SPICE Simulation using Sky130
This repository contains the design and simulation of CMOS circuits using the Sky130 open-source Process Design Kit (PDK). The project demonstrates transistor-level circuit implementation and analysis using SPICE simulations.
## Overview
This repository contains the design and simulation of CMOS circuits using the Sky130 open-source Process Design Kit (PDK). The project demonstrates transistor-level circuit implementation and analysis using SPICE simulations.

## Objectives
- Learn CMOS circuit design fundamentals
- Understand Sky130 PDK usage
- Perform transistor characterization
- Analyze simulation results using ngspice

## Tools Used
- Sky130 PDK
- ngspice
- Magic VLSI
- GitHub

## Design Flow
1. Circuit Design
2. SPICE Netlist Creation
3. Simulation using ngspice
4. Waveform Analysis
5. Result Documentation

## Table of Contents
#NgspiceSky130 - Day 1 - Basics of NMOS Drain current (Id) vs Drain-to-source Voltage (Vds)
##NgspiceSky130_D1SK1 - Introduction to Circuit Design and SPICE simulations
##NgspiceSky130_D1SK2 - NMOS resistive region and saturation region of operation
##NgspiceSky130_D1SK3 - Introduction to SPICE
#NgspiceSky130 - Day 2 - Velocity saturation and basics of CMOS inverter VTC
##NgspiceSky130_D2SK1 - SPICE simulation for lower nodes and velocity saturation effect
##NgspiceSky130_D2SK2 - CMOS voltage transfer characteristics (VTC)
#NgspiceSky130 - Day 3 - CMOS Switching threshold and dynamic simulations
##NgspiceSky130_D3SK1 - Voltage transfer characteristics – SPICE simulations
##NgspiceSky130_D3SK2 - Static behavior evaluation – CMOS inverter robustness – Switching Threshold
#NgspiceSky130 - Day 4 - CMOS Noise Margin robustness evaluation
##NgspiceSky130_D4SK1 - Static behavior evaluation – CMOS inverter robustness – Noise margin
#NgspiceSky130 - Day 5 - CMOS power supply and device variation robustness evaluation
##NgspiceSky130_D5SK1 - Static behavior evaluation – CMOS inverter robustness – Power supply variation
##NgspiceSky130_D5SK2 - Static behavior evaluation – CMOS inverter robustness – Device variation

# NgspiceSky130 - Day 1 - Basics of NMOS Drain current (Id) vs Drain-to-source Voltage (Vds)
## Introduction to Circuit Design and SPICE simulations
## L1 Why do we need SPICE simulations?
SPICE (Simulation Program with Integrated Circuit Emphasis) simulations are used to predict the behavior of electronic circuits before they are physically fabricated. They help designers analyze circuit performance, verify functionality, and identify potential issues at an early stage.
<img width="525" height="511" alt="1" src="https://github.com/user-attachments/assets/9ffd1361-410e-4af0-b714-12c8bfbbc564" />
A circuit design includes PMOS and NMOS tied together in such a fashion that they result into logic gates such as NAND, NOR, OR, AND etc.
The above inverter will have the following charactersitics, we will do the SPICE simulations to find the delay and so we will get the W/L ratio of the particular transistor.
<img width="795" height="610" alt="2" src="https://github.com/user-attachments/assets/4f93e9d7-b181-4db1-9169-037da471a42f" />


