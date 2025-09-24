# Assessing requirements to scale to practical quantum advantage
Summary: 

## Toward quantum applications with practical impact
- Fault-tolerant quantum computing needs OOMs more space

Requirements for scalable qubits (order 1 million):
1. Controllable, i.e. good error-correction
2. Fast (sub-microsecond operation)
3. Small (on the order of 10 microns)

## Resource Estimation
- Estimate using ISA as the intermediary
- Find # of ISA instructions emitted, and find physical resources needed for avg ISA instruction
Layers of quantum stack (similar to classical):
1. High-level language
2. Quantum IR
3. Logical ISA
4. Microcode (QEC)
5. Microarchitecture
6. Device Control

- Authors' framework can estimate qubit count, runtime, power draw
- Best max tolerable error rate for a QEC is 3%, hence error rates < 0.1% likely needed for practical use
- Connectivity greatly hurts thresholds of some codes
- Some 2D codes like surface code can maintain 1% threshold with 2D connectivity
- Recall that the estimator is two-part: first part is frontend compilation to quantum IR, which the estimator then can lower to an ISA and give logical qubit estimates
- Second part gives physical qubit parameters and then does a bottom-up analysis of hardware resources needed to realize ISA code
- Have to translate abstract QIR to the ISA while respecting the topology of the qubits
- Usable QC needs decoherence times much longer than gate op time


