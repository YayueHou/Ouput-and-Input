# [0xx][transformer accelerator][token pruning] SpAtten: Efficient Sparse Attention Architecture with Cascade Token and Head Pruning
## Overview
* Authors:
* Affiliations: 
* Publication Venue: 
* Link: []()
## Summary: 
### Problem:
### Key idea: 
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments:
1. SpAttn performs progressive token pruning and head pruning from layer to layer to reduce the cost of self-attention as well as the general cost of later layers [19]. It requires designing a very specialized top-k selection engine. -- https://ieeexplore.ieee.org/abstract/document/10247993
2. SpAtten [14] proposes the top-k pruning algorithm that ranks input token and attention-head scores using a dedicated hardware module. However, it only considers part of the activations formed, not sparsity in all possible matrix multiplication operations.--TransCODE
3. SpAtten [15] leverages a cascade token pruning mechanism that progressively prunes unimportant tokens based on low attention probabilities, reducing overall compute complexity. However, the proposed “top-k ” pruning mechanism [15], a state-of-the-art hardware-aware dynamic inference method, has a high compute overhead, which partially offsets its throughput gains during model inference according to our experiments (details in Section V-A) --AccelTran
4. SpAtten [36] proposes cascade token pruning and head pruning to reduce the cost of both self-attention block and subsequent layers. While removing several rows and columns of the attention matrix makes the operation regular and hardware-friendly, we find this constraint to be too aggressive as the locality of attention weights usually exists in small granularity. --https://ieeexplore.ieee.org/abstract/document/9896137
5. SpAtten [57] performs structured activation pruning by removing entire attention heads and tokens. However, the remaining heads and tokens may still contain redundant attention, leading to low sparsity. -- Sanger