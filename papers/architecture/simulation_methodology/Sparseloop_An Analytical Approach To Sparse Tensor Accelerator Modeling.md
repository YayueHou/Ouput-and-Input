# [0xx][Accelerator][taxonomy]Sparseloop: An Analytical Approach To Sparse Tensor Accelerator Modeling
## Overview
* Authors: Yannan Nellie Wu, Po-An Tsai, Angshuman Parashar
* Affiliations: MIT, NVIDIA
* Publication Venue: MICRO 2022
* Link: [10.1109/MICRO56248.2022.00096](http://sparseloop.mit.edu/documents/2022-micro-sparseloop.pdf)
## Summary: 
### Problem:
- There is no systematic description and modeling suport for sparse tensor accelerator design.
- Existing design impede designer by low capabilities to explore more design space.
- Mathematical or analytical calculation of accelerator's characteristics are only flexible for dense accelerator designs.

### Key idea: 
- Taxonomy: sparse acceleration features (SAFs)
    - Representation format
        - It means how to represent the location of non-zero values. 
        1. *Uncompressed*: original vector without compression.
        2. *Coordinate Payload*: Use Coordinate to reperesent the position of non-zero values and use Payload to store the real non-zero values or pointer to next dimension.
        3. *Bitmask*: Compress data in a dense array and use a map with one bit values to represent the position of values.
        4. *Ren Length Encoding(RLE)*: Use multiple bits values to represent the distance between non-zero values.
        5. *Uncompressed Offset Pair*: Use multiple bits to represent the position of the start and end position of a series of zeros.
    - Gateing IneffOps
        1. Leader-follower intersection: Only check one operand. If the operand is zero, then keep the operation idle. This may not detect all the ineffectual operations.
        2. Double-sided intersection: Detect both two operands. Either of them being zero could make the operation stay idle. This could detect all the ineffectual operation, but may cause additional hardware overhead.
        - However, though the operation is idle when encountering ineffectual, the caculation time is same as dense matrix. It could only reduce the power consumption.
    - Skipping IneffOps 
        1. The Skipping method totally skip the operation, when a ineffectual operand is detected, but not only stay idle. This method could also reduce the execute time.

- Modeling methodology: Sparseloop
    1. Model the runtime behaviors of sparse accelerators progressively
    2. Model the sparsity-dependent behavior of sparse accelerators statistically.
    3. Split design process into orthogonal process.
- Sparseloop framework
    - Input
        - *Workload specification*: The density and shape of tensors.
        - *Architecture specification*: Hardware organization of architecture and the attributes of components
        - *SAFs specification*: SAFs applied to the storage and computation.
        - *Mapping/mapspace contrainst*: The mapping between workload and iretation
    - Dataflow modeling: Describe tiling, movement and stationary pattern of data
    - Sparse Modeling: Responsible for reflecting the overhead and savings introduced by various SAFs.
        - Format-Agnostic Tensor Description: Use Fiber-tree to reperesent tiles to avoid an specific representation format.
        - Statistical Density Models: Get the density of the tensor statistically.
        - Format Analyzer: Derive overhead of different format.
        - Gating/Skipping Analyzer: Evaluate the amount of eliminated ineffectual operands introduced by each gating/skipping.
        - Traffic Post-processing
    - Micro-architectural Modeling
        - Speed up: cycles spend for actual and ated access
        - Energy


### Takeaways: 
- The SAFs and dataflow should be co-designed carefully to make sure they are amenable
- Find out what bottleneck the performance of accelerator may be more important than naively increase some parameters.
