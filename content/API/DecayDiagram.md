+++
title = 'nudca.decay_diagram'
weight = 5
+++


{{% notice style="info" icon="fa fa-project-diagram" %}}
This page documents the `DecayDiagram` class from `nudca.decay_diagram`, providing tools to visualize decay chains and reverse decay chains for nuclides.
{{% /notice %}}

---

## Overview

`DecayDiagram` represents a decay diagram for a specific nuclide, offering methods to visualize decay chains and reverse decay chains using `networkx` and `matplotlib`. It provides both programmatic access to decay data and publication-quality plotting.

---

## Class: DecayDiagram

```python
from nudca.decay_diagram import DecayDiagram
```

### Constructor
```python
DecayDiagram(nuclide: str, decay_database: DecayDatabase)
```
- **nuclide**: Nuclide symbol or string (e.g., 'Ni56', 'U-238')
- **decay_database**: An instance of `DecayDatabase` containing decay data

---

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `nuclide` | `str` | Standardized nuclide symbol |
| `half_life` | `str` or `float` | Half-life in readable format (default) or seconds |
| `progeny` | `list[str]` | List of daughter nuclides |
| `branching_ratios` | `list[float]` | Branching ratios for each decay mode |
| `decay_modes` | `list[str]` | Decay modes for the nuclide |

---

## Methods

### find_parents
```python
def find_parents(nuclide: str) -> List[str]
```
Find all possible parent nuclides that can decay to the given nuclide.
- **nuclide**: Daughter nuclide symbol
- **Returns**: List of parent nuclide symbols

### get_decay_info
```python
def get_decay_info(parent: str, daughter: str) -> Optional[Tuple[str, float]]
```
Get decay information (mode and branching ratio) between a parent and daughter nuclide.
- **parent**: Parent nuclide symbol
- **daughter**: Daughter nuclide symbol
- **Returns**: Tuple `(decay_mode, branching_ratio)` if found, else `None`

### plot_decay_chains
```python
def plot_decay_chains(label_pos=0.3, fig=None, axes=None, kwargs_draw=None, kwargs_edge_labels=None) -> (Figure, Axes)
```
Plot the decay chains starting from the nuclide.
- **label_pos**: Position of edge labels along the edge (default 0.3)
- **fig, axes**: Optional matplotlib figure/axes
- **kwargs_draw**: Additional keyword arguments for `nx.draw`
- **kwargs_edge_labels**: Additional keyword arguments for `nx.draw_networkx_edge_labels`
- **Returns**: Matplotlib `Figure` and `Axes`

### plot_reverse_decay_chains
```python
def plot_reverse_decay_chains(label_pos=0.3, fig=None, axes=None, kwargs_draw=None, kwargs_edge_labels=None) -> (Figure, Axes)
```
Plot the reverse decay chains (all parents) for the nuclide.
- Arguments as above
- **Returns**: Matplotlib `Figure` and `Axes`

### plot
```python
def plot(digraph, max_generation, max_xpos, label_pos=0.3, fig=None, axes=None, kwargs_draw=None, kwargs_edge_labels=None) -> (Figure, Axes)
```
Low-level method to plot a custom decay digraph. Used internally by the above methods.

---

## Usage Examples

```python
from nudca.decay_database import load_decay_database
from nudca.decay_diagram import DecayDiagram

db = load_decay_database()
decay_diagram = DecayDiagram('Ni56', db)

# Access decay data
print('Radionuclide:', decay_diagram.nuclide)
print('Half life:', decay_diagram.half_life)
print('Progeny:', decay_diagram.progeny)
print('Decay modes:', decay_diagram.decay_modes)
print('Branching ratios:', decay_diagram.branching_ratios)

# Plot decay chains
decay_diagram = DecayDiagram('Ni56', db)
fig, axes = decay_diagram.plot_decay_chains()
fig.tight_layout()
# plt.show()

# Plot reverse decay chains
decay_diagram = DecayDiagram('Fe56', db)
fig, axes = decay_diagram.plot_reverse_decay_chains()
fig.tight_layout()
# plt.show()
```

---

## Notes
- Requires `networkx`, `matplotlib`, and a valid `DecayDatabase` instance
- Plots are publication-quality and can be customized via `kwargs_draw` and `kwargs_edge_labels`
- Nuclide symbols are automatically standardized
- For advanced graph customization, use the `plot` method directly

---

## See Also
- [DecayDatabase API](../API/DecayDatabase/)
- [Nuclide API](../API/Nuclide/)
- [DecayMatrix API](../API/DecayMatrix/)
