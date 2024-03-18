# [0xx][bit net] BitNet: Scaling 1-bit Transformers for Large Language Models
## Overview
* Authors: Hongyu Wang, Furu Wei
* Affiliations: Tsinghua University
* Publication Venue: CL 2023 
* Link: [https://arxiv.org/abs/2310.11453](https://arxiv.org/abs/2310.11453)
## Summary: 
### Problem:
- The energy consumption of training and inference of LLM is significant
### Key idea: 
- replace Linear layer in transformer by BitLinear.
  - The weight is in one bit format (i.e. Matrix multiplication in QKV generation are in 1 bit mode {1,-1}, which avoid multiplication)
  - Other components are in 8 bit format.
  - Apply absmax quantization

### Takeaways: 
- What we can do 
  - This paper only has a general assumption of nenrgy consumption.(i.e. only MUL and ADD are simply accumulated according to matrix dimension)
  - We are looking for a good method to reduce the compution in generation as welll as the transmission of weight.
  - Is it possible for us to marge our projection for score sparsity prediction with the bitlinear layer?

