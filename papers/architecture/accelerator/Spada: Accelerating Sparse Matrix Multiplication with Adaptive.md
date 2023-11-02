# [0xx][MatMul Accelerator]
## Overview
* Authors: Zhiyao Li, Jiaxiang Li, Mingyu Gao
* Affiliations: Tsinghua University
* Publication Venue: ASPLOS 2023
* Link: [https://doi.org/10.1145/3575693.3575706](https://doi.org/10.1145/3575693.3575706)
## Summary: 
### Background
- SpGEMM is widely used in several fields
- SPGEMM could reduce ineffectual zeros (sometimes non-zeros), which save substantial storage and operation cost.
### Problem:
- Highly irregular structures
- Because SpGEMM is applied in various application domains, the accelerators need to support diverse sparse patterns. 
- Recent research only support SpGEMM to support a certain sparsuty ranges to best utilize their architecture. Core reason is the fixed dataflow in the optimizzation of MatMul.
### Key idea: 
- Dataflow
- Window-based Adaptive Dataflow

### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better: