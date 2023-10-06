# [0xx][Structured sparsity]HighLight: Efficient and Flexible DNN Acceleration with Hierarchical Structured Sparsity
## Overview
* Authors: Yannan Nellie Wu, Po-An Tsai
* Affiliations: MIT
* Publication Venue: MICRO2023
* Link: [https://doi.org/10.48550/arXiv.2305.12718](https://doi.org/10.48550/arXiv.2305.12718)
## Summary: 
### Problem:
- For medium/high sparsity DNN, the unefficient operation on zero valuse should be avoided, while for low sparsity DNN, the additional sparsity overhead should be as low as dense DNN.
- Sparsity degree should be flexible enough to be amenable to diffenrent models.
- Unstructed sparsity is less efficient while structured sparsity is less flexible.
### Key idea: 
- Fibertree abstract.
    - A tensor can be represented by a tree-based model. Sparisity pattern can be represented by removing coordinates in different rank of the tree.
    - Most Previous Sparsity only apply sparsity on **one rank** 
- Hierarchical structurd sparsity(HSS)
    - To make sparse ratio more flexible, the paper applyed sparsity on multiple ranks.
    -  The sparsity is first applied on lower rank than on the higher rank. 
    - Multiple the sparse rate in each tile will get a very flexible sparse ratio.
- HighLight
    - Use Skip and CP to implement the SAFs.
        - Use two level piplined mux * 4 to implement the selection of efectual value. 
    - Use more ranks reduce the heirarchys per rank. (2:16 -> 2:8 2:4)
    - High level architecture
        - 1024 MACs into 4 PEs
        - 2 ranks HSS with skipping SAFs
            - To make sure the the skipping unit could fit in the different sparse ratio, the variable fetch management unit is applied. 
    - B sparse
        - three dimension metadata: numbers of non-zeros blocks; end address of each block; value offset inner block. 
        - apply gating to B(activation) sparsity.

### Strengths: 
- The idea of do sparsity in different hierarchy do decrease the length of operands rows to do MUX, which means large MUX was broken down and could be piplined.
### weaknesses: 
- This idea need CP to ensure its multi-hierarchical sparsity, for bitmap could not tell the MUX which higher rank block should be skip. However, when the sparse ratio is not high, the CP method will largely increase the harware overhead. This method only fit matrix with high sparsity
- The microarchitecture of this work need the num G of G:H to be fit with MACs, that means, if the architecture is configured to work on 3:8 and 2:4, then, there should be at least 3 MACs should be work at same time. If 2:4 is applied, one MAC will be idle all the time unless split the fiber of the tree. 
