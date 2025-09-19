# Quantum Random Walks - an introductory overview
Summary: An expository article on quantum random walks

## Introduction
- Consider a system of one particle with varying position and spin (spin \otimes pos)
- If time evolution tells the particle to move in either direction depending on its spin, measuring the spin forces the particle to the left or right depending on what the spin collapses to
- Repetition of measurement produces a random walk
- In this example, we are completely similar to a classical random walk

- Can modulate the distance by rotating the basis we measure in (or equiv, rotating the spin state)
- Note that avg and variance are unchanged, we are just "re-weighting"

## The QRW
- We want behavior like above but with only one measurement
- We discretize the particle's position; it now moves along a lattice so it is computationally tractable
- Choose Z or Z/n as state space, also have a "coin space" which can be modelled as a qubit
- Hadamard gate is one choice of "coin" to apply to weight the spin possibilities
- Quantum random walk over N steps is U^N, for U = S(C \otimes I) where S is the position transform and C is the "coin" transform
- QRW is NOT symmetric, position drifts left due to interference
- Starting the walk in superposition spin state fixes this
- Still, distribution is bimodal and does not converge to Gaussian like in classical case
- In classical case a random walk is always absorbed by a boundary and never escapes to infinity...
- QRW with Hadamard Coin escapes origin with p = 1-2/pi?!
- "DFT" coin works in general d-regular graphs, traverses each edge with even probability
- Hamming cube walk (classical) can be reduced to a line walk (quotient out by hamming distance from 0)

- Continuous time walk has no "coin space" at all
- Think of continuous-time markov chains in classical case, have transition matrix
- In QRW, we use a matrix exponential of an infinitesimal hamiltonian
- Expected hitting time to cross G_n has exponential factor diff between classical and quantum

## Random Walks in CS
- Iterating random walks can probabalistically solve s-t connectivity
- Random walks give an O(n^2) algo for 2-SAT
- In general, efficiency of random walk algo is related to hitting time of solution
- Mixing time measures # of iterations until we are epsilon-close to stationary distribution
- Logically complete gateset for quantum computers is all of the 2x2 rotations along with CNOT

- Unitary time evolution implies that QRWs don't converge to a stationary distribution, as this would discard information
- Cesaro limit lets us workaround
- Mixing time in quantum case depends on all eigenvalues rather than just 2nd largest in classical
- Quadratic speedup for circular random walk (Z/n)
- Hitting time in quantum case depends on occasional measurement
- Authors raise idea of "graph tomography" by finding order of hitting time

## Physical Implementation
- Ion trap can be used to realize a state space like Z
- Optical lattice could realize Z or Z/n, could potentially perform hundreds of iterations

## Decoherence
- Classical walk recovered from QRW by measuring constantly (decohering the state): can we go "halfway" between the two?
- Can measure with probability p on each step
- But distribution is approximately classical unless p is very small (< 1/N)
- A better way is to alternate between different coin spaces, gives more gradual transition
