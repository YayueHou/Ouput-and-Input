# [0xx][bit net] The Era of 1-bit LLMs: All Large Language Models are in 1.58 Bits
## Overview
* Authors: Shuming Ma, Furu Wei
* Affiliations: Tsinghua University
* Publication Venue: CL2023
* Link: [https://arxiv.org/pdf/2402.17764.pdf](https://arxiv.org/pdf/2402.17764.pdf)
## Summary: 
### Problem:
- The transfer between SRAM and DRAM, the useage of SRAM are both expensive
- Previous Bitnet has no feature filter, which may not the optimal pattern of bitnet
  
### Key idea:
- Applied {-1,0,1} for weight representation instead of {-1,1}, and 8-bit activation.
- Applied absmean quant rather than absmax quant
- No normalization befor GeLU, instead use the nature property to avoid zero quantization.
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better:
### Comments
