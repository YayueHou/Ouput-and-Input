# [0xx][ONN][MZI] Deep learning with coherent nanophotonic circuits
## Overview
* Authors: Yichen Shen1, Nicholas C. Harris
* Affiliations: MIT
* Publication Venue: Nature 2017
* Link: [https://www.nature.com/articles/nphoton.2017.93](https://www.nature.com/articles/nphoton.2017.93)
## Summary: 
### Problem:
- Implement photonic ONN is difficult by bulk photonic devices.
- Opportunity 
    - ANN Matmul is fixed
    - Weak requirements on non-linearity
    - Architecture could be passive hence no energy consumption.
### Key idea: 
- SVD
    - implement a OIU(optical inference part)
        - U and V* are implement by optical beamsplitter
        - $\Sigma$ is implemented by optica attenuators.
    - ONU(optical nonlinearty unit) is implemented by saturable absorption and bistablity.
- Implement
    - Program MZI (directly program U and V on the device)

### weaknesses and takeaways:
- From other citations
    - The MZI should be programmed previously which limited the matrix to be more static
- From discussion, it has a low accuray due to the limited resolution
        1. thermal crosstalk (phase shifter in interferometers is controled by thermal)
            - Is there any photoic device which has similiar out, but could be controlled by voltage?
        2. Optical drift
        3. Finite precision of optical phase
        4. Photodectection noise.
        5. Finite photodetection noise
- The low energy consumption only exist when weight is pre-trained and placed on device. The cost of programming the MZI is not shown.

### Comments
