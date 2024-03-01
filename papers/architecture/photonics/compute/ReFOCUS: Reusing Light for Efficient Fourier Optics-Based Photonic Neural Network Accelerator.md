# [0xx][Fourior optics] ReFOCUS: Reusing Light for Efficient Fourier Optics-Based Photonic Neural Network Accelerator
## Overview
* Authors: Shurui Li, Puneet Gupta
* Affiliations: UCLA
* Publication Venue: MICRO 2023
* Link: []()
## Summary: 
### Problem:
- Free-space photonic neural network accelerator
    - Those kind of accelerators are often bulky and inflexible.
- On-chip photonic neural network accelerator
    - MZI and MRR based accelerators
        - The major bottle neck of such kind of accelerator is the conversion between digital and analog domian.
        - These accelerator achieves a low compute-to-conversion ratio due to the small arrary size because of relatively larger photonic components and limitation of WDM.
    - Directly computing accelerator
        - Fourior optics. 
            - Traditional Fourior transform pays a lot for the fourior filter, which has both real-valued part and complex-valued part. (complex filter is expensive)
            - The length of fourior filter should be as same as the input 
        - JTC accelerators
            - JCT can get the co-transform of two signals with two lens and a non-linear unit in middle of them. 
            - The output consist of two convolution result and one non-convolution result which could be shifted off
            - Challenges
                - the lenses on-chip could be only 1D, which could not support the CNN usually in 2D convolution. This will affect the accuracy.
                - The result of JTC is divided in to two convoluion part. Each calculation only pick up one of them to generate the result of computing. This causes redundency.
                - The nonlinear part of JTC is implemented by MMR which has undesired overhead and non-linear material is not mature enough.
                - E-O O-E
                -  
### Key idea: 
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments
