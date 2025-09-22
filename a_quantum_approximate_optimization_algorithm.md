# A Quantum Approximate Optimization Algorithm
Summary: TODO

## Introduction
- Combinatorial Optimization (CO) problems specified by n bits and m clauses
- A clause is a constraint for some of the bits
- Objective function is number of satisfied clauses
- Ex. SAT wants optimal value = # clauses
- Intial state is equal superposition, we turn the obj. fn. into a diagonal operator in computational basis
- Interleave defined "B" and "C" operators to create a desired state in at most mp+p steps, where p is number of interleavings
- As p -> \infty, the max possible expectation value of C in desired state (F_p) over all angles approaches optimal value from below

Algo outline:
1. Pick p and start with angles that maximize F_p
2. Interleave operators to get the desired state
3. Measure in computational basis to read out bitstring z, with high prob. it is optimal

- Can draw angles uniformly from a quantized grid (\[0,2pi\] \times \[0,pi\])^p

## Fixed p algorithms
- Consider MAXCUT for graph of bounded degree. Operator for an edge j-k involves qubits j, k, and those with distance \leq p to j or k. 
- So for any p, operator involves edges at most p steps away. p is in some sense a measure of locality
- Distribution of C is concentrated near its mean
- On 2-regular graphs (rings), max value is n or n-1 for n even or odd
- For p < n/2, the p-subgraph at an edge is just a line with weight n
- As p grows, approximation ratio approaches 1 independent of n
- On 3-regular graphs, set of possible (p=1) subgraphs can be narrowed down significantly
- Use a classical computer to calculate number of types of subgraph and thus the maximum of F_1
- Finding the optimal angles in these cases has a classical (numeric) algorithm
- Algorithm has worst-case approximation ratio ~0.7 for p=1, 0.75 for p=2 (note that the p=1 result is worse than some classical algos)

## A Variant of the Algorithm
- Consider independent set on n vertices
- Size of independent set is hamming weight of answer string z
- In this case, B sends z' -> z iff z and z' have hamming distance 1 (B represents the hypercube with only legal strings)
- Start state is all |0>
- Again, the maximal value is approached as p -> \infty
- Authors give a subroutine for estimating F_p. For p = 1 this can be viewed as evolving |z=0> with the Hamiltonian B, which is an instance of a continuous time QRW.
- For the discrete graph Hilbert space is dim 2^n and B is just the adjacency matrix of the whole hypercube and |111...> is optimal
