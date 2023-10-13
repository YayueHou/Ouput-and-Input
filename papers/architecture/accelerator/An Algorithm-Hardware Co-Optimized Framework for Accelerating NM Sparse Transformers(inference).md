# [012][Accelerator]An Algorithm-Hardware Co-Optimized Framework for Accelerating N:M Sparse Transformers
## Overview
* Authors: Chao Fang; Aojun Zhou; Zhongfeng Wang
* Affiliations: Nanjing University
* Publication Venue: Transaction of VLSI system 2022
* Link: [10.1109/HPCA53966.2022.00049](https://ieeexplore.ieee.org/document/9773187)
## Summary: 
### Problem:
- Deploying Transformers requires large memory and computation overhead.
- Previous Unstructured sparsity cannot be predicted in advanced, which made the performance dragged.
- It is restricted to accelerate N:M sparse networks on current hardware platforms. The SOTA design is infoexible to meet different hardware constraints. 
### Key idea: 
- Co-design frame work
  - At algorithm level, itrerate for several times and let the winner model of each iterate become the next step's input. Limit N from M-1 to n
  - At hardware level, the framework generate the hardware configuration and instructions according to the final winner model.
  - 
- sparsity inheritence mechanism
  - Use current winner model to generate the winner model of next level, that means from N-1->N-2->.....
  - The paper leverages group-wise magnitude pruning.
 
- bitmap-based compression

- STA hardware architecture 
  - A diverse MatMul computing is applied which contains sparse-dense and dense-dense MatMul. Dense-dense bypass the 0 selector.
  - Scalable softmax module is implemented by parrallism and pipline.

### Takeaways: 
- The paper is a little bit similar like EVA, and maybe can be set as an baseline. 

###	Strengths: 
- Divided the results in different sets with different benchmarks.
- Only apply sparse on weight matrix. The access to input DRAM is not neglectable.
###	weaknesses:
- The model is trained for many times during the inheritence mechanism, which cause a large training overhead. 

