# Quantum Cryptography: Public Key Distribution and Coin Tossing
Summary: 


## Quantum Crypto
- Uncertainty principle helps us make secure cryptosystems
- Secret key cryptosystems are not fully secure unless |key| >= |cleartext| and key is only used once

The text explains some basic quantum stuff using photon polarization as its "qubit".

- Bases are conjugate if each vector of the first has an equal length projection onto all vectors of the second
- "Trapdoor" functions used to conceal info from eavesdropper in public key crypto
- Quantum observation forces all eavesdropping to be active, disturbing the state
- If transmission is untouched, parties agree to use the random bits as a one time pad

1. Alice chooses random bit string and random sequence of bases (Z or X), sending photons (qubits) prepared in basis state to match the bitstring
2. Bob randomly decides for each photon which basis to measure in (=> Bob only gets the information from ~half of the bits)
3. Over a classical (info-immutable) channel, Bob reports bases of received bits
4. Alice says which bases were correct
5. Bob reveals some key bits at random to reach consensus
6. Finally, any leftover secret bits used in pad

## Quantum Coin Tossing
- Two untrusting parties want to verify a coin toss

1. Alice randomly chooses ONE basis and sequence of bits, sending encoded photons to Bob
2. Bob chooses a random basis to measure in for each photon and then guesses which basis Alice used
3. Alice certifies Bob's win/loss by sending the entire original bit sequence
4. Bob verifies by comparing Alice's sequence with his tables, should match 100% with Alice's basis and random with other

- Alice could potentially cheat with EPR effect
- Photon decay produces two entangled photons, measuring one forces other into opposite state
- Alice produces EPR pairs and sends Bob one member of each pair
- When Bob guesses, Alice measures stored photons in opposite basis and uses them to force a win
