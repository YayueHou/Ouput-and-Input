# Instruction-Level Parallelism
This section is a reading review based on [Computer Architecture, Sixth Edition: A Quantitative Approach](https://dl.acm.org/doi/book/10.5555/3207796).


## Pipeline
Most processors applying pipeline to increase the efficiency of instruction execution by overlaping instructions. Each instruction in RISV-V ISA could be finished in 5 cycles. A complete execution is described as follow：
1. Instruction fetch cycle. 取指
PC is sent to memory and fetch the instruction. Update PC+=4.
2. Instruction decode/register fetch cycle. 指令译码/读寄存器


## References
[1] John L. Hennessy and David A. Patterson. 2017. Computer Architecture, Sixth Edition: A Quantitative Approach (6th. ed.). Morgan Kaufmann Publishers Inc., San Francisco, CA, USA.