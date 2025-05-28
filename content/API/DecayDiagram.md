+++
title = 'nudca.decay_diagram'
weight = 5
+++


{{% notice style="info" icon="fa fa-project-diagram" %}}
This page documents the `decay_diagram.py` module, which provides visualization and analysis tools for nuclide decay chains. It is part of the NuDCA (Nuclear Decay Chain Astrophysics) package.
{{% /notice %}}

## Overview

The `DecayDiagram` class enables the construction and visualization of nuclear decay chains and their reverse (parent) relationships using `networkx` and `matplotlib`. It provides methods to query decay properties and plot decay diagrams for any nuclide in a given decay database.

---

## Class: `DecayDiagram`

Represents a decay diagram for a specific nuclide, providing methods to visualize decay chains and reverse decay chains.

### Constructor
```python
DecayDiagram(nuclide: str, decay_database)
```
- **nuclide** (`str`): Nuclide symbol (e.g., 'U-238').
- **decay_database** (`DecayDatabase`): Instance containing decay data.

---

## Properties

| Property           | Type                | Description                                      |
|--------------------|---------------------|--------------------------------------------------|
| `half_life`        | float or str        | Half-life of the nuclide (various units).        |
| `progeny`          | list[str]           | Daughter nuclides of the nuclide.                |
| `branching_ratios` | list[float]         | Branching ratios for all decay modes.            |
| `decay_modes`      | list[str]           | Decay modes for the nuclide.                     |

---

## Methods

### `find_parents`
```python
def find_parents(self, nuclide: str) -> List[str]
```
Find all possible parent nuclides that can decay to the given nuclide.

### `get_decay_info`
```python
def get_decay_info(self, parent: str, daughter: str) -> Optional[Tuple[str, float]]
```
Get decay mode and branching ratio between a parent and daughter nuclide.

### `plot_decay_chains`
```python
def plot_decay_chains(self, ...)
```
Plot the decay chains starting from the nuclide. Returns a matplotlib Figure and Axes.

### `plot_reverse_decay_chains`
```python
def plot_reverse_decay_chains(self, ...)
```
Plot the reverse decay chains (parents) for the nuclide. Returns a matplotlib Figure and Axes.

### `plot`
```python
def plot(self, digraph, max_generation, max_xpos, ...)
```
Plot a custom decay diagram using a provided networkx DiGraph.

---

## Example Usage

```python
from nudca.decay_database import load_decay_database
from nudca.decay_diagram import DecayDiagram

db = load_decay_database("ENDF-B-VIII.1_decay")
diagram = DecayDiagram("U-238", db)

# Plot decay chains
diagram.plot_decay_chains()[0].show()

# Plot reverse decay chains
diagram.plot_reverse_decay_chains()[0].show()
```

---

## Notes
- Requires `networkx` and `matplotlib` for plotting.
- Decay data must be provided via a compatible `DecayDatabase` instance.
- See inline docstrings in the source code for advanced plotting options.

---

## See Also
- [DecayDatabase API](./DecayDatabase/)
- [DecayMatrix API](./DecayMatrix/)

