# [0xx][ONN][MRR] CrossLight: A Cross-Layer Optimized Silicon Photonic Neural Network Accelerator
## Overview
* Authors:
* Affiliations: 
* Publication Venue: 
* Link: []()
## Summary: 
### Problem:
- Fabrication process and thermel variation adversely affected the robustness of photonic accelerator.
    - crosstalk in thermal and noise limited the resolution(accuracy) and scalability
    - Process variation introduces resonant drift.
        - Compensation with EO(electro-optic) is faster and energy cheap, but has a small adjust range
        - Compensation with TO(thermo-opti) has higher power and lantency with large adjust range.
    - As MRR number and wavelength numbers increase introduce noise due to crosstalk and splitter loss.

### Background
- Noncoherent photonic accelerator
    - Broadcast and Weight protocol, which use WDM, photonic multiplexors and photodetectors.
    - Aplly MR to weight optical signals. 
- Coherent photonic 
    - manipulate electrical field amplitude rather than signal power, typically use single wavelength.
    - Apply amplitude attenuation proportional to the weight value to weight the signal.
    - coherently accumulated by cascaded Y-junction combiners.

### Key idea: 
- Archs
    - Digital to DAC to MR arrays. 
    - Use MR to modulate both act and wgt
    - Use two seperate unit to do FC and CONV
    - 
- found the MR parameters which could lead to least resonant drift
    - Found that in an MR design of any radii and gap, when the input waveguide is 400 nm wide and the ring waveguide is 800 nm wide at room temperature (300 K), the undesired ΔλMR due to FPVs can be reduced from 7.1 to 2.1 nm (70% reduction).
- Apply TO EO hybrid compensation and apply TED to further cancel the thermal crosstalk.
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments
