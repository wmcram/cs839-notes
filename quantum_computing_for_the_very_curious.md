# Quantum Computing for the Very Curious
Summary: A quick tour of the fundamental concepts in quantum computing.

## Introduction
- In search of a solution to Hilbert's [Entscheidungsproblem](https://en.wikipedia.org/wiki/Entscheidungsproblem), Turing formulated the eponymous Turing Machine which can execute any "computable" algorithm (see Church-Turing thesis)
- Question (Deutsch): Is there a single universal computing device which can efficiently simulate any other physical system?
- Quantum systems are famously hard to simulate

## Part I: The State of a Qubit
- Qubits are the QC analog of a classical "Bit"
- The state of a bit: 0 | 1
- The state of a qubit: complex-valued unit vector (x_1, x_2) in state space (C^2)
- Computational basis states: |0> := (1,0) and |1> := (0,1) corresponding to classical 0 and 1
- As in linear algebra, we make linear combinations of the basis states to span C^2
- Define amplitude as the coefficient of a particular state in a superposition (linear combination)
- To wonder: Why does state space look the way it does?

## Part II: Quantum Logic Gates
- Quantum NOT: NOT(a|0> + b|1>) = a|1> + b|0>
- Notation: NOT ~ X (Related to Pauli spin matrices)
- Quantum gates are unitary linear operators, equiv. 2x2 unitary matrices
- Recall: unitary means that U^daggerU = I
- X becomes the matrix ((0,1),(1,0))
- X is an involution (just like classical NOT)
- Gate Composition ~ Matrix Multiplication (just like linear algebra)

- Hadamard Gate: H|0> = 1/sqrt(2) * (|0> + |1>), H|1> = 1/sqrt(2) * (|0> - |1>)
- H is also an involution

Exercises:
1. H^2 = I as above
2. J sends the given vector to 0, so the gate is not unitary.
3. This is just because function composition is written backwards from how "pipes" are written.

- Measurement of a Qubit is a probabilistic conversion to a classical bit (recall probability = amplitude^2)
- Qubit collapses to one of the computational basis states right after measurement
- Exercise: the given qubits are just H|0> and H|1>, and as shown above H is an involution. Therefore, applying H again sends these qubits back to |0> and |1>, which will measure as 0 and 1 with certainty.
- Rotations are unitary matrices
- Unitary matrices preserve length of argument, important because then we preserve unit norm for our qubits. In fact, a matrix is norm-preserving iff it is unitary.
- An n-qubit system has 2^n basis states (similar to states of bits)
- CNOT gate: If first qubit is 1, flip second qubit. Equiv, |x,y> => |x, y XOR x>
- Applying H to first qubit of |00> then running both through a CNOT produces 1/sqrt(2) * (|00>+|11>), an entangled state.
- CNOT is an involution
- CNOT can flip control qubit: CNOT|+-> = |-->
