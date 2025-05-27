+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'DecayDatabase'
weight = 4
+++


{{% notice style="info" icon="fa fa-database" %}}
This page documents the `decay_database.py` module, which provides access to nuclear decay data and utilities for nuclide analysis. It is part of the NuDCA (Nuclear Decay Chain Astrophysics) package.
{{% /notice %}}

## Overview

The `DecayDatabase` class represents a database of nuclear decay data for a set of nuclides. It provides access to half-lives, decay modes, progeny, branching ratios, decay energies, and plotting utilities. The module also includes the `load_decay_database` function for loading data from disk.

---

## Class: `DecayDatabase`

### Constructor
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
- **data_source** (`str`): Name of the data source (e.g., 'ENDF-B-VIII.1_decay').
- **nuclides** (`np.ndarray`): Array of nuclide symbols.
- **half_life_data** (`np.ndarray`): Array of half-life data tuples.
- **decay_constants_data** (`np.ndarray`): Array of decay constants.
- **decay_modes_data** (`np.ndarray`): Array of decay modes for each nuclide.
- **progeny_data** (`np.ndarray`): Array of progeny lists for each nuclide.
- **branching_ratios_data** (`np.ndarray`): Array of branching ratios for each nuclide.
- **decay_energies_data** (`np.ndarray`): Array of decay energies for each nuclide.

---

## Methods

| Method | Description |
|--------|-------------|
| `validate_nuclide_symbol(nuclide)` | Validate and standardize a nuclide symbol. Raises `NuclideStrError` if invalid or not found. |
| `get_nuclide_half_life(nuclide, units='readable')` | Get the half-life of a nuclide in the specified units. |
| `get_nuclide_progeny(nuclide)` | Get the list of progeny (daughter nuclides) for a nuclide. |
| `get_nuclide_branching_ratios(nuclide)` | Get the branching ratios for all decay modes of a nuclide. |
| `get_nuclide_decay_modes(nuclide)` | Get the decay modes for a nuclide. |
| `get_nuclide_decay_constants(nuclide)` | Get the decay constant (lambda) for a nuclide. |
| `get_proton_numbers()` | Get the array of proton numbers (Z) for all nuclides. |
| `get_neutron_numbers()` | Get the array of neutron numbers (N) for all nuclides. |
| `get_nuclide_decay_energy(nuclide, energy_type)` | Get a specific type of decay energy for a nuclide. |
| `get_nuclide_electromagnetic_energy(nuclide)` | Get the electromagnetic decay energy for a nuclide. |
| `get_nuclide_light_particle_energy(nuclide)` | Get the light particle decay energy for a nuclide. |
| `get_nuclide_heavy_particle_energy(nuclide)` | Get the heavy particle decay energy for a nuclide. |
| `get_nuclide_neutrino_energy(nuclide)` | Get the neutrino decay energy for a nuclide. |
| `get_nuclide_total_decay_energy(nuclide)` | Get the total decay energy released (sum of EM, LP, HP, and Neutrino energies). |
| `plot_nuclear_chart(...)` | Plot the nuclear chart (N vs Z) colored by half-life, with magic numbers highlighted. |
| `__eq__(other)` / `__ne__(other)` | Compare two `DecayDatabase` objects for equality or inequality. |

---

## Function: `load_decay_database`

```python
def load_decay_database(data_source: str = 'ENDF-B-VIII.1_decay') -> DecayDatabase
```
- **data_source** (`str`): Name of the decay data source.
- **Returns:** `DecayDatabase` — Loaded decay database object.

---

## Example Usage

```python
from nudca.decay_database import load_decay_database

db = load_decay_database("ENDF-B-VIII.1_decay")

# Validate a nuclide symbol
symbol = db.validate_nuclide_symbol("U-235")

# Get half-life
half_life = db.get_nuclide_half_life("U-235")

# Get decay modes
modes = db.get_nuclide_decay_modes("U-235")

# Plot nuclear chart
fig = db.plot_nuclear_chart()
fig.show()
```

---

## Notes
- The database is typically loaded from a compressed NumPy file using `load_decay_database`.
- Methods provide both raw data access and scientific utilities for nuclear analysis.
- Plotting requires `matplotlib`.

---

## See Also
- [DecayDiagram API](./DecayDiagram/)
- [DecayMatrix API](./DecayMatrix/)
