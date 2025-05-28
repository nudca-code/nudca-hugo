+++
title = 'Nuclide'
weight = 3
+++

# Nuclide API Reference

{{% notice style="info" icon="fa fa-atom" %}}
This page documents the `nuclide.py` module, which provides data structures and utilities for representing and parsing nuclear nuclides. It is part of the NuDCA (Nuclear Decay Chains Astrophysics) package.
{{% /notice %}}

## Overview

The `nuclide.py` module defines the `Nuclide` class for representing nuclear nuclides, as well as supporting functions and exceptions for parsing, validating, and converting nuclide symbols, atomic numbers, and canonical IDs. It enables robust handling of nuclide data in scientific and engineering applications.

---

## Main Class: `Nuclide`

Represents a nuclear nuclide, providing properties for atomic number (Z), mass number (A), neutron number (N), metastable state, and canonical ID. Supports parsing from string or integer formats and provides equality/hash operations.

### Constructor
```python
Nuclide(nuclide: Union[str, int])
```
- **nuclide** (`str` or `int`): Nuclide symbol (e.g. 'U-235', '235U', 922350000) or canonical id.

---

### Properties

| Property   | Type   | Description |
|------------|--------|-------------|
| `Z`        | int    | Atomic number (number of protons). |
| `A`        | int    | Mass number (protons + neutrons). |
| `N`        | int    | Neutron number (A - Z). |
| `state`    | str    | Metastable state symbol ('' for ground, 'M', 'N', ...). |
| `id`       | int    | Canonical nuclide ID (zzzaaassss form). |
| `nuclide_symbol` | str | Standardized nuclide string (e.g. 'U-235'). |

---

### Key Methods

| Method | Description |
|--------|-------------|
| `__repr__()` | String representation of the nuclide. |
| `__eq__(other)` | Equality comparison. |
| `__ne__(other)` | Inequality comparison. |
| `__hash__()` | Hash function for use in sets and dicts. |

---

## Exception: `NuclideStrError`

Custom exception for invalid nuclide strings, providing context on the error.

---

## Utility Functions

| Function | Description |
|----------|-------------|
| `parse_nuclide(nuclide)` | Parse a nuclide string or canonical id to standardized format. |
| `Z_to_element(Z)` | Convert atomic number to element symbol. |
| `element_to_Z(element_symbol)` | Convert element symbol to atomic number. |
| `get_metastable_symbols()` | Get allowed metastable state symbols. |

---

## Usage Example

```python
from nudca.nuclide import Nuclide, parse_nuclide

n = Nuclide('U-235')
print(n.Z)  # 92
print(n.A)  # 235
print(n.state)  # ''
print(n.id)  # 922350000

# Parse from canonical id
n2 = Nuclide(922350000)
print(n2.nuclide_symbol)  # 'U-235'
```

---

## Notes
- Supports flexible parsing from various nuclide string formats and canonical IDs.
- Provides robust error handling for invalid nuclide representations.
- Includes mappings for all known elements and allowed metastable states.

---

## See Also
- [DecayDatabase API](./DecayDatabase/)
- [DecayMatrix API](./DecayMatrix/)
- [NucleoDecay API](./NucleoDecay/)
