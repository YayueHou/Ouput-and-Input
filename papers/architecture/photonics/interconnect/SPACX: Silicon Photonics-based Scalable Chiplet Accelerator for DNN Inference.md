# [001] [Photonic Chiplet] SPACX: Silicon Photonics-based Scalable Chiplet Accelerator for DNN Inference
* Authors: Yuan Li, Avinash Karanth
* Affiliations: Ohio University
* Publication Venue: HPCA 2022
* Link: [https://ieeexplore.ieee.org/document/9773266](https://ieeexplore.ieee.org/document/9773266)

## Summary: 

1. Problem:
    - Metallic-based interconnects obstacles (latency, power efficiency, bandwidth)
    - Broadcast communication (DNN nature but not well-support by  metallic)
2. Key Ideas:
    - Arch: 8 chiplet and 8 PEs arch with photonic in silicon interposer while electrical in global buffer
    - Broadcast: unicast to interface with GB, splitters to enable sigle broadcast; Share same wavelenth to enable cross - chiplet communication
        - Dataflow:
        - BandWidth: Tuning the numbers of wavelengths
3. Strengths
    - Lower Communication time and execution time
    - Largely reduce network energy
4. Weaknesses
    - Higher computation time in intensive layers.
5. Others
    - Bandwidth allocation scheme: Lower time* higher E/O 