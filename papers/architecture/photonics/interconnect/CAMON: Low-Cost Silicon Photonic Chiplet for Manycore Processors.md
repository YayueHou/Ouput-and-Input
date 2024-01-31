# [0xx][photonic interconnect][chiplet] CAMON: Low-Cost Silicon Photonic Chiplet for Manycore Processors
## Overview
* Authors: Zhehui Wang, Jiang Xu
* Affiliations: University of Science of Technology, Hong Kong
* Publication Venue: TCAD 2020
* Link: [https://ieeexplore.ieee.org/document/8755274](https://ieeexplore.ieee.org/document/8755274)

## Summary: 
### Problem:
- Systems scales up lead to need of low latency and energy consumption.
- Advantages of photonic connection: 
    1. Higher bandwidth
    2. More independent(to distance) and lower energy consumption.
    3. optical pins have higher energy efficiency than electrical pins.
### SOTA
- Several cores consist a cluster while several clusters consist a manycore processor. 
- Most SOTA manycore processor use directory-based cache coherence protocol.
- If consider directory as part of LLC, 63% flits are data from LLC to cluster while 27% are controls from cluster to LLC.

### Key idea: 
- Architecure
    - 4 core/L1 in a cluster, each cluster has one shared L2 cache, and LLC/Mem is shared by all clusters. 8 directories has a router attached with LLC/Mem router.
    - Only the connection between on-chip LLC/Mem router and off chip LLC/Mem router is optical. All other connections are electrical.
- Photonic chiplet
    - Area Eficiency: Use two seperate part to build up the chiplet. 
    - Easy Maintainess and thermal control: Use laser bank as light source
    - Apply MR as interface to build E/O O/E interface (more simple, energy/area efficient).
        - Traditional: SerDes and seperate E/O O/E module.
        - In paper: Use MR and PDs to to serialization/deserialization and EO/OE. Optical SerDes: 4 parallel eletrical signal each has pi/2 phase shift and tune the MR sequencially.
    - Apply laser light channels to reduce MR numbers. The channel and waveguide used in transmission is preassiged.
        - The agent fisrt send configuration info to laser source and destination optical switch.
        - Optical switches turn on relaed MRs which enables the transmission between photonic ring and TX/RX port.
    - Arbitration/Control simplify: Use agent connect to each router
        - Agent: manage conflict, generate MR configurarion info.
        - Deadback avoidance: Off-chip router agent as master and on-chip router agent as slave. Master first grant the request and than the slave.
    - Laser activation compensation: apply laser preactivation.

### Takeaways: 
- Using preassigned mapping may lost dynamic.
- There seems to be a drop off between bw and energy consumption because lasers are energy consuming but more laser means larger BW. There appears a optimazation point.

