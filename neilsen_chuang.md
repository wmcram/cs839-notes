# Neilsen and Chuang

## Chapter 7 - Physical Realization
### 7.1 - Guiding Principles
- Interactivity tradeoff: want our physical qubits to be safe from outside influence but this makes them harder to measure
- Number of ops for a physical qubit given by decoherence time over op time
- Ion trap has the highest ratio at time of writing at 1e13, but this doesn't account for all desirable factors

### 7.2 - Conditions for Quantum Computation
- Four requirements for quantum computation:
1. Represent quantum information in a noise-resistant way
2. Perform some "complete" set of unitary operations
3. Prepare a base initial state
4. Measure the output

- Set of accessible states should be finite, discrete rather than continuous
- Idealized infinite potential well restricted to two lowest energy states forms a qubit
- Spins and CNOTs are a universal set
- ...But any imperfection in our unitary transforms causes decoherence
- Example of initial state prep: cool ions into their ground state
- Example of qubit measurement: check fluorescence of (possibly) excited atom

## Chapter 10 - Quantum Error Correction
### 10.1 - Introduction
- A binary symmetric channel flips a bit with probability 0 < p < 1
- Copying a bit to three adds redundancy and can protect if one bit is flipped provided p is low (majority voting)
- prob that 2 or 3 bits flipped is 3p^2(1-p) + p^3 = 3p^2 - 2p^3. Note that this is only better than p when p < 1/2.
- Doesn't necessarily work for quantum information due to no-cloning theorem, continuous error range, and destructive measurement
- In a quantum system, model the channel as applying X with probability 0 < p < 1
- Encode a|0> + b|1> as a|000> + b|111>
- Make projections for each of the four "error syndromes"
- Upon detecting a certain error, flip it back to the proper state. This then gives same probability of transmission as the classical case.
- The above works for discrete bit flips, what about continuous errors?
- Fidelity between pure and mixed state defined as sqrt(<\psi|\rho|\psi>), maximizes at 1
- Can also have a phase flip (Z gate) with chance 1-p
- Using Hadamard we can just change into the |+>,|-> basis and use the bit flip encoding above
- Two channels are "unitarily equivalent": channels have same action up to hermitian conjugation (UCU^dag)

### 10.2 - The Shor Code
- Shor code protects against arbitrary single-qubit errors
- Built by composing phase flip code with one bit flip code for each qubit. Produces entangled pairs
- The composition here allows us to correct from stuff like bit flip AND phase flip
- In fact, protects against any error: extension by linearity and decomposing the noise into an operator sum
  shows that the above corrections actually correct every effect in the composition.

