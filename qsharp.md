# Q\#: Enabling scalable quantum computing and development with a high-level DSL
Summary: The authors present a new high-level quantum programming language with many features from modern languages like default immutability, higher-order functions and partial application, and more. It models quantum computation as happening in an environment auxiliary to a classical computer, which calls into the quantum programs as subroutines similarly to a GPU.

- Classical control, recursion, while loops difficult or impossible to realize in the circuit model
- Supports definition of oracle circuits
- Language makes quantum routines available to the classical host program
- Has partial application (even has hole syntax)
- Notion of "quantum purity"; function can affect classical state but not quantum state
- Measure keyword like in Silq
- Using keyword (like python with) allocates some qubits and releases them following the block
- Can borrow rather than allocate "dirty ancillae" with borrowing keyword
- Support for generics, map, fold
