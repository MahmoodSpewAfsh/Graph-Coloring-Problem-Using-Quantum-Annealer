# Graph Coloring with QUBO on D-Wave Quantum Annealer

This repository contains a Python implementation for generating the QUBO model for the graph coloring problem and solving it using D-Wave's quantum annealer.

## Overview

The graph coloring problem involves assigning colors to the vertices of a graph such that no two adjacent vertices share the same color. This implementation uses a Quadratic Unconstrained Binary Optimization (QUBO) model to encode the problem and solve it using D-Wave's quantum annealer.

## Theoretical Discussion

### Graph Coloring Problem

The graph coloring problem can be formulated as follows:
- **Input**: A graph \( G = (V, E) \) and an integer \( k \) representing the number of colors.
- **Output**: An assignment of colors to the vertices such that no two adjacent vertices share the same color.

### QUBO Formulation

To encode the graph coloring problem as a QUBO problem, we introduce binary variables $ \( x_{vi} \) $ where $ \( x_{vi} = 1 \) $ if vertex \( v \) is assigned color $ \( i \) $, and $ \( 0 \) $ otherwise.

#### Constraints

1. **Each Vertex Must Have Exactly One Color**:
   - For each vertex \( v \), the sum of all color assignments should be exactly 1:
    $$ \[
     \sum_{i=0}^{k-1} x_{vi} = 1
     \] $$
   - This can be encoded in the QUBO model with a penalty term:
    $$ \[
     A \left( 1 - \sum_{i=0}^{k-1} x_{vi} \right)^2
     \] $$

2. **Adjacent Vertices Must Have Different Colors**:
   - For each edge \( (u, v) \) and each color \( i \), adjacent vertices \( u \) and \( v \) should not both be assigned the same color:
    $$ \[
     x_{ui} + x_{vi} \leq 1
     \] $$
   - This can be encoded in the QUBO model with a penalty term:
    $$ \[
     B x_{ui} x_{vi}
     \] $$

#### QUBO Model

Combining the constraints, the QUBO model can be expressed as:
$$ \[
\text{Minimize} \quad \sum_{v \in V} \left[ A \left( 1 - \sum_{i=0}^{k-1} x_{vi} \right)^2 \right] + \sum_{(u, v) \in E} \sum_{i=0}^{k-1} B x_{ui} x_{vi}
\] $$

## Files

- `generate_qubo.py`: The main Python script that generates the QUBO model for the graph coloring problem.

## Requirements

- Python 3.6+
- `networkx`
- `numpy`
- `dimod`
- `dwave-ocean-sdk`
- `matplotlib`

You can install the required packages using the following command:

```bash
pip install networkx numpy dimod dwave-ocean-sdk matplotlib
