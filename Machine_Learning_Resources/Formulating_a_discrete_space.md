# Representing Tensor Networks as a Searchable Space
## Defining a Problem
The contraction of a tensor network can be optimized by changing the order in which contractions occur. The problem the algorithm must address is finding the contraction order with the lowest computation cost, this is known as a tensor network contraction order (TNCO) problem. 

## Representing the Problem
To search a space, the problem must be represented so that the RL agent can quantitatively evaluate the cost of the contraction. Our method for doing this utilized a K-spin ising model, with a Hamoltonian evaluating the computational cost of the current configuration. 

The ising model is represented by a two-dimensional rectangular matrix, with rows corresponding to steps in the contraction process and columns corresponding to tensors present in the contracting network. The matrix values are binary variables $x$ that represent the presence of a tensor in a current contraction step. 

This ising model matrix represents the problem in a quantitative way that a cost function Hamiltonian can measure. 

## Evaluating a configuration
We use the following cost functon to evaluate the current configuration of the ising model matrix: 

![Cost Function Figure](https://github.com/RPIQuantumComputing/RLForQuantumCircuits/blob/main/Machine_Learning_Resources/Figures/Cost_Function_Fig.png?raw=true "Cost Function Visualization")

In the function, the outermost sum refers to indexing through every step of the contraction step. The first term of the inner part of the sum indexes through the current row up to $N-i$, representing how with each step less thensors are presen in the network. As it indexes through the current row, it will add the value of the binary variable $x$ to the sum. If it is greater than or less than two, additional cost will be added to the function. This serves to punish the algorithm for including more or less than two tensors in any contraction step. 

The second term of the inner part of the sum indexes through the row twice to test every possible pair of tensors in the step. If both tensors are present, $J$ will be added to the sum, where $J$ represents the cost of the tensor contraction. 

The goal of the RL agent is to optimize this function towards its lowest possible value. 



