# [001][Energy Estimation]Accelergy: An Architecture-Level Energy Estimation Methodology for Accelerator Designs
## Overview
* Authors: Yannan Nellie Wu, Joel S. Emer, Vivienne Sze
* Affiliations: MIT
* Publication Venue: ICCAD 2019
* Link: [10.1109/ICCAD45719.2019.8942149](https://ieeexplore.ieee.org/document/8942149)
## Summary: 
### Problem:
- Accurate measure of energy can only be esmitmate nearly after layout which overheads many resources such as time.
- Early-stage estimation of energy is also needed. 
### Background
- Current Energy Estimation Methods
    1. **Component estimators**
        - Only focus on energy measurement on specific components such as SRAMs. (CACTI, Orion)
        - Though go deep into components, this method would lost holistic view of whole system.
    2. **Processor estimators**
        - Focus on processors which consist of fixed and limited set of components. (CPU,GPU,IPU,TPU)
        - The estimation is quick without generate low level evaluation, however lost flecxibility.
    3. **Design-specific energy tables**
        - Customized evaluation focus on specific design case
        - This method is exetremely design-specific. 

### Key idea: 
- 
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
