# [0xx][transformer train]TransCODE: Co-Design of Transformers and Accelerators for Efficient Training and Inference
## Overview
* Authors: Shikhar Tuli, Niraj K. Jha
* Affiliations: Princeton University
* Publication Venue: TCAD 2023
* Link: [https://arxiv.org/abs/2303.14882](https://arxiv.org/abs/2303.14882)
## Summary: 
### Problem:
1. Previous work most focus on inference acceleration. However transformer training demand higher memory footprint, especially on edge AI devices.
2. The design space of transformer are mostly designed for a specific model. More PE would cause high parallelization in shallow and wide model, however low utilization for deep and narrow network.
3. Different design space of accelerator lead to different result.
For shallow and wide models, more PEs could bring high parallelization and low latency.  But requires high bandwidth and more computing resources. For deep and narrow models, too many PEs would cause low utilization. Previous design space research work mainly focus on CNNs. (NAAS, CODEBench)

### Key idea: 
1. DynaProp
    - Prune the weight activation and gradients matrix before operation
   - Set a theshold and prune the value less than threshold.
   - Threshold is determined by the desired sparse ratio and get through look up at runtime.
2. ELECTOR
    - Hardware module
        1. Main memory 
            - off-chip DRAM for scalable and economical application
            - on-chip HBM for memory-intensive edge/server application
            - on-chip monolithic 3-D RRAM

        2. control block
            - do tiling works and schedule each tile to PEs.

        3. PEs
            - Compressed data -> DynaProp-> Sparse matrix and mask
            - Sparse matrix -> Precompute Sparsity module-> zero-free data
            - Zero-free out -> Postcompute Sparsity module-> Sparse matrix

    - Transformer mapper
        1. Self-attention
            - How much one token attends to another token.
        2. Linear Transformer
            - This operation implements an LT on the input sequence
        3. Dynamic-span-based-convolution  
            - The DSC operation implements a 1-D convolution over the input.
    - Design space
        1. Convert these hyperparameters into a 12-D vectors.
        2. Training a surrogate model by these vectors to output the subsequent query as an accelerator embedding   

3. TransCODE
- Leverage ELECTOR and FlexiBERT 2.0 design space to implement co-design.

### Takeaways: 
- The workflow could be applied in several of our work area. The photonic design choice and hyperparameters has larger effect on the performance of system.
- The pruning of gradients seems make sense on edge devices or devices for vision tasks. However, for most situation the loss during training will aggregate, if the network is exetremely deep.
