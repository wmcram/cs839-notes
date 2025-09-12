# Tower: Data structures in quantum superposition
Summary: The authors develop a quantum PL with RAM, a memory allocator, and a language for bounded recursion.
The reversible semantics of these systems allows concrete implementations of abstract data structures in a QC.

## Background
- Many quantum algorithms rely on data structures requiring RAM
- Three requirements for data structures in quantum PLs:
1. Reversible Operation: Every operation must be reversible
2. History Independence: Each instance of the DS has a single unique physical representation in memory,
   oblivious to its history of operations. Needed for interference to behave properly. Example given in text
   is if the set {1,2} was impl'd as [1,2] but elsewhere as [2,1], interference wouldn't work since states differ.
3. Bounded-time execution: Operations must have time bounds depending on only classical parameters. Because recursion
   must be unrolled by "compiler", recursion must then be classically bounded.

- Core Tower is the PL which has reversible operation
- Boson is the memory allocator which has history independence
- Combined into Tower lang, which bounds execution with its type system, providing all 3 properties.
- Ground is a basic DS library using Tower
- qRAM implemented in terms of a gate that swaps a register with a memory addr.

## Data Structures in Tower
- Variables can be in superposition
- Classical operations can be lifted over superpositions (think fmap)
- Use uncomputation to preserve reversibility of some ops
- Can get reverse operations "for free" using syntactic inversion (duality connection)
- Implementing sets with binary trees or hash tables is not H.I.
- To get H.I. we need a unique linking structure for every DS and unique physical repr.
- Boson ensures that all allocations are H.I.
- Radix trees have linking structure in bijection with sets

## Core Tower
- Core Tower is imperative and reversible
- Operational semantics for expressions and stmts
- if statements cannot have a net effect on context, and condition cannot be modified post-hoc
- Machine states <s, R, M> of program, registers, and memory
- Core Tower's semantics are sound in both directions
- There is a semantics for translating Core Tower to a unitary quantum circuit

## Boson
- Boson uses a free list for allocation
- Naive implementation not H.I. (even if we dealloc everything!)
- Can make naive solution statistically H.I. if the freelist is uniformly chosen from
- However, by making the free list a uniform superposition with the symmetrization operator we recover H.I.
- Symmetrization is an idea from quantum simulation

## Tower
- Tower extends Core Tower with more types, recursion bounds, fn defs
- Tower can be translated to Core Tower, recursion is inlined

## Ground
- Has lists, stacks, queues, sets
- When recursive calls are uncomputed, exponential slowdown can occur. Using an accumulator goes exp -> linear time for some algos
- Hard to uncompute data if it can be conditionally mutated
- Time complexity of a quantum program is the sum (not max!) of its branches
