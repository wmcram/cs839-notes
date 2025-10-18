# Unqomp: Synthesizing Uncomputation in Quantum Circuits
Summary: The authors provide a process for transforming circuits in a semantics-preserving way such that all ancilla qubits are uncomputed to |0>. They do the operations on a circuit graph model, and provide transformations to and from quantum circuits.

- Silq's type system can give some guarantees, but it still has no compiler so no actual implementation can be used
- Automatic uncomputation can duplicate work if we are not careful
- A temp value can be safely uncomputed via inversion if the original computation can be described classically and depends on values that can be reused
- A gate is qfree if it can be expressed on classical bits; qfree gates can be automatically uncomputed
- Problem: given a circuit C and ancillae A, create a new circuit C' with same semantics but resets ancillae to |0>
- Where to insert inversion? After all gates using computed value, and before any gates targeting values used in the inversion
- Use a model called circuit graph, kind of like a compute graph but less ordering restrictions

Algorithm:
1. Find last gate targeting ancilla
2. Check that gate is qfree
3. Insert inversion node into graph and ensure no cycles were formed

- The process above is repeated for each gate applied to an ancilla
- Circuits can be transformed to circuit graphs algorithmically
- Semantics given to circuit graphs, just pick a linearization of the nodes and run the gates in order (can be shown it doesn't matter which ordering we pick)
- To compile a graph back to a circuit, again just pick an ordering and lay down the gates
- If the lifetimes of ancillae don't overlap, can use the same wire for both of them
- Unqomp first iterates over a graph in reverse order, doing an uncomputation step for each gate acting on an ancilla
- Uncomputation not possible in general, Unqomp errors in this case
- Unqomp only recognizes a subset of valid behaviors, can't optimize H^2
- Authors give Qiskit++, or Qiskit with Unqomp
