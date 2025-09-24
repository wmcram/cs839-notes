# Focus beyond Quadratic speedups for Error-Corrected Quantum Advantage
Summary: The authors do some napkin math to find when the crossover point is for quantum advantage in various problems
and quantum computing models. They find that even with many concessions to the quantum side, with current tech these crossover
points are prohibitively large for speedups under n^4.

- Quantum error correction and device operation times introduce huge constant factors on quantum algorithms
- Quantum gates slower by factor of ~1e10
- Authors believe merely quadratic speedups are not practical "quantum advantage"
- Authors also note that most problems amenable to quantum algorithms are embarrassingly parallel already
- Toffoli gates need CCZ states, which are time-consuming to make and consumed on use
- Typo on page 4 lol "between 10 and 10"
- Ion traps and superconducting qubits leading styles, but both still have prohibitively large gate times
- Quantum advantage only realized for very large problem sizes and still requires OOMs of speedup
- Need quartic speedup or higher to be truly viable today
- Examples of quartic: Tensor PCA algo, query complexity reductions, linear diffeq
- Authors consider other cost models but argue that the results are similar regardless (on energy, physical space usage)
