# [0xx][vision transformer acceleration] ViTCoD: Vision Transformer Acceleration via Dedicated Algorithm and Accelerator Co-Design
## Overview
* Authors: Haoran You, Zhanyi Sun
* Affiliations: gatech
* Publication Venue: HPCA 2023
* Link: [https://arxiv.org/abs/2210.09573](https://arxiv.org/abs/2210.09573)
## Summary: 
### Problem:
1. ViTs have fixed number of input tokens during both training and inference, hence there are oppotunities to avoid on-the-fly sparse attention pattern prediction.
2. ViT allows high sparse ratio which aggravate the irregular data access and processing, which lead to utilization problem. Moreover, the non-zero elements concentrate along the diagonal lines of matrix, which is exetremely unefficient pattern.

### Key idea: 
- Algorithm: Split and Conquer Algorithm
    1. pruning: apply fixed mask which is extracted according to the criterion of the pruned messages.
    2. workload balance: divided the Q/K pairs into dense and sparse part. The K has strong relationship with all Q is sent into dense part and the remain part is sparse part.
- Hardware: Auto-encoder Module
    1. Use a encoder to compress the input data according the dimension of head before move data from DRAM to off-chip memory
    2. decoder the data after movement finished.
    - has lost and funtuning is needed to recover the lost.
### Takeaways: 
- The encode and decode make sense but nothing novelty
- The research on non-zero distribution in ViT is important because structured pruning performance worse in ViT 
### Strengths: 
- The taxonomy is clear
### weaknesses: 
- The divde of sparse and dense core will result in low utilization when the whole model is dense and FFN are not distributed as attention.
- overall, this work is too specific for attention layer in ViT.

### Comments
ViTCoD is the first co-design framework dedicated to accelerating sparse ViTs’ inference, offering a new perspective on efficient ViT solutions. -- author