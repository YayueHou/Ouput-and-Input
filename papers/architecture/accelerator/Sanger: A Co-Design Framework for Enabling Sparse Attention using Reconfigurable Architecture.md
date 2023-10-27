# [0xx][Transformer Acceleration] Sanger: A Co-Design Framework for Enabling Sparse Attention using Reconfigurable Architecture
## Overview
* Authors: Liqiang Lu, Yicheng Jin, Yun Liang
* Affiliations: Peking University
* Publication Venue: 2021 MICRO
* Link: [https://doi.org/10.1145/3466752.3480125](https://doi.org/10.1145/3466752.3480125)
## Summary: 
### Problem:
- Algorithm
    1. Dynamic sparsity cannot be pre-determined before inference and varies among samples.
    2. Non-zeros in softmax is implicit
- Hardware
    1. Dynamic sparsity are usually highly unstructured. 
- Structured sparse such as SpAtten still has redundency and lack of sparsity.
- Unstructured sparse would cause workload irregularity.
- Some work only contain software optimization without hardware optimization.
### Key idea: 
- Software
    - First quantize Q and K to 4-bit and compute low-bit $\hat{S}$
        - Use symmetric linear quantization as quantization operator.
    - Extract implicit sparsity from $\hat{S} = softmax(\mathbb{Q}^{-1}(\mathbb{Q}(Q)\mathbb{Q}(K)^T)\sqrt{d})$ using a threshold T and output a bitmap M.
- Compression
    - Partition the M into sub-matrix.
    - Pack by skipping zero only rows.
    - Split the packed sub-rows to structured blocks. Each block has similar number of non-zeros.
- Hardware
    - Score-stationary.
        1. Q sent in row and K sent in column, calculate each K with a Q (like outer-product)
        2. Each PE conducts an exponential operator to prepare for softmax operation.
        3. Store the MAC result in PE and accumulate it in each iteration. (Score-stationary)
        4. Deivide the reault of all PEs by sum of exponential operator to normalize in softmax function.
    - Sparse score stationary
        - Insert bubble between PEs, which only stall data for one cycle.
    - Reconfigurable SpMM and SDDMM
        - Store data densely in registers and full connect the PEs to all registers
        - Use MUX to select input source(QK/SV)
### Takeaways/drawbacks.
- The full connection of PEs and registers will introduce a large hardware overhead.
- I am thinking about how to not do full connection to PE and at the same time keep a high sparse ratio flexibility.
- Also, the bubble PE only decrease the energy but not decrease the latency.
