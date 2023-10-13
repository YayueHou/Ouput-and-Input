# [011][Accelerator] Eyeriss: A Spatial Architecture for Energy-Efficient Dataflow for Convolutional Neural Networks
## Overview
* Authors: Yu-Hsin Chen, Joel Emer, Vivienne Sze 
* Affiliations: MIT
* Publication Venue: 2016 ISCA
* Link: [10.1109/ISCA.2016.40](https://ieeexplore.ieee.org/document/7551407)
## Summary: 
### Problem:
* Data handling. Input loading and partial sum storage cost energy and area.
* Shape adaptive matters.
* No comparison method for energy consumption of different dataflow
### Key idea: 
- Taxonomy of dataflow
        1. weight stationary
        2. output stationary
        3. No Local Reuse
        4. Row Stationary
- Efficiency calculation
        1. calculate relative normalized results (not accurate data)
        2. use REUSE to define the input consumption
        3. use ACCUMULATION to define the psum calculation consumption
### Takeaways: 
###	Strengths: 
- first one to introduce dataflow concept
- a taxonomy research method
###	weaknesses: 
- compression out of date.
###	How can you do better:
- encoding method is already be improved by later research.

