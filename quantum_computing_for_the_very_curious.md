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
- Quantum gates are linear operators, equiv. 2x2 matrices
- X becomes the matrix ((0,1),(1,0))
- X is an involution (just like classical NOT)
- Gate Composition ~ Matrix Multiplication (just like linear algebra)
