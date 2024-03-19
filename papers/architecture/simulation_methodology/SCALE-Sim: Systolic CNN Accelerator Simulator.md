# [0xx][DNN simulator][systolic array dataflow] SCALE-Sim: Systolic CNN Accelerator Simulator
## Overview
* Authors: Ananda Samajdar, Tushar Krishna
* Affiliations: gatech
* Publication Venue: 
* Link: [https://arxiv.org/abs/1811.02883](https://arxiv.org/abs/1811.02883)
## Summary: 
### Problem:
- Where does the high efficiency comes from?
  - The data stream from near by PE which means the data movement is purely locally.
  - The hyper-parameters have some impact on the model performance, which are interwined.
### Motivation
- Mapping the dataflow to the accelerator because dataflow would affect the performance of the system
- Hardware optimization
  - The compute unit utilization
  - Memory size is in positive proportion with the data reuse rate however is negatively proportional with the energy efficiency.
- Simulators: could be find on github
### Questions Answered: 
- Does the size of the array dictate the choice of dataflow?
  - Their result show that, array size do influence the performance of dataflow. However, the outperform dataflow does not changed when array size changed. No dramatic impact is shown.
  - The less time the stationary matrix is needed to be mapped into the array, the betther. (reuse the smaller matrix)
  - If the number of output pixels (input size and stride) are larger than the number of weight, WS will outperform.
  - Problem: They didn't do layer wise evaluation.

- How much does the hyper-parameters of the workload dictate the choice of dataflow?
  - Memory bandwidth: The demanding bandwidth decrease while the buffer size (scratch pad) increase. The return will dimish after a threshold.
  - Shape of array: Square shape of array performance better. (In my opinion that is because the data reuse peak appears around the square shape)
  - **Scaling out vs. Scaling up**: 
    - scaling out means having more arrays and dividing compute among them; Scaling up means adding PEs to make the array bigger.
    - Overall scratch out outperform, however this would vary between workloads.

- Are we missing out a lot by employing fixed dataflows? Or is there a dataflow which works in all cases?
    - No according to aforementioned.
### Takeaways
1. This paper could support my opinion the smaller size matrix is better to be stationary
2. The Scaling out and scaling up is observed in my research. Though not dramatic impact.
