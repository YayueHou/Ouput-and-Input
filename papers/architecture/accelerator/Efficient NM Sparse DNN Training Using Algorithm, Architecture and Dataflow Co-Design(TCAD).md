# [016][N:M sparse]Efficient N:M Sparse DNN Training Using Algorithm, Architecture, and Dataflow Co-Design
## Overview
* Authors: Chao Fang, Wei Sun, Aojun Zhou, Zhongfeng Wang
* Affiliations: Nanjing University
* Publication Venue: TCAD 2023
* Link: [10.1109/TCAD.2023.3317789](https://ieeexplore.ieee.org/document/10256041)
## Summary: 
### Problem:
- SOTA DNN has peta-level floating point operations for training process.
- Structured sparse has less sparse ratio, while unstructured sparse has high hardware overhead.
- There are several challenges/oppotunities to optimize N:M sparse.
    - N:M is only be implemented in backward/forward before but not in bidirection
    - The N:M is limited in N:M patterns and if leaverage before inference the N elements need to be update leading to computational overhead.
    - Dataflow optimization is need to improve hardware utilization and speed up
### Key idea: 
- Bidirectional N:M sparse trainig BDWP
    - Caculate the N:M weight at the beginning of forward pass, and only used sparsed W in FP
    - Sparse W before caculate gradiant, only update W that the gradient is calculated.
- Hardware SAT
    - N:M sparse tensor computing engine
        - Support both dense and sparse matmul.
    - Flexible Systolic Interconnect
        - Can switch between OS and WS dataflow by change the interconnect method of  systolics.
    - Weight update vector engine
        - Mixed precision scheme of NVIDIA AMP
        - Exchange FP16 to FP32 and after several calculation, change it back
    - Sparse online reduction engine
        - 32 parallel lanes with a SORE in each lane.
        - A SORE contains a top-k sorter and a data provider.
        - M cycles is need for one N:M operation.
        - Compare a value with M values in stack, if large, replace one in stack with it. 
    - Dataflow Optimization
        - Apply interleaving mapping method to fill the pipline and avoid waiting for stall.
        - Perform the forward pass with FP16 until update the weights.
        - Pre-generate the N:M values to hide latency
### Takeaways: 
- Except the pruning algorithm, this paper has many novel idea, such as configurable dataflow.

###	Strengths: 
- Use the pre-generate method to reduce the cycles.
- Though hardware overhead, configurable dataflow brings more oppotunity to reuse data in different layers.  

###	weaknesses: 
- The flexible in stationary methods introduced registers to store partial values or weight. In WS mode, higher sparse ratio means more register, and the waste of registers in OS mode.
- The N:M reduction engine need M cycles to finish the pruning. For it nearly sort all the values in the M group. 
###	How can you do better:
- Use our method to improve N:M pruning.
                                                              