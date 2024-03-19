# [0xx][matmul accelerator][reconfigurable dataflow] Flexagon: A Multi-Dataflow Sparse-Sparse Matrix Multiplication Accelerator for Efficient DNN Processing
## Overview
* Authors: Francisco Muñoz-Martínez, Tushar Krishna
* Affiliations: Universidad de Murcia, Spain
* Publication Venue: ASPLOS 2023
* Link: [https://arxiv.org/abs/2301.10852](https://arxiv.org/abs/2301.10852)
## Summary: 
### Problem:
- Previous work most focus on a specific dataflow. However, for DNN, the dataflow which has the best performance varies between layers.

### Key idea: 
- On-chip network
  - DistributioNetwork: Bense network with N-input N-output topology with several levels.
- Merger-reduction network 
  - A tree like structure:
    - each node could do both comparison and reduction.
    - In each step, the node could decide to merge the multiplication or only output one multiplication, while the another output wait for next output.
  - To save the compression decoding hardware overhead, the three compression pattern are reused among the execution. (the hardware contains the decoder for both CSC and CSR)
- Memory
  - read only FIFO, r/w cache and partial write SRAM

### Strengths: 
- The evaluation of cache though seems not to be the same level as the accelerator arch design, the consideration of this element is interesting.
### weaknesses: 
- The writing is hard to understand because the poor illustration figures.
- The impact of dataflow on accelerator is largely depends on local buffer size and tiling methods.
- According to my result, in some exetreme situation, one dataflow would achieve a outstading performance than others. However, if carefully configured, the three dataflow could achieve the same performance. Furthermore, the data distribution could also affect the performance of a accelerator. 
### How can you do better:
- The method of how to make the dataflow reconfigurable is not hard to find out. On contrary, how to decide which dataflow to use according to configuration is more important. 
- Though I think the hardware in SPADA is too completed compared with this paper, I think the reconfigurable dataflow in SPADA seems smarter than config the hardware.
### Comments
