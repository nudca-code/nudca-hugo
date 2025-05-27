+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'DecayMatrix'
weight = 6
+++

# DecayMatrix API Reference

{{% notice style="info" icon="fa fa-atom" %}}
This page documents the `decay_matrix.py` module, which provides core data structures and utilities for nuclide decay chain calculations. It is part of the NuDCA (Nuclear Decay Chain Astrophysics) package.
{{% /notice %}}

## Overview

The `decay_matrix.py` module defines classes and functions to construct, store, and manipulate decay matrices for nuclear decay networks. It is designed for scientific computing and supports analytical and numerical solutions to the Bateman equations.

---

## Main Classes

### `DecayMatrix`

Represents the decay matrix and related structures for nuclide decay calculations.

**Attributes:**
- `decay_constants`: `np.ndarray` — Array of decay constants for each nuclide.
- `matrix_P`: `scipy.sparse.csc_matrix` — Transformation matrix for Bateman solutions.
- `matrix_P_inv`: `scipy.sparse.csc_matrix` — Inverse of transformation matrix P.
- `initial_abundance`: `np.ndarray` — Initial abundance vector (default: zeros).
- `matrix_Lambda`: `scipy.sparse.csc_matrix` — Diagonal matrix for decay constants (default: zeros).

**Methods:**
- `__init__(decay_constants, matrix_P, matrix_P_inv)` — Initialize with decay constants and transformation matrices.
- `__repr__()` — String representation.
- `__eq__(other)` — Equality comparison.
- `__ne__(other)` — Inequality comparison.

---

### `MatrixBuilder`

Builds matrices representing the decay of nuclides based on decay constants, branching ratios, and decay chains.

**Attributes:**
- `decay_database`: `DecayDatabase` — Database containing nuclide decay data.

**Properties:**
- `nuclides` — List of nuclides.
- `nuclide_index_map` — Mapping of nuclide names to indices.
- `matrix_size` — Number of nuclides.

**Key Methods:**
- `build_decay_matrix()` — Returns transformation matrix P and its inverse.
- `build_matrix_A()` — Constructs the decay matrix A (rates between nuclides).
- `build_matrix_P(matrix_A)` — Constructs the transformation matrix P.
- `build_matrix_P_inv(matrix_A, matrix_P)` — Constructs the inverse of P.
- `_check_identity()` — Checks if P and P_inv form an identity matrix.

---

## Utility Functions

- `serialize_decay_matrix(data_source='ENDF-B-VIII.1_decay')`
  - Saves the decay matrix P and its inverse to disk as `.npz` files.
- `load_decay_matrix(data_source='ENDF-B-VIII.1_decay') -> DecayMatrix`
  - Loads the decay matrix P and its inverse from disk and returns a `DecayMatrix` object.
- `_csc_matrix_equal(matrix_a, matrix_b)`
  - Helper to compare two sparse matrices for exact equality.

---

## Usage Example

```python
from nudca.decay_matrix import load_decay_matrix

decay_matrix = load_decay_matrix()
print(decay_matrix)
# Access transformation matrices:
P = decay_matrix.matrix_P
P_inv = decay_matrix.matrix_P_inv
```

---

## Notes
- The module relies on SciPy sparse matrices for efficient storage and computation.
- Decay data is loaded from a `DecayDatabase` (see related documentation).
- The Bateman solution is supported via transformation matrices P and P_inv.

---

## See Also
- [DecayDatabase API](./DecayDatabase/)

