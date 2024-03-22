# [0xx][butterfky sparse] Pixelated Butterfly: Simple and Efficient Sparse Training for Neural Network Models
## Overview
* Authors: Tri Dao, Christopher Ré
* Affiliations: standford university
* Publication Venue: ICLR 2022
* Link: [https://arxiv.org/abs/2112.00029](https://arxiv.org/abs/2112.00029)
## Summary: 
### Problem:
- The access of a single values has the same cost as accessing the block of the value, hence, regular data access is prefered. Original butterfly has a non block-alighed data access pattern, which seems unefficient.
- The flat butterfly is as expressive as the normal butterfly and better expressiveness than normal random pattern. Low-rank matrix are also needed to increase expressiveness
- The multiplication of matrix of factors are difficult to parallelize. Flat butterly replace the multiplication with addition.
### Key idea: 

### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments
