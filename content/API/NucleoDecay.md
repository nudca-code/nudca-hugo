+++
title = 'NucleoDecay'
weight = 6
+++


{{% notice style="info" icon="fa fa-radiation" %}}
This page documents the `nucleo_decay.py` module, which provides tools for modeling radioactive decay, heating rates, and nuclide abundance evolution in nuclear astrophysics. It is part of the NuDCA (Nuclear Decay Chain Astrophysics) package.
{{% /notice %}}

## Overview

The `nucleo_decay.py` module offers a comprehensive class and utilities for simulating radioactive decay processes, calculating decay heating rates, and managing nuclide abundances in large nuclear decay networks. It supports matrix-based solutions to the Bateman equations and provides import/export and visualization capabilities for scientific workflows.

---

## Main Class: `RadioactiveDecay`

Represents a radioactive decay network, enabling time evolution, heating rate calculations, and abundance management.

### Constructor
```python
RadioactiveDecay(
    initial_abundance: Dict[str, float],
    decay_database: DecayDatabase,
    decay_matrix: DecayMatrix
)
```
- **initial_abundance** (`Dict[str, float]`): Initial nuclide abundances (by symbol).
- **decay_database** (`DecayDatabase`): Decay data for all nuclides in the network.
- **decay_matrix** (`DecayMatrix`): Matrix representation of the decay network.

---

### Properties

| Property            | Type                      | Description                                      |
|---------------------|---------------------------|--------------------------------------------------|
| `initial_abundance` | Dict[str, float]          | Initial nuclide abundances.                      |
| `decay_database`    | DecayDatabase             | Decay data for the network.                      |
| `decay_matrix`      | DecayMatrix               | Matrix representation of the decay network.      |
| `nuclides`          | List[str]                 | List of nuclide symbols in the network.          |

---

### Key Methods

| Method | Description |
|--------|-------------|
| `calculate_nuclide_abundances(decay_times)` | Compute time evolution of nuclide abundances. |
| `decay_heating_rates(decay_times, energy_type=None)` | Calculate heating rates at given times (optionally by energy type). |
| `decay_process(decay_times)` | Core matrix-based Bateman solution for abundance evolution. |
| `plot_heating_rates(decay_times, legend=True, save_path=None, xlim=None, ylim=None, energy_type=None)` | Plot log-log heating rates vs. time. |
| `import_nuclide_abundance(filepath, fmt='csv')` | Import nuclide abundances from file (CSV, JSON, Excel). |
| `export_nuclide_abundance(filepath, fmt='csv')` | Export current nuclide abundances to file. |
| `export_decay_abundance(decay_times, filepath, fmt='csv', index_as_time=True)` | Export time evolution of abundances to file. |

---

## Function: `calculate_radioactive_heating_rates`

```python
def calculate_radioactive_heating_rates(
    decay_constants: np.ndarray,
    abundances: np.ndarray,
    decay_energies: np.ndarray
) -> np.ndarray
```
Numba-accelerated function to compute total heating rates from decay constants, abundances, and decay energies.

---

## Usage Example

```python
from nudca import load_decay_database, load_decay_matrix, RadioactiveDecay

db = load_decay_database('ENDF-B-VIII.1_decay')
dm = load_decay_matrix('ENDF-B-VIII.1_decay')
rd = RadioactiveDecay({'Kr88': 1e-5}, db, dm)

times = np.geomspace(1e-2, 1e3, 10000) * 86400
nuclides, abundances = rd.calculate_nuclide_abundances(times)
heating = rd.decay_heating_rates(times)
rd.plot_heating_rates(times)
```

---

## Notes
- The class supports both analytical and numerical solutions for large decay networks.
- Heating rates can be calculated for total or specific decay energy types (e.g., 'beta', 'alpha', 'gamma').
- Import/export supports CSV, JSON, and Excel formats for interoperability.
- Plotting requires `matplotlib`.
- Performance-critical routines are accelerated with Numba.

---

## See Also
- [DecayDatabase API](./DecayDatabase/)
- [DecayMatrix API](./DecayMatrix/)
- [DecayDiagram API](./DecayDiagram/)