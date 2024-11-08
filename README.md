# Bin Packing Problem (BPP) Quantum Solution

## Introduction

The **Bin Packing Problem (BPP)** is a well-known optimization problem where the objective is to pack a collection of items, each with a weight, into the minimum number of bins, subject to a maximum weight capacity for each bin. This problem has numerous applications in fields such as supply chain management, logistics, and manufacturing. In this repository, we apply various **quantum computing** approaches to solve the BPP, including:

1. **Integer Linear Programming (ILP) Formulation**.
2. **Transformation from ILP to QUBO**.
3. **Brute Force Solver**.
4. **Quantum Annealing** using D-Wave's Ocean framework.
5. **Quantum Variational Approaches**.
6. **Quantum Approximate Optimization Algorithm (QAOA)**.

## Task Overview

In this task, we are tasked with solving the BPP using quantum computing by:

1. Defining the **ILP formulation** of BPP.
2. Transforming the **ILP** into **QUBO** (Quadratic Unconstrained Binary Optimization) using a custom function.
3. Solving the QUBO using different methods:
   - **Brute Force**.
   - **Quantum Annealing**.
   - **Quantum Variational Approach** (with different ansatzes).
   - **Quantum Approximate Optimization Algorithm (QAOA)**.
4. Comparing the results of these approaches with the brute force solution.

## Problem Formulation

### 1. **ILP Formulation of BPP**

In the ILP formulation, we define binary decision variables for each item and each bin, where:
- **x(i, j) = 1** if item **i** is placed in bin **j**.
- **y(j) = 1** if bin **j** is used.

The objective is to minimize the number of bins used while respecting the weight constraints of each bin.

### 2. **Transforming ILP to QUBO**

The QUBO formulation is a binary optimization problem where the objective function is quadratic in terms of binary variables. The ILP constraints are translated into quadratic terms for binary decision variables.

### 3. **Brute Force Solver**

The brute force method exhaustively searches through all possible ways of packing the items into bins. Although this guarantees the optimal solution, it becomes computationally infeasible as the problem size grows.

### 4. **Quantum Annealing**

Using **D-Wave Ocean SDK**, we map the QUBO model onto the quantum annealer's hardware, leveraging quantum tunneling to potentially find a better solution to the QUBO problem.

### 5. **Quantum Variational Approach**

The **Quantum Variational Approach (QVA)** involves constructing a parameterized quantum circuit (ansatz) to explore the solution space. We test several ansatzes and use classical optimization techniques to tune the parameters and solve the QUBO.

### 6. **Quantum Approximate Optimization Algorithm (QAOA)**

**QAOA** is a hybrid quantum-classical algorithm that uses quantum circuits to explore solution spaces and classical optimization techniques to fine-tune parameters. We implement QAOA from scratch and solve the QUBO.

## Code Structure

- **bin_packing_ilp.py**: Contains the ILP formulation and a function to convert the ILP to QUBO.
- **bin_packing_qubo.py**: Implements the QUBO formulation.
- **brute_force_solver.py**: Brute force approach to solve the QUBO.
- **quantum_annealing_solver.py**: Implements quantum annealing using D-Wave Ocean.
- **variational_solver.py**: Implements quantum variational approaches.
- **qaoa_solver.py**: Implements QAOA from scratch.

## Requirements

To run the code, you'll need the following dependencies:

```bash
pip install qiskit dwave-ocean-sdk scipy docplex
```
## Results and Comparison

We compare the following methods:

### 1. **Brute Force**:
- The brute force approach exhaustively checks all possible configurations of item placements into bins. It guarantees an optimal solution but becomes computationally infeasible as the problem size increases due to its exponential time complexity.

### 2. **Quantum Annealing**:
- Using **D-Wave's Quantum Annealing** framework, the QUBO is mapped onto the quantum hardware, which attempts to find an optimal or near-optimal solution by exploiting quantum tunneling to escape local minima.
- The quantum annealer works by finding the lowest energy state in the Ising model representation of the QUBO, leveraging quantum mechanical effects.

### 3. **Quantum Variational Approach**:
- The **Quantum Variational Approach** combines quantum computing and classical optimization techniques. A parameterized quantum circuit (ansatz) is used to explore the solution space, and classical optimization techniques are employed to find the optimal parameters.
- Several ansatzes (e.g., hardware-efficient, variational forms like QAOA or custom forms) were tested, and their performance was compared.

### 4. **Quantum Approximate Optimization Algorithm (QAOA)**:
- **QAOA** is a hybrid quantum-classical algorithm. It uses quantum circuits to explore the solution space of the QUBO and classical optimization algorithms to adjust the parameters of the quantum circuit to improve the solution over time.
- The goal of QAOA is to find the best approximation to the solution by evolving the system's quantum state through parameterized gates, with the final state providing the solution.

### Analysis

1. **Brute Force**:
   - The brute force method guarantees the optimal solution but has **exponential time complexity**. As the problem size grows, the time taken to compute the solution increases drastically. For larger problem sizes, it becomes practically impossible to use brute force.

2. **Quantum Annealing**:
   - The quantum annealing approach benefits from the ability to explore a large solution space simultaneously, potentially escaping local minima faster than classical optimization techniques. The results depend on the problem's size and the annealing time, but quantum annealing typically provides approximate solutions in reasonable time for larger problems.
   - The quality of the solutions can vary, and it depends on how well the problem is mapped to the quantum annealer and the available hardware's capabilities.

3. **Quantum Variational Approach**:
   - The **variational approach** offers flexibility in choosing different ansatzes to explore the solution space. While this can be more efficient than brute force, it still requires careful tuning of parameters. Its performance heavily depends on the ansatz chosen and the classical optimizer used.
   - For some cases, variational methods can find solutions close to the optimal, but they still face challenges in ensuring global optimization, especially for large problem sizes.

4. **QAOA**:
   - **QAOA** is designed for combinatorial optimization problems like QUBO and is more scalable than brute force. It combines quantum circuits with classical optimization techniques. The performance of QAOA improves with deeper circuits and better optimization methods.
   - While QAOA can potentially offer better solutions than classical methods, its efficiency and solution quality depend on factors like the number of layers in the quantum circuit, the classical optimizer, and the problem's structure.

### How Do the Results Compare with the Brute Force Approach?

- **Brute Force** provides the optimal solution, but due to the exponential growth in complexity, it is not feasible for larger problems.
- The **Quantum Annealing** and **Quantum Variational Methods** provide approximate solutions much faster, and they perform well for larger instances of the problem. They have the potential to outperform classical methods for large problem sizes, especially when the problem space is large and complex.
- **QAOA** offers another promising quantum solution, balancing quantum circuit depth and classical optimization. It provides near-optimal solutions in much less time than brute force for large problem sizes.
- In general, **quantum methods** offer a significant advantage over brute force when the problem size increases, as they explore solution spaces efficiently, potentially providing solutions faster with good enough approximations.

## Conclusion

The results indicate that **quantum algorithms** such as Quantum Annealing, Variational Quantum Methods, and QAOA have the potential to outperform brute force for solving combinatorial optimization problems like the Bin Packing Problem, especially as the problem size grows. While quantum algorithms may not always provide exact solutions (depending on the approach), they often provide good approximations much faster than classical exhaustive search methods.
