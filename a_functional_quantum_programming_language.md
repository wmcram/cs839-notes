# A functional quantum programming language
Summary: An exposition of QML, a functional language to represent quantum algorithms

## Finite classical and quantum computation
- Category FQC of finite quantum computations, FCC of finite classical computations
- A QML program is just a morphism in FQC
- Objects in both categories are finite sets, with quantum computations happening on C^A for some finite set A
- A reversible finite computation is a bijection (classical) or unitary operator (quantum)
- Initial state modelled as tuple (A,H) of input A and "heap" H; final state as (B,G) where our "product" is cartesian (classical) or tensor (quantum)
- Morphisms compose intuitively
- Two systems are extensionally equal if they agree on outputs for all inputs

## QML rules and semantics
- Syntax based on strict linear logic

## Conclusions
- The classical finitary language compiles functional terms into reversible computations, and the quantum version extends to unitary transformations
- Authors are implementing a QML compiler in Haskell
- Authors argue that control of decoherence is essential for quantum PLs
