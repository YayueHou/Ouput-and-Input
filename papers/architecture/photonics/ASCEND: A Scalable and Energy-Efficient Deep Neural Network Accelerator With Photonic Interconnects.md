# [0xx][photonic interconnect] ASCEND: A Scalable and Energy-Efficient Deep Neural Network Accelerator With Photonic Interconnects
## Overview
* Authors:
* Affiliations: 
* Publication Venue: 
* Link: []()
## Summary: 
### Problem:
- SOTA work only employ broadcast to facilitate cache coherence protocol or not fully exploit the broadcast of photonic interconnection. A novel photonic network which is tailored to DNN
inference and efficiently supports broadcast communication is necessary.
- Convetional metallic connection arch optimize based on data locality, which means only one operand is broadcasted. Phtonic interconnection has distance independent latency and ease of broadcast, which made it posiible to broadcast both Weight and Activition.

### Key idea: 
1. Novel Photonic Network:
    1. Unit 2D PE Array Architecture: 2*2 PE arrays. ifmap broadcast along columns and weight broadcast along rows.
    2. Wavelength Allocation: 4 wavelength are used to broadcast weight and are one-off. 4 wavelength are used to broadcast ifmap and are reused for PE-GLB unicast. 
   
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
