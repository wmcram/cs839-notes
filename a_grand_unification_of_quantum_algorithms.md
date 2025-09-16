# A Grand Unification of Quantum Algorithms
Summary: The authors present how the Quantum Singular Value Transformation (QSVT) can be used to implement amplitude amplification, phase estimation, and hamiltonian simulation and outlines how the theory was developed. They claim this points to a "unification" of different quantum algorithms.

- QSVT applies a polynomial transform to the singular values of an operator (which is embedded in a larger unitary operator)
- Achieved by appling SU(2) rotations to embedded subspace
- Polynomial parameterized by rotation angles 
- Parameterizing QSVT gives rise to almost all known quantum algorithms


## QSP to QSVT
- QSP essentially uses two types of single-qubit rotation: Signal rotation (W) and signal processing rotation (S)
- Signal rotation has fixed angle, processing rotation varies
- By choosing certain angles, can increase sensitivity of qubit to signal (greater region of "guaranteed" |0>)
- Bijection between polynomials and phase angle sequences (order of poly = len sequence)
- Qubitization: identifying qubit-like subsystems
- "oblivious" amplitude amplification realized by QSP, but finding phase angles is a challenge
- Grover's algorithm realized by picking all angles to be pi
- Eigenvalue transform can apply poly to eigenvalues of embedded matrix
- Can extend to singular values of a possibly non-square matrix
- Use block-encoded operators for larger transforms => realized as a controlled-A operator in circuits
- All about constructing the needed operator and "one shotting" the problem

## Search via QSVT
- In search we know we have initial state psi_0 which is non-orthogonal to final state |m>.
- Want a polynomial sending a -> 1
- Can approximate the sign function with polynomials
- QSVT needed over eigenvalue transform here

Algo: Assume we have a controlled version of oracle U
1. Use QSVT to construct the needed operator for a = 1/sqrt(N) in matrix element |m><psi_0|
2. Apply operator to uniform superposition; |m> in register with probability at least 1-delta, can decrease delta as needed

## Eigenvalue threshold via QSVT
- Given access to a Hamiltonian H, want to know if any of its eigen values are smaller than lambda_t
- Block encode H, difficult this time since ||H|| is unknown
- Want to create a function with QSVT which filters large eigenvalues
- After applying certain (even) polynomial and simplifying, problem reduces to needing to distinguish between two Bernoulli distributions
- Authors provide a time bound for distinguishing the distributions with ~O(log(1/delta)) for confidence 1-delta

## Phase Estimation via QSVT
- Given access to unitary U and an eigenvector |u> and eigenvalue e^(2ipi * phi), find phi

1. Assume phi is an m-bit number (finite precision). We iterate from LSB to MSB
2. At each step, construct a matrix with singular values encoding LSB of phi and theta
3. Applying QSVT and measuring an ancilla gives one bit of phi

- Since factoring (Shor's algo) relies on phase estimation, we can use QSVT to do factoring
- QSVT can also be seen as a generalization of the QFT

## Function Evaluation via QSVT
- Want to evaluate a function f of a matrix
- Use QSVT with a polynomial approximating f
- Hamiltonian simulation feasible with the exponential function (decomposed into cos and isin)
- Can do matrix inversion for Hermitian A
- Use an odd polynomial approximating 1/x
