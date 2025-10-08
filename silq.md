# Silq: A high-level quantum language with safe uncomputation and intuitive semantics
Summary: Silq is an imperative quantum programming language that automatically inserts uncomputation steps when the compiler proves it is safe to do so, reducing programmer burden. Silq supports const parameters like in C++, and supports annotation of functions with keywords qfree and mfree for functions that avoid superposition and measurement respectively.

- Typical quantum languages need to uncompute temporary values
- Uncomputation can be done safely if:
1. The uncomputed value can be described classically
2. The variables used to evaluate it are preserved

## Intro to Silq

- Silq is a language which automatically inserts uncomputations when valid
- Uses QRAM model of computation
- Silq uses linear types to detect when values are no longer used, and treats constants non-linearly
- Generalize unitary operators to linear isometries (throw away same dimension requirement) to support dynamic alloc/deallocation
- Supports "const generics" over natural numbers
- Classical variables use "!" notation, and can be copied freely unlike quantum variables 
- "qfree" functions can be viewed as functions on ground sets
- Supports c++ style "const parameters" for read-only args
- Linear type system consumes non-const parameters after call
- reverse(f) gives the inverse function for all non-measuring functions
- intuition: qfree says no superposition, mfree says no measurement

## Silq-Core
- Silq-Core is a stripped-down version without dependent typing, imperative fragment, other unnecessary stuff
- Keywords reverse, measure, if-then-else
- if supports classical and quantum conditions
- Have product types, no sums
- measure keyword consumes its argument, returning a classical variable
- Silq requires ~half as many quantum gates compared to Q#

### Key Features of Silq
- const, only QPL with read-only parameters
- qfree, for functions that don't induce superpositions
- mfree, for functions that don't measure
