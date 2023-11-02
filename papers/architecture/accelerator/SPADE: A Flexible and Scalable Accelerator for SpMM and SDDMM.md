# [0xx][MatMul Accelerator]SPADE: A Flexible and Scalable Accelerator for SpMM and SDDMM
## Overview
* Authors: Gerasimos Gerogiannis, Josep Torrellas
* Affiliations: UIUC
* Publication Venue: ISCA2023
* Link: [https://doi.org/10.1145/3579371.3589054](https://doi.org/10.1145/3579371.3589054)
## Summary: 
### Problem:
- Data reuse behaviour heavily depends on the input sparse matrix structure.
- Moving data between accelerator and CPU has large overhead.
- SDDMM and SpMM has less flexibility.
- SIMD for SpMM and SSDDMM are difficult to apply due to the irragular sparse memory access.
- GPU kernal execution is faster while CPU is faster when transfer overhead take into consider.
  - GPU support a virtual address shared with CPU which is inefficient  
### Key idea: 
- SPADE
    - Tight integration 
        - Each CPU core has 1-4 SPADE PE tighttly integrated with it.
        - CPU and PE share same STLB L2 cache and clock. (PE is 1/4 clk freq of CPU)
            + Bypass buffer optionally allows PE bypass L1 cache to perform more efficiently.
            + The program interleave CPU execution section and SPADE execution section. Before change to SPADE mode, the pages of matrix data structures are pinned in physical memory.
            + Before Transfer from CPU mode to SPADE mode the L1 cache of CPU is written back to L2 cache. Any data area that would be accessed by SPADE need written back to memory and invalidate from cache.
            + Before SPADE to CPU, SPADE L1 write back to L2 and invalidated, BBF written back to main mem and invalidate.
    - CPE control the PE to operate using an input register. When CPU run, SPADE pause, when SPADE run CPU pause. 
    - Programability
        1. Instruction sent to PEs are tile level instruction.
        2. Before instruction are fenerated, input matrix and several parameters are analyzed.
        3. At run time, CPE take layout of tiled matrix and generate the instruction for PEs.
            1. Initialize: Arguments initialize basic parameters such as size, addr, cache bypass.
            2. Tile: Arguments take info of NNZ start and end position and numbers.
            3. Scheduling Barrirt Instruction: Schedule the process align the column. (same as reuse the activation column)
            4. WB&Invalidate Instruction: Write back (L1 to L2, BBF to main memory) and invalidate L1 and BBF.
            5. Termination Instruction: SPADE pause.
    - Pipline
        1. sparse front-end: Get all information to load data. Fetch data to L1, generate the address of rows needed.
        2. vOp Generator: Allocate two VRs for two operands and load the data from memory.
        3. dense back-end: Dispatch operation in to piplined SIMD unit. Store result in VRF. Write back periodically to memory.
### Takeaways: 
- Consider the accelerator operation and CPU performance together is important. For the data fetch, transfer and instruction decompression dominate the overhead of the whole system.
### Strengths: 
- Use instruction in tile level and decompress in PE, this enale simple control of operation and SIMD implemention
### weaknesses:
- Access to L2 directly is slower and more energy cost compered with L1, however pages and cache miss also cause latency. This is a trade off.
