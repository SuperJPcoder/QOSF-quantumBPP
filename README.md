# Bin Packing Problem Optimization using Quantum Computing

## Project Overview

This project tackles the classic **Bin Packing Problem (BPP)** using quantum computing. The goal is to minimize the number of bins required to pack items of varying weights. We employ classical ILP methods and transform them into Quadratic Unconstrained Binary Optimization (QUBO) models to leverage quantum computing methods like Quantum Annealing and the Quantum Approximate Optimization Algorithm (QAOA).

## Objectives

### 1. Integer Linear Programming (ILP) to Quadratic Unconstrained Binary Optimization (QUBO)
- **Description**: Start with a classical ILP model for the Bin Packing Problem and convert it into a QUBO representation.
- **Steps**:
  - Define the ILP for BPP, including variables, constraints, and the objective function.
  - Implement a QUBO transformation function and test it with different problem sizes (small, medium, large).

### 2. Brute-Force QUBO Solver
- **Description**: Implement a baseline brute-force solution for the QUBO problem.

### 3. Quantum Annealing Solver
- **Description**: Solve the QUBO model using D-Wave’s Ocean framework for quantum annealing.

### 4. Quantum Variational Solver
- **Description**: Explore multiple ansatz structures in a hybrid optimization to solve the QUBO problem.

### 5. Quantum Approximate Optimization Algorithm (QAOA)
- **Description**: Implement QAOA from scratch for the QUBO model and compare results with other approaches.

### 6. Results Analysis
- **Description**: Analyze and compare performance, accuracy, and scalability of quantum solutions versus classical methods.

## Code Structure

- **`ilp_to_qubo.py`**: Contains the ILP model and QUBO transformation functions.
- **`brute_force_solver.py`**: Implements the brute-force solution for the QUBO model.
- **`quantum_annealing_solver.py`**: Solves the QUBO problem using the D-Wave Ocean framework.
- **`variational_solver.py`**: Implements the variational quantum solver with multiple ansatz configurations.
- **`qaoa_solver.py`**: QAOA solution for the QUBO model.
- **`analysis.ipynb`**: Jupyter notebook for comparative analysis of results.

## Getting Started

### Prerequisites

- **Python 3.8+**
- **Qiskit** for quantum circuit creation
- **D-Wave Ocean SDK** for quantum annealing

### Installation

1. Clone the repository and install dependencies:

    ```bash
    git clone https://github.com/your-repo-link
    cd your-repo
    pip install -r requirements.txt
    ```

### Usage

1. **ILP to QUBO Transformation**: Generate a QUBO model from an ILP problem.

    ```bash
    python ilp_to_qubo.py
    ```

2. **Brute-Force QUBO Solver**: Run a brute-force solution of the QUBO model.

    ```bash
    python brute_force_solver.py
    ```

3. **Quantum Annealing Solver**: Solve the QUBO problem using quantum annealing.

    ```bash
    python quantum_annealing_solver.py
    ```

4. **Variational Quantum Solver**: Test with different ansatz configurations.

    ```bash
    python variational_solver.py
    ```

5. **QAOA Solver**: Run the QAOA solution for the QUBO model.

    ```bash
    python qaoa_solver.py
    ```

6. **Analysis**: View results and comparisons in `analysis.ipynb`.

## Results and Insights

- **Performance**: Runtime analysis of each approach based on problem size and number of qubits.
- **Accuracy**: Comparison of solution accuracy across classical and quantum methods.
- **Scalability**: Insights on practical limitations of quantum methods for larger problem sizes.

## References

- [D-Wave Ocean Documentation](https://docs.ocean.dwavesys.com/en/stable/)
- [Qiskit Optimization Documentation](https://qiskit.org/documentation/optimization/)
- [Quantum Approximate Optimization Algorithm (QAOA)](https://arxiv.org/abs/1411.4028)
