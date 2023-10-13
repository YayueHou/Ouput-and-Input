# [004][approximation]DOTA: Detect and Omit Weak Attentions for Scalable Transformer Acceleration
## Overview
* Authors: Zheng Qu, Liu Liu
* Affiliations: UCSB 
* Publication Venue: ASPLOS 2022
* Link: [https://dl.acm.org/doi/abs/10.1145/3503222.3507738](https://dl.acm.org/doi/abs/10.1145/3503222.3507738)
## Summary: 
### Problem:
- Transformer need unique strong connection detection methods for its attention matrix.
- The detection of strong connection is either costly or inaccurate.
### Key idea: 
- Weak attention detection
    1. Use the linear transformation to get lower-rank matrix than the original Q, K, V. 
  $$Q, K= XP\tilde{W_Q}, XP\tilde{W_K} \\
        P\in \sqrt{\frac{3}{k}} \{ -1,0,1\}^{d\times k}
     $$
    2. Use the $\tilde{QK^K}$ to detect weak attention. The output $QK^T$ and $\tilde{QK^K}$ would have the same shape. So the mask of $\tilde{QK^K}$ can also be used in  $QK^K$ directly.
    3. Use mean squared error to optimize low-rank transformation parameters. 
- DOTA
    - Reconfigurable Matrix Multiplication Unit
        - This RMMU support multi-precision by using the $(a+b)(c+d)=ab+ac+bd+bc$, split a fix-point operand into several lower precision and add them together.
        - The attention detector use lower precision and real calculation in QK use FX16 and dequantized to FP32 to scaling and softmax. Finally being requantized to FX16 before QKV.
    - Dataflow
        - Reschedule dataflow to balance the workloads.
### Takeaways: 
- The workload balance may exist in all unstructured pruning. 
### Strengths: 
- The approximate method to pre-calculate the mask is novel and usedful
- The configurebale MMU is significant when co-design with the approcimate method
### weaknesses: 
- The work load balance module will introduce additional overhead

