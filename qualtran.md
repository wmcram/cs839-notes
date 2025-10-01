# Expressing and analyzing quantum algorithms with Qualtran
Summary: 

## Qualtran
- Authors implemented bloqs which represent quantum operations, subroutines, and programs
- Turn bloqs into a compute graph
- Linear logic used to implement no-cloning and no-deletion errors for bloqs
- Datatypes of arbitrary bit-width
- No sum or product types
- Recursively sum gate counts for sub-bloqs (DP?) to get total gate count of algo
- Qubit count of a bloq is max used for sub-bloq plus any aux (resting) qubits 
- Authors tested 32-bit quantum adder via classical simulation
- For quantum ops that are just "reversible classical ops on superpositions", can simulate classically efficiently

## Subroutines
- unary z-axis rotations
- SU2 rotations decomposed into z rotations
- QVR, which phase rotates each basis state
- Support for unary iteration from last session
- Support for QROM "lookup tables"
- Quantum state preparation, encoding a classical vector into amplitudes of qubits
- Can do a similar thing but put each vector entry into a basis state in a mixed density matrix
- Block encoding, quantum signal processing and even the QSVT

## Case Studies
- Authors provide decompositions of bloqs for Hamiltonian simulation using a variety of algorithms
- Also for ground states in quantum chemistry
- Also for breaking both RSA and ECC
- Toffoli counts for primitive ops are still really large, like 1e6 for modular multiplication
- So far, only estimates down to the logical level, true resource estimates need the physical parameters of hardware
- Qualtran lets you swap out your PhysicalCostModel
- Authors divide qubits into algorithm (logical) qubits, physical qubits, and "tiles" (squares of qubits used in surface code)
- Surface code works for Clifford gates easily, but T, Toffoli and CCZ need more support 
- Like in previous papers, this magic state distillation is a big bottleneck, Qualtran lets you set parameters of your factories
- Can set logical and physical error rates
- All of the above can be combined to get wall-clock time, physical qubit count, and error probability
