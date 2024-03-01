# Representing the Quantum Fourier Transform Classicaly with Tensor Networks

## Section One: Introducing the Quantum Fourier Transform Circuit

The Quantum Fourier Transform (QFT) is an operation ran on a multip-qubit system, which reveals the basis states that make up the combined state of the system. The QFT process is analogous to how the Discrete Fourier Transform (DFT) tests the different harmonics that represent a data set with a periodic nature. The QFT uses Hademard gates and Controlled Phase Shift Rotation (CPSR) gates to alter the final state vector of each qubit in the circuit. 

### CPSR Gates
The CSPR gate utilizes a control qubit and a target qubit, shifting the target qubit's phase relative to the distance between the control and target qubit. This operation results in the entangling of the two qubits involved in the gate.

Below is the matrix representation of the CPSR gate in a hypothetical three-qubit system: <br>
<div align="center">

![CPSR GATE](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/QFT_Intro_branch/QFT_Intro_Folder/Screenshot%202024-03-01%20145625.png?raw=true)
<br>

</div>
The identity matrix for qubits one and three is present to ensure only the second qubit is affected by the CPSR gate. This highlights that the control qubit in this gate remains unchanged. 

### Hadamard Gate
The Hadamard gate is used to alter the state vector of a qubit so that it represents an equal superposition of states 0 and 1. 

Below is the matrix representation of a Hademard gate on the first qubit in a hypothetical three-qubit system:<br>
<div align="center">

![HADAMARD GATE](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/QFT_Intro_branch/QFT_Intro_Folder/Screenshot%202024-03-01%20145744.png?raw=true)

</div>
Similar to the CPSR gate, the identity matrices are present to ensure only the targetted qubit is affected.

### Circuit Visualization
![QFT Circuit](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/QFT_Intro_branch/QFT_Intro_Folder/QFT%20CIcuit.jpg?raw=true)

In this three-qubit circuit, the "H" gates represent Hademard gates, and the "Z" gates represent the CPSR gates. The black dots on a CPSR gate indicate the control qubit, and the "Z" represents the target qubit. The sequential nature of the QFT is illustrated by the amount of Z gates each qubit controls. Each qubit in the QFT controls $N-k$ qubit rotations, where $N$ represents the number of qubits in the system, and $k$ represents the rank of the qubit in the system, starting at 1 for $k \leq N$. This pattern can be seen in the final state of eac qubit, which includes an array that shows each qubit that influnced the final state vector of said qubit. 

## Section Two: Representing the QFT as a Tensor Network. 

The classical simulation of the QFT can be represented as a tensor network that contracts towards $N$ state vectors, where $N$ is the number of qubits in the QFT circuit. 

The image below represents the tensor network visualization of a classically simulated QFT circuit:

![QFT TENSOR TREE](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/QFT_Intro_branch/QFT_Intro_Folder/QFT%20TENSOR%20TREE.jpg?raw=true)

This visualization takes on a tree structure to emphasize which qubit is the control qubit in each sequence of CPSR gates, by assiging different levels of depth in the tree to a specific control qubit. The purpose of this visualization is to link the QFT to its close counterpart, the Fast Fourier Transform (FFT), by encapsulating the sequential nature of the QFT. 

Alternatively, the QFT tensor network can be represented linearly to emphasize the flow of contraction in the network:

![LINEAR QFT NETWORK](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/QFT_Intro_branch/QFT_Intro_Folder/QFT%20TENSOR%20NETWORK%20TWO.jpg?raw=true)

This visualization follows a left-to-right flow of contraction and does a better job at representing entanglement. 

## Section Three: Reinforcement Learning (RL) Applications
Representing the classical simulation of the QFT circuit as a tensor network makes it easier for RL algorithms to optimize the simulation of QFT; tensor networks allow the RL algorithm to approach the optimization task as a tensor network contraction order (TNCO) problem. 

Using methods similar to those highlighted in Xiao-Yang Liu's paper *Classical Simulation of Quantum Circuits: Parallel Environments and Benchmark*, an RL model can search through the tesnor network and find ways to reduce the number of computations. 
