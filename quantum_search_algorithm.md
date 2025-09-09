# How the Quantum Search Algorithm Works
Summary: A quick intro to Grover's algorithm.

- Quantum search requires O(sqrt(n)) operations compared to classical O(N)
- Algorithm works by layering circuits that check the search predicate repeatedly
- We make the simplifying assumption that there is exactly one solution, s
- Let C_s be an oracle that evaluates the predicate over a given instance x


## "Uncomputation" Trick
1. Apply oracle to |x>|0>|0> to get |x>|s(x)>|w(x)>
2. Tack on a qubit in |0> state, and CNOT with the s(x) register as control to copy s(x) to get |x>|s(x)>|w(x)>|s(x)>
3. Apply inverse of oracle to undo step 1, obtaining |x>|0>|0>|s(x)>
4. Throw away |0>|0>

- In general sends |x>|z> -> |x>|z XOR s(x)>
- Needed to implement "clean" computation (I guess making the I/O line up)
- Exercise: To build an OR gate, convert to NOT and AND gates using De Morgan and then just translate to circuit

## Grover's Algorithm
- Quantum search is useful when search space doesn't have much structure and there exists a recognizer (problem is NP)
- Let E be the equal superposition state over the search space. That is, if there are N = 2^n candidates, apply H to n qubits.
- Idea is to grow good amplitudes and shrink bad ones
- Letting sin(delta) be the component of E in the |s> direction, we see that sin(delta) = 1/sqrt(N) and hence delta = arcsin(1/sqrt(N)), which approximates to 1/sqrt(N) for large N.
- Reflection across |s>, then |E> would decrease angular distance to |s> by 2 * delta
- Since required rotations is proportional to 1/delta and delta is proportional to 1/sqrt(N), we have O(sqrt(N)) ops
- Reflection process known as Grover iteration

## How to Reflect
- Can build a circuit to negate only |0>...|0>
- Use "phase trick" to simplify reflections, example in text is to create H|1> then use a control gate firing on |0>...|0>
- The oracle box C_s reflects across an arbitrary state |s>
- To reflect across E, first undo the superposition, reflect about |0>...|0>, then redo the superposition
- Probability of getting s upon measurement is cos^2(delta) = 1 - sin^2(delta) = 1 - 1/N
- Use classical C_s to verify solution upon measurement, successive checks drive error probability vanishingly low
