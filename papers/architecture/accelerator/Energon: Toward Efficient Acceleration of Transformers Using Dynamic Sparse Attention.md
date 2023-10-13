# [0xx][transformer accelerator] Energon: Toward Efficient Acceleration of Transformers Using Dynamic Sparse Attention
## Overview
* Authors: Zhe Zhou, Junlin Liu, Zhenyu Gu
* Affiliations: Peking University
* Publication Venue: TCAD 2023
* Link: [https://arxiv.org/abs/2110.09310](https://arxiv.org/abs/2110.09310)
## Summary: 
### Problem:
- In transformer, attention calculation dominate the overhead of latency and energy.
- The current solution either non-dynamic or could not acheive acceptable accuracy.
    - A^3 only save computation but not reduce DRAM access
    - SpAtten don't support dynamic pruning
### Key idea: 
- MP-MRF
    - Select keys in filter round which use a threshold to filter lower-precision values.
    - Fisrt, apply extremely low bitwidth to compute Q*K^T and select large attention scores.
    - Next, increase the bitwidth to filter out high attention scores from remain K-Q pairs, until the accuracy is acceptable
    - Use mean value of a row as threshold instead of sorting.
    - Set a parameter to introduce a offset to threshold to get reconfigrable sparsity ratio.
    - Apply multi-precision quantization. INT16, INT4 and INT2 are all supported.
- Energon co-processor architecture
    - Filter Unit
        - QK and V are stored in INT4 and INT16 seperately. Q,K first sent to filter and sent the indices to Attention unit to calculate the atention scrore in high precision.
        - Use INT4xINT2 and INT4xINT4 in first and second iteration. The max, min and mean of a row is calculated seperately by three thread and get the threshold which is sent to selector to get indices for high-precision calculation.
    - Attention Unit
        - In AU, high precision K and Q are producted, scaled and buffered. 
        - Then QK^T are sent into softmax and finally calculte QK* V
    - Performance Model
        - K V load cost t_load is calculated based on the bandwidth and needed data
        - MAC cost t_comp is calculated based on pruning ratio and output numbers and query length.
        - t_load/t_comp is used to evaluate the pipline efficiency
### Takeaways: 
- The performance model is novel and efficent.
### Strengths: 
- This method first fetch Low precision value from DRAM. In next iteration the higer precision value are not all refetched from DRAM but only the missed one are refetched. which reduced the access to DRAM
- The extremely low precision could reduce the calculation overhead of mask.
### weaknesses: 
- Though retrain is not required, the iteration is inevitable.
- The divider in mean calcultion may be much more time consuming than sorting. 
