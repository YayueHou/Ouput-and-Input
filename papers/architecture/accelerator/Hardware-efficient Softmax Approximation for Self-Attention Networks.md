# [0xx][transformer accelerator][softmax]Hardware-efficient Softmax Approximation for Self-Attention Networks
## Overview
* Authors: Nazim Altar Koca, Chip-Hong Chang
* Affiliations: NYU
* Publication Venue: ISCAS2023
* Link: [https://ieeexplore.ieee.org/document/10181465](https://ieeexplore.ieee.org/document/10181465)
## Summary: 
### Problem:
1. There are far more softmax layers in attention than in DNNs 
2. The approximation applied in DNN such as log-sum-exp method escalates accuracy loss due to the cumulation of quantization errors in attention layer.

### Key idea: 
1. Algorithm: Use only shifter and adders to implement it.
    - Softmax + max normalization: $\sigma(z_i) = \frac{e^{z_i-z_{max}}}{\Sigma_{j=1}^Ne^{z_j-z_{max}}}$, let $z_i-z_{max}=y_i$
    - The denominator can be approximated to the nearest power-of-two integer value.
    - The $e^{y_i}$ can be approximated by $2^{1.5y_i}$ and $1.5y_i=(y_i+y_i/2)$ which means $y_i+y_i>>1$
    - Represent $2^{1.5y_i}$ by $2^{u_i+v_i}$ where $u_i$ and $v_i$ are integer and fractional part of $1.5y_i$ respectively.
    - for $v_i$ is in $[-1,0]$, $2^{v_i}$ can be approximated by $1+v_i/2$ which means $1+v_i>>1$, and $2^{u_i}$ is $>>abs(u_i)$
    - $\frac{(1+v_i>>1)>>abs(u_i)}{round(\Sigma_{j=1}^N (1+v_j>>1)>>abs(u_j))}$
2. The distribution of softmax output is like a right-skew distribution with a long tail of near zero values, hence it is possible to prune some softmax operation based on the mean value of inputs.
### Takeaways: 
- Though it decrease the latency, the main clock frequency is decrease. 
- It avoid exponential module and divider.

### How can you do better:
- The approximation without maximum normalization
- $\sigma=\frac{e^{x_i}}{\Sigma_{j=1}^Ne^{x_j}} = \frac{2^{1.5x_i}}{\Sigma_{j_i}^N2^{1.5x_j}}$
- $2^{1.5x_i}=2^{u+v}\approx (1+v)<<u$, $2^v\approx 1+v$

### Comments
