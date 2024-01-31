# [0xx][photonic interconnect] POPSTAR: a Robust Modular Optical NoC Architecture for Chiplet-based 3D Integrated Systems
## Overview
* Authors: Yvain Thonnart, Ayse K Coskun
* Affiliations: Boston University
* Publication Venue: DATE 2020
* Link: [https://ieeexplore.ieee.org/document/9116214](https://ieeexplore.ieee.org/document/9116214)
## Summary: 
### Problem:
- Technology constraints
    1. geometric variability: Microring resonance has a huge dependence on silicon sickness.
        - It is possible to design a WDM Tx/Rx site with increasing MRR perimeters. Identical MRR perimeters may lead to totally different resonance in long distence propogation.
    2. Temperature sensitive: resonance would shift according to thermal variation.
        - resistive heaters are applied to arrange the temperature of ring to lock the MMR resonannce to the closest laser wavelength.
- WDM extention
    1. Trade-off exist between insertion loss and extinction ratio in PN-type MRR
    2. Trade-off exist between thru IL at rsonance and drop IL out of resonance.
    3. SWMR is better than MWMR and MWSR for optical budget. (cascading several PN rings tuned to the same waveguide os not scalable in terms of optical power budget. The jumps from thru port to drop port of several PIN rings for routing is neither impossible.)

### Key idea: 
- Use the spiral structure, which means the waveguide pass the Rx and with a inwards shift on the spiral to the next Rx row to avoid waveguide crossing.

### Takeaways: 
- This paper discussed the challenges and constraints that must be considered in photonic interpose design.


### Comments
1. "Though constructed by single-write-multiple-read channels, disable the broadcast capability."



