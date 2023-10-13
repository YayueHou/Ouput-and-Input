# [014][Accelerator]SCNN: An Accelerator for Compressed-sparse Convolutional Neural Networks
## Overview
* Authors: Angshuman Parashar, Minsoo Rhu, Anurag Mukkara
* Affiliations: MIT UCB
* Publication Venue: 2017 ISCA
* Link: [https://doi.org/10.1145/3079856.3080254](https://doi.org/10.1145/3079856.3080254)
## Summary: 
### Problem:
- pruning and ReLU cause redundency (RAM access, RAM space)
- previous work only apply one of weight/activation. 

### Key idea: 
- dataflow
  - Apply Input Stationary
    - Block channels to K_c/K, calculate K_c*H*W
    - send W/I from seperated bank of data (splited refer to the coordinate of output by a network like crossbar switch) 
    - do Cartesian product
- Architecture
    - PEs simply connected
    - driven by sequencer (control data movement)
    - arbitrated bus for broadcast and delivery.
### Takeaways: 

###	Strengths: 
- the first to apply sparse on weight and activation at same time.

###	weaknesses: 
- The application of coordinate computation introduced additional hardware overhead.
- The Cortesian product caused multiplexing adundency.
###	How can you do better:
- Using other dataflow or methods.
