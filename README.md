# QuantumSuperdenseCoding

Quantum computing is a revolutionary field that combines principles of quantum mechanics with computer science. It leverages quantum phenomena such as superposition, interference and entanglement to perform calculations in ways that are fundamentally different from classical computing. This enables quantum computers to solve certain problems faster than classical computers.

## Table of Contents
- [Quantum vs Classical Computing](#quantum-vs-classical-computing)
- [Quantum Measurements](#quantum-measurements)
- [Quantum Gates](#quantum-gates)
- [Quantum Superdense Coding](#quantum-superdense-coding)
- [Resources](#resources)

## Quantum vs Classical Computing
Classical computers operate using bits, which can represent either a 0 or a 1. Quantum computers, on the other hand, use quantum bits or qubits, which can be in a superposition of both 0 and 1 simultaneously. This property allows quantum computers to perform parallel computations and explore multiple solutions simultaneously, leading to potential exponential speedup in certain algorithms.

Mathematically, a qubit can be represented as a linear combination of the basis states |0⟩ and |1⟩. We can write the state of a qubit as:

|ψ⟩ = α|0⟩ + β|1⟩



Here, α and β are complex numbers, known as probability amplitudes. The probability of measuring the qubit in state 0 is given by |α|^2, and the probability of measuring it in state 1 is |β|^2. The sum of the squared magnitudes of the probability amplitudes must equal 1, ensuring that the qubit is normalized.

## Quantum Measurements
In quantum computing, measurement plays a crucial role. When a qubit is measured, its state collapses to either 0 or 1 with a certain probability. The probability of obtaining a specific measurement outcome is given by the squared magnitude of the probability amplitude associated with that outcome.

For example, if we have a qubit in the state |ψ⟩ = α|0⟩ + β|1⟩, the probability of measuring it in state 0 is |α|^2, and the probability of measuring it in state 1 is |β|^2.

During the computation, a qubit can be in a superposition, existing in a combination of both 0 and 1 states. However, when a measurement is performed on the qubit, it collapses into either 0 or 1 with probabilities determined by the amplitudes α and β. The measurement outcome is probabilistic, meaning that repeated measurements on the same qubit will yield different results according to the probabilities associated with each state.

It is important to note that the act of measurement disturbs the quantum state of the qubit, leading to the collapse of the superposition. This property is a defining characteristic of quantum computing and allows for the extraction of classical information from quantum systems.


## Quantum Gates
Quantum gates are operations that act on qubits and manipulate their state. These gates can be visualized as rotations or transformations on the Bloch sphere, which is a geometrical representation of the qubit states.
To explore and visualize quantum gates interactively, you can use this [link](https://javafxpert.github.io/grok-bloch/).
Here are some commonly used quantum gates:

### X Gate
The X gate, also known as the Pauli-X gate, is a quantum gate that flips the state of a qubit. It can be represented as a rotation around the X-axis on the Bloch sphere. Mathematically, it can be applied to an arbitrary state as follows:

X|ψ⟩ = |1⟩⟨0|ψ⟩ + |0⟩⟨1|ψ⟩



### H Gate
The Hadamard gate, represented as H, is a quantum gate that puts a qubit into a superposition state. It can be visualized as a rotation around the X-axis, followed by a rotation around the Z-axis on the Bloch sphere. Mathematically, it can be applied to an arbitrary state as follows:

H|ψ⟩ = 1/√2 (|0⟩⟨0|ψ⟩ + |1⟩⟨1|ψ⟩) + 1/√2 (|0⟩⟨1|ψ⟩ - |1⟩⟨0|ψ⟩)



### Z Gate
The Z gate is a quantum gate that introduces a phase flip on the qubit. It can be visualized as a rotation around the Z-axis on the Bloch sphere. Mathematically, it can be applied to an arbitrary state as follows:

Z|ψ⟩ = |0⟩⟨0|ψ⟩ - |1⟩⟨1|ψ⟩



### CNOT Gate
The CNOT gate, also known as the controlled-X gate, is a two-qubit gate that performs an X gate (bit flip) operation on the target qubit based on the state of the control qubit, it can be applied to an arbitrary two-qubit state as follows:

CNOT(|a⟩⊗|b⟩) = |a⟩⊗|a⊕b⟩

Here, ⊕ denotes addition modulo 2.

The CNOT gate can be used to create entanglement between qubits. When the control qubit is in a superposition state, the CNOT gate entangles the control qubit with the target qubit. This entanglement enables quantum information processing tasks such as Superdense Coding and Quantum Teleportation.


## Quantum Superdense Coding
Superdense Coding is a protocol in quantum information theory that allows two classical bits of information to be transmitted using only one qubit of communication. It exploits the entanglement and quantum properties of qubits to achieve this compression.

### Protocol Steps

1. **Initialization**: Alice and Bob start with a pair of entangled qubits, known as a Bell pair or an EPR pair. The Bell pair is created as follows:
   - Alice prepares a qubit in the |0⟩ state.
   - Alice applies the X gate (bit flip) to her qubit.
   - Alice applies the H gate (Hadamard gate) to her qubit.
   - Alice sends her qubit to Bob.

   After these steps, Alice's qubit is entangled with Bob's qubit, forming the Bell pair:

   |Φ+⟩ = (1/√2)(|00⟩ + |11⟩)

2. **Encoding**: Alice wants to send the bits 01 to Bob. She applies the corresponding quantum gates to her qubit A based on the bit values:
   - If the first bit is 0, Alice does nothing (applies the identity gate).
   - If the first bit is 1, Alice applies the Pauli-X gate (bit flip) to her qubit A.
   - If the second bit is 0, Alice does nothing.
   - If the second bit is 1, Alice applies the Pauli-Z gate (phase flip) to her qubit A.

3. **Communication**: Alice sends her qubit A to Bob.

4. **Decoding**: Upon receiving the qubit A from Alice, Bob performs a series of operations on his qubit B to decode the message:
   - Bob applies a CNOT gate with qubit B as the control qubit and qubit A as the target qubit.
   - Bob applies a Hadamard gate to qubit B.
   - Bob performs measurements on both qubits B and A.

5. **Measurement and Interpretation**: Based on the measurement outcomes, Bob can determine the two classical bits sent by Alice:
   - If Bob measures both qubits B and A to be 00, it means the bits sent by Alice were 00.
   - If Bob measures both qubits B and A to be 01, it means the bits sent by Alice were 01.
   - If Bob measures both qubits B and A to be 10, it means the bits sent by Alice were 10.
   - If Bob measures both qubits B and A to be 11, it means the bits sent by Alice were 11.


By utilizing the shared entangled state and the appropriate quantum gates, Alice can encode information into the state of her qubit, which then allows Bob to decode and retrieve the original information upon measurement.

The beauty of quantum superdense coding lies in the use of entanglement and quantum gates to enable more efficient communication, surpassing the classical limitations of one classical bit per one qubit.

For an interactive example and implementation of Superdense Coding, you can check out the [Superdense Coding Jupyter Notebook](./quantum_communication.ipynb).

## Introduction to Qiskit
Qiskit is an open-source framework for quantum computing developed by IBM. It provides a powerful and user-friendly interface to experiment with quantum circuits, simulate quantum systems, and run programs on real quantum computers.

To get started with Qiskit, follow these steps:

### Installation Guide
Make sure you have Python installed on your system, then you could use pip to install Qiskit by opening the terminal and run the following command:
```
pip install qiskit
```
### Defining a Quantum Circuit
In Qiskit, a quantum circuit is defined using the QuantumCircuit class. You need to specify the number of qubits the circuit will have. Here's an example of defining a quantum circuit with 2 qubits:
```
from qiskit import QuantumCircuit

# Define a quantum circuit with 2 qubits
qc = QuantumCircuit(2)
```
### Applying Gates
Quantum gates are applied to the quantum circuit to manipulate the qubits' state. To apply a gate, you need to call the corresponding method on the circuit object and specify the qubit(s) to which the gate should be applied. Here's an example of applying the H gate (Hadamard) to Qbit 1:
```
qc.h(1)  # Apply Hadamard gate to qubit 1
```
### Measuring Qubits
Measurement is a crucial step in quantum computing. It allows us to extract classical information from quantum systems. To measure qubits in Qiskit, we use the measure_all() method. This method automatically measures all the qubits in the circuit and maps them to classical bits. Here's an example:
```
# Measure all qubits in the circuit
qc.measure_all()
```
### Visualizing the Circuit State
Qiskit provides visualization tools to understand and analyze the quantum circuit state. To visualize the circuit state using the Bloch sphere representation, you need to execute the circuit, obtain the statevector, and then use the draw method. Here's an example:
```
from qiskit import execute, Aer
from qiskit.quantum_info import Statevector
from qiskit.visualization import plot_bloch_multivector

# Execute the circuit and obtain the statevector
simulator = Aer.get_backend('statevector_simulator')
job = execute(qc, simulator)
state = Statevector(job.result().get_statevector())

# Display the Bloch sphere representation of the state
state.draw('bloch')
```
## Resources
Here are some helpful resources to learn more about quantum computing:

- [Qiskit Documentation](https://qiskit.org/documentation): The official documentation for Qiskit, an open-source framework for quantum computing developed by IBM.

- [Wikipedia - Quantum Computing](https://en.wikipedia.org/wiki/Quantum_computing): A comprehensive overview of quantum computing concepts and technologies.

- [YouTube - Introduction to Quantum Computing](https://youtu.be/F_Riqjdh2oM): A video introduction to the basics of quantum computing.
