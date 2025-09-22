# Architectures for a quantum random access memory
Summary: The authors present some QRAM architectures which require O(2^n) quantum logic gates but only use O(n) gates per access.

- QRAM allows superposition of input addresses, but the "cells" themselves are just bitstrings. The input superposition, however, gives rise to an output superposition of bitstrings
- O(2^n) logic gates needed for classical and QRAM, but "bucket brigade" strategy allows for only O(n) gate usages per call

## Description of Protocol
- In a "fanout" RAM, each bit of address tells you which way to go in an abstract BST
- This is the naive case, need to control O(2^n) gates during a call but easy to implement
- In bucket brigade, pass both routing and I/O signals along the same route using trits
- State 2 of a trit is the "wait" state, which absorbs a signal and then switches to it (ex. an incoming 0 turns 2 -> 0)
- Passing input bits in one-by-one, a path is carved through the sea of 2 states until the destination is reached, and only O(n) gates are fired
- Less gates being fired means less chances for errors, useful for keeping QRAM coherent
- In practice, for a fanout QRAM we need to do a little more. Authors present a "quantum bus" which performs unitary transformations on the input qubit that represent "routing"
- Doing this routing entangles some state with the bus itself, must utilize uncomputation to decorrelate
- For a bucket brigade QRAM, we now use "qutrits". Similar to classical version, |0> and |1> route qubits while |2> "absorbs" a qubit (how does this preserve reversibility?)
- Again, after the route is carved we send a bus qubit through before bringing it back and uncomputing the path we made
- This can be generalized to the case where memory cells store quantum, not just classical, information
- One way to accomplish this (workaround no-cloning) is with "swap-only" RAM (linear types connection?)

## Physical Implementations
- Can use an optical array to accomplish a fanout QRAM
- Can also use controlled phase gates
- Physical qutrits can be realized by creating a coupled level structure
- A "Raman transition" can be used to realize the absorption/retransmission of qubits
