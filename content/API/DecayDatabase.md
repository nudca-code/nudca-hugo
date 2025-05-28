+++
description = 'Where our lookout pretends to spot land while actually napping'
title = 'DecayDatabase'
weight = 4
+++

{{% notice style="info" icon="fa fa-atom" %}}
The `DecayDatabase` class is the core component for accessing and analyzing nuclear decay data in the NuDCA library. It provides efficient access to nuclide properties, decay modes, branching ratios, decay energies, and visualization tools for nuclear charts. This API is designed for scientific computing, nuclear physics, and astrophysics applications.
{{% /notice %}}

## Overview

`DecayDatabase` encapsulates a comprehensive database of nuclear decay data, supporting:
- Querying half-lives, decay modes, progeny, and branching ratios
- Access to decay energies (electromagnetic, light particle, heavy particle, neutrino, etc.)
- Visualization of the nuclear chart (N vs Z) with half-life color mapping
- Fast loading from pre-processed data files (e.g., ENDF-B-VIII.1)

The database is typically loaded using the `load_decay_database` function.

---

## Class: DecayDatabase

```python
class DecayDatabase:
    def __init__(
        self,
        data_source: str,
        nuclides: np.ndarray,
        half_life_data: np.ndarray,
        decay_constants_data: np.ndarray,
        decay_modes_data: np.ndarray,
        progeny_data: np.ndarray,
        branching_ratios_data: np.ndarray,
        decay_energies_data: np.ndarray
    ) -> None
```

### Key Methods


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

## Function: load_decay_database

```python
def load_decay_database(data_source: str = 'ENDF-B-VIII.1_decay') -> DecayDatabase
```
Loads a `DecayDatabase` object from a compressed data file for the specified data source.

---

## Nuclide String Format

All nuclide arguments accept standard nuclide strings (e.g., 'U-238', 'Fe56'). The `Nuclide` class is used internally for validation and parsing. See the Nuclide API for more details.

---

## Related Classes

- **Nuclide**: Represents a nuclide, providing properties for atomic number (Z), mass number (A), neutron number (N), and metastable state.
- **DecayDatabaseManager**: For advanced users, provides tools for loading, sorting, and serializing nuclear decay data files.

---


## Usage Example

```python
from nudca import load_decay_database

db = load_decay_database('ENDF-B-VIII.1_decay')

# Query half-life (as readable string and in seconds)
print(db.get_nuclide_half_life('U-238'))           # e.g., '4.468 billion years'
print(db.get_nuclide_half_life('U-238', 's'))      # e.g., 1.409e+17

# Get decay modes and branching ratios
print(db.get_nuclide_decay_modes('U-238'))         # e.g., ['α']
print(db.get_nuclide_branching_ratios('U-238'))    # e.g., [1.0]

# Get progeny (daughter nuclides)
print(db.get_nuclide_progeny('U-238'))             # e.g., ['Th-234']

# Get decay energies
print(db.get_nuclide_decay_energy('U-238', 'EM'))  # Electromagnetic energy
print(db.get_nuclide_total_decay_energy('U-238'))  # Total decay energy

# Plot the nuclear chart
fig = db.plot_nuclear_chart()
fig.savefig('nuclear_chart.png')
```


## See Also

- [Nuclide API](./Nuclide/)
- [DecayDiagram API](./DecayDiagram/)
- [DecayMatrix API](./DecayMatrix/)
