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

## WHy do we need SPICE?
The clock Tree synthesis, crosstalks, and timing are built on SPICE (Simulation Program with Integrated Circuit Emphasis), without SPICE there won't be delays and if there are no delays physical design flow, crosstalk won't make any sense.
Let us say we have done some Clock Tree Synthesis of the circuit shown below with bufffers with different capacitive load at the output.
A two-level buffering structure is implemented to drive multiple loads while reducing propagation delay. Delay values are determined using buffer characterization tables based on input slew and output load.
After the SPICE simulation we get a "Delay Table", which includes input slew and output load. The intersection value of Input slew and Output load is considered as Delay. Delay tables for both level 1 and level 2 buffers have been shown. This is calculated by circuit design and simulation

<img width="1305" height="626" alt="4" src="https://github.com/user-attachments/assets/3419e7ce-bad5-4d9c-b036-fe19848f9207" />

The source of the above Delay Tables comes from circuit design using SPICE simulations. SPICE simulations involves characterisation of any CMOS logic.

## L2 Introduction to basic element in circuit design-NMOS
An NMOS transistor consist of P-type substrate, heavily doped with n+ region. There is an isolated region which isolates the transistor from other transistors. The n+regions are Source and Drain. Above itthere is an oxide layer, and top of it is metal deposition which is the GAte termianal.

<img width="1167" height="482" alt="5" src="https://github.com/user-attachments/assets/07f0e3c8-f157-4b78-b972-40d14b6e81eb" />

<img width="1285" height="582" alt="10" src="https://github.com/user-attachments/assets/7857dc8a-80e3-4d32-b7b9-8a9694ec141f" />

Threshold Voltage is a very important term, all the characterisation depends on threshold voltage.
When Vgs=0 => source and drain terminal both are grounded, Body is also ground. P-substrate and n+ act as PN junction diode and as there is no potential so there is a high resistance. No channel formation is there.
When Vgs>0 => gate is now positively charged and due to this there will be Accumulation of negative charges at the surface of substrate.

## L3 Strong inversion and threshold voltage
Due to Accumulation of negative charges, there will be formation of Depletion Region, depleting of it's majority carriers i.e positive carriers here.

<img width="816" height="373" alt="8" src="https://github.com/user-attachments/assets/892164b2-4f8d-42e1-b7e0-009864be180c" />

Now we will increase the Gate voltage further, we will see that the positive charge carriers will be repelled and there will be increase of Depletion Width. On further increase of Gate voltage we will reach at a point where the surface gets inverted into an n-type material, this is called "Surface Inversion" or "Stronf Inversion". The gate voltage of Vgs voltage where Strong Inversion happens is called "Threshold Voltage".

<img width="1256" height="515" alt="9" src="https://github.com/user-attachments/assets/b272ce72-a68d-4a89-b427-9476ff749db1" />

What will happen if we further increase Vgs? As there are no more negative charges that will be attracted towards the positive Vgs, The negative charges from n+ region will get attracted and so there will be a formation of channel at the surface.

<img width="1285" height="582" alt="10" src="https://github.com/user-attachments/assets/8b0a1e6b-8279-49cd-a84a-45ff1161b4a0" />

Now there is a possibility of current from Source to Drain. The channel has bridged the gap between source to drain regions. But as there is no Drain voltage so the elctrons will not move, this is "Cut Off Region".
We will see what happens when we change the potential of Body terminal.

<img width="1263" height="497" alt="11" src="https://github.com/user-attachments/assets/0ae3d359-6a12-49bd-997c-11e04be22a8d" />

There will be increase in depletion region between source and body terminal. 

## L4 Threshold voltage with positive substrate potential
If we increase Vgs, we will see that the depletion region increase in both the cases. But, in second case as there is Vsb +ve, few charges from channel will be pulled towards the source.

<img width="1178" height="588" alt="13" src="https://github.com/user-attachments/assets/c7d0cbc2-eb27-4e95-b532-96b5f859bff3" />

Due to this the surface inversion will be slower in second case. Therefore some extra potential has to be apllied in second case to create inversion.

<img width="1302" height="559" alt="14" src="https://github.com/user-attachments/assets/da01e08c-df30-4471-9332-62108c0d93c4" />

<img width="624" height="229" alt="15" src="https://github.com/user-attachments/assets/db15ee6d-988f-4d6c-a289-660263af11cc" />

Semiconductor surface inverts to n tye at Vgs = Vto + V1

<img width="1263" height="608" alt="16" src="https://github.com/user-attachments/assets/2303e96b-7fed-4d91-a8ca-78c9d30af321" />

The figure shows:
Vsb>0
For an NMOS:
Source is at a higher potential than the body. Source-body junction becomes more reverse biased. Depletion region becomes wider.
As the depletion region widens, more gate voltage is needed to attract enough electrons and form the inversion channel.

Therefore:
Threshold voltage increases
This phenomenon is called the Body Effect.

note : The parameters such as Gamma comes from foundaries after simulation of which in SPICE we get the value for Vt (Threshold Voltage).

## NMOS resistive region and saturation region of operation
## L1 Resistive region of operation with small drain-source voltage
For "Resistive region" of operation we apply Drain-source voltage. If we keep on increasing the Gate-source voltage, the channel width keeps on increasing. The net Induced charges is propotional to (Vgs-Vt).

Now let's apply very small Vds at start. And keep Vt=0.45V, Vgs also small initially. We can see that the source is grounded and Drain is at some potential, so there will also be a voltage gradient accross the channel.

Also, the Effective channel length is much lesser than the original channel length. y-axis represents the width of transistor and x axis is the voltage across the channel. On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.

<img width="805" height="530" alt="21" src="https://github.com/user-attachments/assets/0fd271e4-f94d-424e-95af-84c083e15723" />

## L2 Drift current theory
The effective channel voltage will vary w.r.t x.

for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V.

At x=Vds=0.05V, Vgs-Vx=0.95V. Now if we see the induced chagre equation, it is proportional to the effective channel voltage.

As we know there are two types of currents; Dift and Diffusion current, Here there is Drift current due to potential difference across the channel.

<img width="368" height="433" alt="23" src="https://github.com/user-attachments/assets/65c8837f-479c-4662-a404-190b0f93f9f4" />

<img width="1124" height="544" alt="25" src="https://github.com/user-attachments/assets/42840cfe-a7b3-4e00-9832-5143383fc98a" />

There are two types of currents; Dift and Diffusion current, Here there is Drift current as there is potential difference across the channel.

<img width="1264" height="570" alt="24" src="https://github.com/user-attachments/assets/30df588c-e4d0-44eb-9df5-62466c1d83ce" />

To get the drain current, the top view of transistor is required.

<img width="1124" height="544" alt="25" src="https://github.com/user-attachments/assets/42840cfe-a7b3-4e00-9832-5143383fc98a" />

## L3 Drain current model for linear region of operation
As there is change of voltage across the channel length, this will result in change of velocity which is a function of mobility and electrci field.

<img width="384" height="582" alt="26" src="https://github.com/user-attachments/assets/ba3f4e91-182e-4781-8136-031037b9e4e4" />

We will integrate the above equation, where limits of dV will be from 0 to Vds and limits of dx will be from 0 to L.

<img width="427" height="405" alt="27" src="https://github.com/user-attachments/assets/3c4b048b-fc34-4ef5-bbbc-809e82f01d2f" />

<img width="372" height="37" alt="29" src="https://github.com/user-attachments/assets/7df1d960-a0e9-4ed5-b844-24f115a825c3" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.

<img width="376" height="208" alt="30" src="https://github.com/user-attachments/assets/463ece34-fccb-4a80-bfae-67814ed72767" />

But, here we cannot say that it is in Linear region, since the Drain current is the quadratic function of Vds. We will calculate the Id with the given values.
 When (Vgs-Vt)>=Vds, It is in "Linear region".
 
<img width="654" height="423" alt="32" src="https://github.com/user-attachments/assets/e9a90119-e9ee-420d-b1d3-88e91bf96800" />

## L4 SPICE conclusion to resistive operation
TO ANSWER How do we calculate Id for different values of 'Vgs' and at every value of 'Vgs', sweep Vds till (Vgs-Vt) using linear equation for Id? We need to do SPICE simulations.

<img width="789" height="331" alt="Screenshot 2026-06-05 071450" src="https://github.com/user-attachments/assets/19fe1fa9-2571-43a1-bdd0-70a96550a90a" />

## L5 Pinch-off region condition
There is also a Region of operation when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region". We know the channel voltage is Vgs-Vds. Now, we will increase the Vds.


<img width="1243" height="589" alt="34" src="https://github.com/user-attachments/assets/016ee3c1-c7bc-41bf-a1d7-df44a21114d2" />

When Vgs-Vds is greater than Vt, there will be a conducting channel.
When Vgs-Vds is equal to Vt, we will see at drain side, just Inversion has happened as it is equal to Vt, so channel will start disappearing at drain side.


<img width="1276" height="565" alt="36" src="https://github.com/user-attachments/assets/37352173-26fb-4f56-ac29-484094de4267" />

When Vgs-Vds is equal to Vt, we will see at drain side, just Inversion has happened as it is equal to Vt, so channel will start disappearing at drain side.

Pinch off Voltage When the channel starts to disappear, is termed as "Pinch off region"

<img width="1307" height="569" alt="37" src="https://github.com/user-attachments/assets/b61514fb-35d0-427f-aea9-1b54fa8947e8" />

<img width="385" height="91" alt="38" src="https://github.com/user-attachments/assets/da7d5856-8df5-4f0f-97f0-579b71f874a4" />

## L6 Drain current model for saturation region of operation
In saturation region, the channel voltage will remain constant as 'Vgs-Vt', and the drain current will not depend on Vds. To get drain current equation in saturation region we will replace Vds as Vgs-Vt.

<img width="436" height="341" alt="39" src="https://github.com/user-attachments/assets/8e75b166-e53d-4a66-8a9e-f73cfb2243ed" />

According to the equation, the mosfet acts as perfect current source. But this is not true, when we increase Vds we will that Depletion region at drain increases and so channel length further reduces.Therefore, we see a slight dependency of Vds over Id. This is called "Channel Length Modulation".

<img width="1237" height="528" alt="40" src="https://github.com/user-attachments/assets/d061ba95-3790-420f-80d9-b8f0b1f7fa7c" />

<img width="816" height="154" alt="41" src="https://github.com/user-attachments/assets/379662a2-356f-4ea9-8c7f-0838e2c5a422" />

## Introduction to SPICE
## L1 Basic SPICE setup
The encircled parameters arwe called spice model parameters. These may or may not be constants.

These are directly coming from the foundary, we don't need to derive them.

<img width="870" height="501" alt="44" src="https://github.com/user-attachments/assets/e64c6e0a-b490-480e-8f03-c22ed75d8a83" />

<img width="235" height="441" alt="Screenshot 2026-06-05 073458" src="https://github.com/user-attachments/assets/0da35745-2eb2-4e92-9551-f389b299443d" />

## L2 Circuit description in SPICE syntax
To define a spice netlist :

firstly nodes are identified

<img width="571" height="361" alt="46" src="https://github.com/user-attachments/assets/284e0b7b-d975-452b-8386-7d73cee319b6" />

Then,nodes are named and code is written.

SPICE Netlist 

<img width="780" height="352" alt="Screenshot 2026-06-05 074743" src="https://github.com/user-attachments/assets/a1afcf49-dd7f-4473-8e0d-5c9e38acc8bb" />

## L3 Define technology parameters
Now we will look for model of this particular NMOS. For this we have model paramters, and it becomes easy to model from the parameters. That is where the technology file comes into picture. The models for the name NMOs will be found in file which has the attribute of the similar name.

<img width="1187" height="573" alt="61" src="https://github.com/user-attachments/assets/9307f6ce-5dd0-4c2c-bb95-d48814e71deb" />

Inside the brackets, technology paramteters will exist. Similarly for pmos also.

<img width="499" height="74" alt="62" src="https://github.com/user-attachments/assets/4471cdaa-80a2-4952-9c08-d547b7de07e9" />

Now, we just plug in this packaged file in .mod file and call this file in top level SPICE netlist.

<img width="509" height="456" alt="63" src="https://github.com/user-attachments/assets/e5562d28-a5de-4232-b313-c26055040df8" />

<img width="576" height="176" alt="64" src="https://github.com/user-attachments/assets/986fbd74-e39c-4a49-a637-b8cbf7c8bb8e" />

In the below image, the highlighted part is comment in SPICE.
Now, we need to sweep the Vgs and Vds for SPICE simulations.

<img width="565" height="239" alt="65" src="https://github.com/user-attachments/assets/9e79ba3c-44cc-40bb-b4f6-ab4e35db433d" />

## L4 First SPICE simulation

<img width="1002" height="548" alt="image" src="https://github.com/user-attachments/assets/c30db3cc-4084-428b-b2ec-30e9b17239ab" />

<img width="953" height="564" alt="image" src="https://github.com/user-attachments/assets/6161ec76-5d1e-4b19-92f0-3bcb74e8ce8a" />

<img width="867" height="679" alt="image" src="https://github.com/user-attachments/assets/cc5e2e7a-6706-4a3f-998e-1a3786a5ebff" />

To check the value of Id for corresponding Vds and Vgs, just left click and see.

<img width="292" height="125" alt="Screenshot 2026-06-05 080253" src="https://github.com/user-attachments/assets/506470b5-cec5-42d9-bc9a-ea747aab9246" />




# NgspiceSky130-Day2-Velocity saturation and basics of CMOS inverter VTC
## SPICE simulation for lower nodes and velocity saturation effect
## L1 SPICE simulation for lower nodes
This curve is from previous SPICE simulation in which Id is at y-axis and Vds is at x-axis

<img width="1219" height="733" alt="Screenshot 2026-06-05 082454" src="https://github.com/user-attachments/assets/10446a2f-2cc6-47d3-930e-314be5bbfd50" />

the above graph the area left of curve; Vds=Vgs-Vt is Linear region as current is increasing linearly, the area right is Saturation region with slight increase in current due to velocity saturation and below is the Cut off region.Also this case is when the channel length is large.

Now we are taking different W and L, but the ration of W/L is same as previous, so the Id should not change. But this is not the case practically.

Below is the spice deck, where only the values of W and L is changed, rest everything remains same.

<img width="787" height="486" alt="Screenshot 2026-06-05 083333" src="https://github.com/user-attachments/assets/d164e057-a7fe-40cd-8d80-1c258515bea6" />

## L2 Drain current vs gate voltage for long and short channel device
Now we are comparing between Long and Short channel device

<img width="1341" height="715" alt="Screenshot 2026-06-05 082845" src="https://github.com/user-attachments/assets/6d0fe567-63ec-4d3f-b8b5-3946e808be0f" />

Some of the observations are:
1. If we see Id values for different Vgs and for Vds=2.5V, there is a quadratic dependency of Id on Vgs. Whereas for short channel device, at Vds=2.5V, the current is increasing linearly due to velocity saturation.

<img width="1350" height="735" alt="Screenshot 2026-06-05 085153" src="https://github.com/user-attachments/assets/c4390ca0-2275-4861-82df-d2a1eae3bcbe" />

Now we will plot graph of Id vs Vgs and sweeping Vds or keeping Vds constant = 2.5V.

<img width="788" height="491" alt="Screenshot 2026-06-05 091608" src="https://github.com/user-attachments/assets/4f4dba9b-5359-478c-884d-a39203f5a998" />

syntax explains that what will be there on left hand side will be sweeped at every value on right hand side. For example here for every value of Vdd, Vin will be sweeped. The plot we get is quadratic, it is only when Vds=2.5V 

<img width="554" height="442" alt="Screenshot 2026-06-05 091641" src="https://github.com/user-attachments/assets/ee39e779-6ccd-4600-a80e-f5c3984aedd3" />

velocity saturation: is a phenomenon that occurs in short-channel MOSFETs when the electric field in the channel becomes very high.

<img width="1357" height="668" alt="Screenshot 2026-06-05 090333" src="https://github.com/user-attachments/assets/0f81471d-5f82-4030-9530-1a67e5abb93f" />

## L3 Velocity saturation at lower and higher electric fields
For short channel we will see more of a linear behaviour as the Vgs increases. This is due to velocity saturation effect.

<img width="986" height="488" alt="Screenshot 2026-06-05 092209" src="https://github.com/user-attachments/assets/a756b1e8-ceb5-40b1-b728-13c93aae4edf" />

We know velocity and electric field are related to each other with equation v=uE, where v is velocity, E is electric field and u is mobility. Velocity increases linearly with electric field over certain electric field value after which it gets saturated. This is due to scattering at higher fields and mobility decreases. 

<img width="891" height="471" alt="Screenshot 2026-06-05 092308" src="https://github.com/user-attachments/assets/4cc40e7b-d9f5-4d4e-b479-eb8960d22551" />

Velocity saturation happens for higher gate-source voltages.

<img width="925" height="438" alt="Screenshot 2026-06-05 092332" src="https://github.com/user-attachments/assets/119799a3-a545-4a39-8ca2-20de74831052" />

<img width="949" height="418" alt="Screenshot 2026-06-05 092410" src="https://github.com/user-attachments/assets/fa7b0b01-5235-463b-9931-8d87687fc1b3" />

## L4 Velocity saturation drain current model
Let us take Vgs-Vt=Vgt because we will be taking Vgs as large values. Current equation we will be using as shown above, For lower values of Vds we will neglect the 'lambda' term.

There is one more technology paramter which is "Vdsat", it is the velocity of gate when the device just enters the Velocity saturation region.

<img width="820" height="190" alt="Screenshot 2026-06-05 092923" src="https://github.com/user-attachments/assets/2823e681-b37d-4051-834c-3d8dde8bbdd9" />

Saturation region:

<img width="995" height="523" alt="Screenshot 2026-06-05 092959" src="https://github.com/user-attachments/assets/14c3f128-99e2-48b8-9417-bb8b7067277d" />

Resistive region:

<img width="1043" height="526" alt="Screenshot 2026-06-05 093011" src="https://github.com/user-attachments/assets/3ac59572-cdd7-4f0a-85f7-fc9a6473c67b" />

Veocity Saturation region:

<img width="1200" height="573" alt="Screenshot 2026-06-05 093057" src="https://github.com/user-attachments/assets/c49219dc-7a8b-4e9d-86ae-21bb3da75ec5" />

In the above equation, it seems when W is constant and L is lowered then Id should increase, But it is not so practically.

Observation 2 - The saturation current for lower nodes is low instead of being high. This is because Velocity saturation tends to saturate the device early so the peak current we see for lower nodes is much lesser than for higher nodes. 

<img width="1274" height="561" alt="Screenshot 2026-06-05 093531" src="https://github.com/user-attachments/assets/545421cc-182c-4f35-916a-7b36d9db1d55" />

## L5 Labs Sky130 Id-Vgs


## L6 Labs Sky130 Vt


## CMOS voltage transfer characteristics (VTC)
## L1 MOSFET as a switch
We will now look at the device parameters from the switch point of view.

<img width="877" height="360" alt="Screenshot 2026-06-05 094159" src="https://github.com/user-attachments/assets/29bfcea8-0d15-41ea-bc35-ea7afa029b56" />

When |Vgs|<Vt, device is OFF and it acts as open switch
When |Vgs|>Vt, device is ON and it acts as closed switch

<img width="1082" height="591" alt="image" src="https://github.com/user-attachments/assets/4ab676ad-bf29-42e3-bddd-438e51d3ed40" />

## L2 Introduction to standard MOS voltage current parameters








































