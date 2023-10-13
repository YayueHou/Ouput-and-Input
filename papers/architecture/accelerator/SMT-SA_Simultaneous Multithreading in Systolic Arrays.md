# [012][Systolic Array] SMT-SA: Simultaneous Multithreading in Systolic Arrays
## Overview
* Authors: Gil Shomron, Tal Horowitz, and Uri Weiser
* Affiliations: NVIDIA
* Publication Venue: IEEE COMPUTER ARCHITECTURE LETTERS 2019
* Link: [10.1109/LCA.2019.2924007](https://ieeexplore.ieee.org/document/8742541)
## Summary: 
### Problem:
- The propagation of zero valuse through the array could cause the underutilization of MAC.
### Key idea: 
- SMT-SA
  - The paper intruduced simultaneous multithreaded systolic to utilize the MAC when encountering zero values
  - SMT-SA has more than one threads on each PU. The PU recieves more than one input, bypass the thread with zero values.
  - Non-zero values thread are held by queue to be selected.
- IR sharing: To reduce the area cost, IR buffer and MAC are shared by all threads per PU. 

### Takeaways: 
- Evaluation
  - Estimate the area and energy cost through Cadence Innovus.  
  - The paper use the ratio of performance speedup and area overhead to estimate area efficiency.
###	Strengths: 
- multithread seems to be efficiency in speedup and energy efficiency. And the area overhead is acceptable.

###	weaknesses: 
- To improve the performance of SMT-SA, additional hardware overhead has been introduced.
- The area overhead presented directly is important for the discription of area increase.
###	How can you do better:
- 