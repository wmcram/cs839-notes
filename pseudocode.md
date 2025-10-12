# Conventions for Quantum Pseudocode
Summary: The author gives some notational conventions and semantic ideas that apply when writing pseudocode for high-level descriptions of quantum algorithms.

- Use underline notation for quantum registers; have same semantics as classical registers, but exist in superpositions of computational basis states
- Once a register "becomes quantum", cannot do anything classical with it until it is measured
- Only classes of operations on quantum registers: unitary evolution and measurement
- Assigning quantum register to classical one just does a measurement automatically
- Unitaries can be reversed easily
- Can convert to classical without measurement if a proof is supplied that register is in known state
- "pure" (non-measuring) subroutines are compatible with the quantum if statement, just like the QML paper
