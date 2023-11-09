# Sparse Matrix Multiplication
## Background
- Sparse Matrix multiplication appears in several fields.
  - In ML, after pruning and activation funtion, the matrix will become sparse.
- In previous research, people proposed several methods to optimize MatMul
  - For sparse MatMul, there are three kind of dataflows which is most applied.
    - Inner-product
    - Outer-product
    - Row-wise product

##  
## Storage of Sparse Matrix
- **CSR**
It keeps three arrays, containing the offsets of the beginning of each row (offsets), the nonzero values(vals), and their column indices (columns)
$$
\begin{pmatrix}
0 & 1 & 3 & 0 & 0 \\
2 & 0 & 0 & 0 & 0 \\
0 & 4 & 0 & 5 & 6 \\
0 & 9 & 0 & 7 & 0 \\
0 & 0 & 0 & 0 & 8 
\end{pmatrix}\\ 
vals: \{1 , 3 ,2 , 4 , 5 , 6 , 9 , 7 , 8 \} \\
columns: \{1, 2 , 0 , 1 ,3 ,4 , 1 , 3 ,4 \} \\
offsets: \{ 0 , 2 , 3 , 6 , 8 , 9 \}
$$
- **CSC** 
As same as CSR except store align column.

## Sparse Patterns
