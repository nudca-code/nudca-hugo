+++
title = "nudca.decay_database"
description = "Comprehensive API reference for nudca/decay_database.py"
weight = 4
+++

> This documentation covers the full API of `nudca/decay_database.py`. It is intended for developers and users who wish to integrate or extend the nuclear decay database functionalities.

{{% children %}}

---

## Table of Contents
- [Overview](#overview)
- [Main Classes & Functions](#main-classes--functions)
  - [DecayDatabase](#decaydatabase)
  - [DecayDatabaseManager](#decaydatabasemanager)
  - [HalfLifeColorMap](#halflifecolormap)
  - [load_decay_database](#load_decay_database)
- [Usage Examples](#usage-examples)
- [Notes](#notes)

---

## Overview

`decay_database.py` provides a comprehensive toolkit for loading, querying, processing, and visualizing nuclear decay data. Its core features include:
- Querying half-lives, decay modes, progeny, branching ratios, and decay energies for nuclides
- Sorting nuclides by decay chains and serializing data for efficient access
- Visualizing the nuclear chart (N-Z plot) with customizable color mapping

---

## Main Classes & Functions

### DecayDatabase

> **class nudca.decay_database.DecayDatabase**

The main class representing a nuclear decay database, encapsulating all nuclide decay data and query methods.

**Constructor**

```python
DecayDatabase(
    data_source: str,
    nuclides: np.ndarray,
    half_life_data: np.ndarray,
    decay_constants_data: np.ndarray,
    decay_modes_data: np.ndarray,
    progeny_data: np.ndarray,
    branching_ratios_data: np.ndarray,
    decay_energies_data: np.ndarray
)
```
- `data_source`: Name of the data source (e.g., 'ENDF-B-VIII.1_decay')
- Other arguments are numpy arrays for various nuclide properties

**Key Methods**

| Method | Description |
|--------|-------------|
| `validate_nuclide_symbol(nuclide)` | Validate and standardize a nuclide symbol. Raises if invalid or not found. |
| `get_nuclide_half_life(nuclide, units='readable')` | Get half-life in readable string, seconds ('s'), or original units. |
| `get_nuclide_progeny(nuclide)` | Get list of daughter nuclides. |
| `get_nuclide_branching_ratios(nuclide)` | Get branching ratios for all decay modes. |
| `get_nuclide_decay_modes(nuclide)` | Get all decay modes for a nuclide. |
| `get_nuclide_decay_constants(nuclide)` | Get decay constant (lambda) in 1/s. |
| `get_proton_numbers()` | Get array of proton numbers (Z) for all nuclides. |
| `get_neutron_numbers()` | Get array of neutron numbers (N) for all nuclides. |
| `get_nuclide_decay_energy(nuclide, energy_type)` | Get decay energy of a specific type (see below). |
| `get_nuclide_total_decay_energy(nuclide)` | Get total decay energy (sum of EM, LP, HP, Neutrino). |
| `plot_nuclear_chart(...)` | Plot the nuclear chart (N vs Z), with many customization options. |

**Decay Energy Types**
- `'EM'`: Electromagnetic energy
- `'LP'`: Light particle energy
- `'HP'`: Heavy particle energy
- `'Neutrino'`: Neutrino energy
- `'Gamma'`, `'Beta_Minus'`, `'Beta_Plus'`, `'Alpha'`, `'Neutron'`, `'Proton'`, `'Effective_Q'`: See code for full mapping

**Equality Operators**
- `__eq__(other)`: Compare two DecayDatabase objects for equality
- `__ne__(other)`: Inequality comparison

{{% notice style="green" title="get_nuclide_half_life" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_half_life(self, nuclide: str, units: str = 'readable') -> Union[float, str]
```
Returns the half-life of a nuclide in the specified units ('readable', 's', or original units).
{{% /notice %}}


{{% notice style="green" title="get_nuclide_decay_modes" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_decay_modes(self, nuclide: str) -> List[str]
```
Returns the list of decay modes for the given nuclide.
{{% /notice %}}


{{% notice style="green" title="get_nuclide_branching_ratios" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_branching_ratios(self, nuclide: str) -> List[float]
```
Returns the branching ratios for all decay modes of the nuclide.
{{% /notice %}}


{{% notice style="green" title="get_nuclide_progeny" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_progeny(self, nuclide: str) -> List[str]
```
Returns the list of progeny (daughter nuclides) for the given nuclide.
{{% /notice %}}


{{% notice style="green" title="get_nuclide_decay_energy" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_decay_energy(self, nuclide: str, energy_type: str) -> float
```
Returns the specified type of decay energy for the nuclide. Supported `energy_type` values:
- 'EM': Electromagnetic
- 'LP': Light particle
- 'HP': Heavy particle
- 'Neutrino': Neutrino
- 'Gamma', 'Beta_Minus', 'Beta_Plus', 'Alpha', 'Neutron', 'Proton', 'Effective_Q'
{{% /notice %}}


{{% notice style="green" title="get_nuclide_total_decay_energy" groupid="notice-toggle" expanded="true" %}}
```python
def get_nuclide_total_decay_energy(self, nuclide: str) -> float
```
Returns the total decay energy released (sum of EM, LP, HP, and Neutrino energies).
{{% /notice %}}


{{% notice style="green" title="plot_nuclear_chart" groupid="notice-toggle" expanded="true" %}}
```python
def plot_nuclear_chart(self, figure=None, nuclei_linewidths=0.3, colorbar=False,
                       figsize=(9,6), dpi=300, magic_numbers=[2,8,20,28,50,82,126],
                       **kwargs
                    ) -> plt.figure
```
Plots the nuclear chart (N vs Z) colored by half-life, with magic numbers highlighted. Returns a matplotlib figure.
{{% /notice %}}




---

### DecayDatabaseManager

> **class nudca.decay_database.DecayDatabaseManager**

A manager class for loading, saving, and processing nuclear decay data files. Handles sorting, conversion, and serialization for use in `DecayDatabase`.

**Constructor**
```python
DecayDatabaseManager(data_source: str = 'ENDF-B-VIII.1_decay')
```
- `data_source`: Name of the decay data source

**Key Methods**
- `serialize_decay_database()`: Load, sort, and save the decay database in both CSV and compressed NumPy formats for fast loading.
- `transform_radionuclide_data(df)`: Convert a DataFrame of nuclide data into arrays for DecayDatabase.
- `sort_nuclide_data(df, decay_mode='β-')`: Sort nuclides for consistent ordering, prioritizing stability and decay chains.
- `sort_decay_chains(df, decay_mode='β-')`: Sort nuclides so that decay chains (by the specified mode) are in order.
- `parse_string_to_list(df, column_name)`: Convert string representations of lists in a DataFrame column to actual Python lists.

**Constants**
- Various string labels for DataFrame columns (e.g., `RADIONUCLIDE_LABEL`, `HALF_LIFE_SECOND_LABEL`, etc.)

---

### HalfLifeColorMap

> **class nudca.decay_database.HalfLifeColorMap**

A configuration and utility class for half-life color mapping in nuclear chart visualizations.

**Constructor**
```python
HalfLifeColorMap(half_life_data: Optional[np.ndarray] = None)
```
- `half_life_data`: Array of half-life data for all nuclides

**Key Methods & Properties**
- `min_half_life`: Minimum finite half-life in the dataset
- `max_half_life`: Maximum finite half-life in the dataset
- `get_range_for_half_life(half_life)`: Get the appropriate range key for a given half-life value
- `get_cmap_and_norm(range_key)`: Get colormap and normalization for a given range key
- Internal plotting helpers (prefixed with `_`): figure creation, plotting stable/unstable nuclides, axis/legend setup, etc.

---

### load_decay_database

> **Function**

```python
def load_decay_database(data_source: str = 'ENDF-B-VIII.1_decay') -> DecayDatabase
```
Loads a DecayDatabase object from a compressed NumPy file for the specified data source.
- `data_source`: Name of the decay data source
- **Returns**: `DecayDatabase` instance

---

## Usage Examples

```python
from nudca.decay_database import load_decay_database

db = load_decay_database()
print(db.get_nuclide_half_life('U-238'))  # Readable half-life
print(db.get_nuclide_decay_modes('U-238'))  # Decay modes
print(db.get_nuclide_progeny('U-238'))  # Daughter nuclides
print(db.get_nuclide_total_decay_energy('U-238'))  # Total decay energy

# Plot the nuclear chart
import matplotlib.pyplot as plt
fig = db.plot_nuclear_chart(figsize=(10, 7))
plt.show()
```

---

## Notes
- Requires `numpy`, `pandas`, `matplotlib`, and related scientific libraries
- Data files must be placed in the `nudca/data/` directory in the expected format
- Some methods require strict nuclide symbol formats; use `validate_nuclide_symbol` for safety
- `plot_nuclear_chart` supports many customization options (see source code for details)
- For custom data sources or advanced data processing, refer to `DecayDatabaseManager`

---


## See Also

- [Nuclide API](./Nuclide/)
- [DecayDiagram API](./DecayDiagram/)
- [DecayMatrix API](./DecayMatrix/)
