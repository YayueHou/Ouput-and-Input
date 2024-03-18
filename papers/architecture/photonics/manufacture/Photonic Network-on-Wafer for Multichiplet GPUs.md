# [0xx][interconnect technology] Photonic Network-on-Wafer for Multichiplet GPUs
## Overview
* Authors: Shiqing Zhang, Lieven Eeckhout
* Affiliations: 
* Publication Venue: IEEE micro
* Link: [https://dl.acm.org/doi/10.1109/MM.2023.3237927](https://dl.acm.org/doi/10.1109/MM.2023.3237927)
## Summary: 
### Problem:
1. GPUs are scaled by connect multiple GPU together while proveding abtraction of a single logic GPU to software. Providing low cost high bandwidth inter GPUs in long distance is challenging.
### Why photonic
1. The distance of space. Eletrical should be around 100um-200um to avoid crosstalk. Photonic is around 25um.
2. Bandwidth density
3. Power consumption.
4. Optical interconnect can cross each other in one layer.
### Key idea: 
- Photonic network-onwafer (NoW) GPU architecture in which premanufactured and pretested GPU dies and memory chips are mounted on a wafer-level interposer that connects the GPU chips through a photonic network layer, while connecting each GPU die with its local memory stack electrically

