# [0xx][]
## Overview
* Authors:
* Affiliations: 
* Publication Venue: 
* Link: []()
## Summary: 
### Problem:
- Previous Research
    - Traditional accelerator based on digital eletronics face limit of Dennard scaling
    - Photonic computing alternatives like MZI array, MRR banks and PCM(Phase Change Material)-based crossbar only designed and optimized for weight-static NNs. They fail to efficiently support attention-based transformers.
- Challenges for transformer accelerators
    1. Transformers have MatMul with two dynamic input operands.
        - Previous photonic accelerators map one operand on device by program the device, which consumes time.
    2. Transformer matmul are in full range 
        - Previous incoherent PTC such as MRR constrained at least one operand to be non-negative.
        - Negative operands have to be decomposed into differences of non-negative operands which introduce additional accumulation.
- Key insight
    1. Mapping and device programming can dominate total latency for WS PTCs whose overhead can not be easily amortized
        - Optically encode both operands for dynamic switching.
    2. Incoherent PTCs use weighted light intensities to do multiplication which make supporting full-range matmul difficult.
        - Encode signs to extra phase dimension and perform signed computation via interference.

### Key idea: 
- 

### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments
