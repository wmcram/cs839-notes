# How to Factor 2048 bit RSA integers in 8 hours using 20 million noisy qubits
Summary: The authors combine a bunch of techniques to optimize Shor's algorithm and DLP, and give some cost estimates for realizing such a computer.

## The Construction
- Shor's works by computing order r of a random g in Z/N
- Turn exponentiation into iterated controlled modular multiplication
- Decompose this into controlled scaled addition, then into controlled modular addition, then into regular addition w/ comparison
- The "coset representation" allows us to swap from modular adders to regular adders 
- We use windowed arithmetic, which turns groups of controlled additions into a "lookup table add" using the methods of the previous paper
- Around ~37ms per lookup addition op
- Factoring 2048 bit integer then takes ~7hrs
- Lattice surgery impl of QEC takes 2(d+1)^2 phys qubits per logical qubit

## Cryptographic Implications
- Enhanced Shor's outperforms Ekera's algorithm
- Crypto has moved from DLP in finite fields and RSA -> DLP on elliptic curves
- Need to migrate ~20 years ahead of schedule to protect confidential info-at-rest

## Future Work 
- Could translate classical Karatsuba or Strassen to a quantum circuit
- Could use a better CCZ factory via a block code
- Could parallelize/distribute the additions
