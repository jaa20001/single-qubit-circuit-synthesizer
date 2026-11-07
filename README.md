# Single-Qubit Circuit Synthesizer

## Project Overview

A Python program that automatically synthesizes a single-qubit unitary matrix into a Qiskit quantum circuit using ZYZ Euler decomposition.

## Features

- Validates 2×2 unitary matrices
- Extracts and restores global phase
- Computes ZYZ Euler rotation angles
- Handles special cases where β = 0 or β = π
- Generates Qiskit quantum circuits
- Verifies the synthesized circuit against the original matrix

## Requirements

- Python
- NumPy
- Qiskit
- Qiskit visualization dependencies (for circuit drawings)

## Usage

```python
import numpy as np
from qiskit.quantum_info import Operator

U = np.array([[0, -1], [1, 0]], dtype=complex)

qc = synthesize_single_qubit(U)

print(np.allclose(U, Operator(qc).data))
print(qc.draw())
```

Expected result: `True`

## Mathematical Background

The synthesizer decomposes a unitary matrix into:

\[
U = e^{i\gamma}R_z(\alpha)R_y(\beta)R_z(\delta)
\]

The rotation angles are extracted from the matrix elements, and the resulting circuit is verified numerically.

## Test Cases

- Identity gate
- Pauli-X gate
- S gate
- Ry(π)
- Rz(π/3)
- General U(2) matrix with nonzero global phase

All listed cases have been checked during development.
