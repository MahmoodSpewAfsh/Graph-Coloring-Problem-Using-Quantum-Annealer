# Graph-Coloring-Problem-Using-Quantum-Annealer
This repo is created for the implementation of Graph Coloring Problem using D'wave Qauntum Annealer for QCISBU class


# Graph Coloring with Ising Model on D-Wave Quantum Annealer

This repository contains a Python implementation for solving the graph coloring problem using an Ising model and D-Wave's quantum annealer.

## Overview

The graph coloring problem involves assigning colors to the vertices of a graph such that no two adjacent vertices share the same color. This implementation uses an Ising model formulation to encode the problem and solves it using D-Wave's quantum annealer.

## Files

- `graph_coloring.py`: The main Python script that defines the graph, constructs the Ising model, submits it to the D-Wave quantum annealer, and visualizes the solution.

## Requirements

- Python 3.6+
- `networkx`
- `numpy`
- `matplotlib`
- `dwave-ocean-sdk`

You can install the required packages using the following command:

```bash
pip install networkx numpy matplotlib dwave-ocean-sdk
