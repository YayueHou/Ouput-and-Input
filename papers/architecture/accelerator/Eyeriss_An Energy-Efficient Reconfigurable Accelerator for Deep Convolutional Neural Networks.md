# [009][dataflow] Eyeriss: An Energy-Efficient Reconfigurable Accelerator for Deep Convolutional Neural Networks
- Authors: Yu-Hsin Chen, Tushar Krishna, Member, Joel S. Emer, Vivienne Sze
- Affiliations: MIT
- Publication Venue: IEEE JOURNAL OF SOLID-STATE CIRCUITS, VOL. 52, NO. 1, JANUARY 2017
- Link: [10.1109/JSSC.2016.261635](https://ieeexplore.ieee.org/document/7738524)
## Summary: 
### Problem: 
- From on-chip to off-chip/Interchip data movement (High energy efficiency/Large throughput)
- Compress data
- Adjustable CNN shape

### Key idea:
-Structure
	1. 2 clock domian (Link->FIFO<-Core Clock, 64 bit bus)
	2. 168 PEs (16*14), communicate with neighbour/GLB/scratch pad 
        3. 4 level mem hierarchy (108k GLB, DRAM, inter-PE, spad) 
        4. a RLC CODEC, a ReLU module
### Control
1. Top level: DRAM and GLB (asynchronous interface), GLB and PE (NoC), RLC and ReLU; Lower level: inter PE 
2. reconfigure (layer shape, communicate pattern)->processing->reconfigure(next layer)->... 
	- Data Movement
  		1. Raw Stationary dataflow (minimize movemnet)
                	- 1D in row as primitives
                	- 2D in PE sets (W in horizen, I in diagonally, O in vertical)
		        - nD multi  PE sets, array processing pass
            	2. Data Statistic: RCL module
### NoC
1. Global input network/output network with X-bus and Y-bus, PE->PE directly
2. PE/Data Gating
   	- 3 spads with FIFO connection (SRAM for filter, Registers for ifmap and psum)
     	- Gate logic with zero buffer to ignore 0
## Takeaways: 
- Strengths: Take energy cost between DRAM and chip into acount
- weaknesses: Compression only work in networks with many repeated numbers
- How can you do better: WDM worth considering
