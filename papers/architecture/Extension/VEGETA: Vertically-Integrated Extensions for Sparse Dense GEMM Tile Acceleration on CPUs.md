# [0xx][CPU extension] VEGETA: Vertically-Integrated Extensions for Sparse/Dense GEMM Tile Acceleration on CPUs
## Overview
* Authors: Geonhwa Jeong, Tushar Krishna
* Affiliations: GaTech
* Publication Venue: 
* Link: []()
## Summary: 
### Problem:
1. Though most DL tasks are offloaded to domain-specific accelerators and GPU, CPU are sometimes more efficiency and cheaper for edge devices and modest-size tasks.
2. Most work focus on dense GEMM but there is demand on sparse matrix multiplication.
3. Different with DMA:
    - General purpose CPUs are sensitive to hardware devoted to improving a subset of workload.
    - New functional unit CPU should be able to support a wide variety of use cases.
    - CPUs need programmability support to support sparsity unlike DMA engines.
4. Challenges:
    - Programmability: Size of unstructured sparsity matrics tiles is irregular.
    - Implementation overhead: index logic in RF or additional interconnect between PE lead to overhead. 
### Key idea: 
- Row-wise N:M sparsity: Tansfer unstructured dataflow to structured dataflow in row.
- VEGETA:
    - Define tile register, utile register and vtile register to support SpMM
        - treg are used to store compressed sparse data. Each tile is structured
        - ureg and vreg store dense data and has a size of M/N*sizeof(treg).
        - A series of instruction are designed for reg operation.
    - PEs
        - define two kind of PEs: Dense PU and Sparse PEs.
        - Dense PE are normal SA with WS
        - SPE has additional MUX. Weight are static and MUX select which input to stream.
        - Apply output forwarding to opt pipeline.
### Takeaways: 
- Add ISA to arch:
    1. Define registers
    2. Define operations
    3. Example algorithm.