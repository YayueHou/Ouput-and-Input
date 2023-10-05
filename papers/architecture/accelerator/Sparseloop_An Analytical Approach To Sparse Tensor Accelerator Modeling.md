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
        1. Leader-follower intersection: Only check one operand. If the operand is zero, then keep the MAC idle. This may not detect all the ineffectual operations.
        2. Double-sided intersection: Detect both two operands. Either of them being zero could make the MAC stay idle. This could detect all the ineffectual operation, but may cause additional hardware overhead.
        - However, though the MAC is idle when encountering ineffectual, the caculation time is same as dense matrix. It could only reduce the power consumption.
    - Skipping IneffOps 
        1. The Skipping method totally skip the operation, when a ineffectual operand is detected, but not only stay idle. This method could also reduce the execute time 
### Takeaways: 
### Strengths: 
### weaknesses: 
### How can you do better: