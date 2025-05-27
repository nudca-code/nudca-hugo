+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'Nuclide'
weight = 5
+++
---

load_dataset(dataset_name=None, dir_path=None, load_sympy=False)

---
Load a decay dataset, either from a set of data files packaged within `radioactivedecay`, or by specifying a local directory containing the data files.

**Parameters:**
- **dataset_name** (`str`, optional)  
  Name of the decay dataset (or sub-package directory name). Use `"DEFAULTDATADecayData"` to load the default dataset.
- **dir_path** (`str` or `None`, optional)  
  Path to the directory containing the decay dataset files. Use `None` to load data that are bundled as a sub-package of `radioactivedecay`. Default is `None`.
- **load_sympy** (`bool`, optional)  
  Load SymPy version of the decay data for arbitrary-precision decay calculations. Default is `False`.

**Returns:**  
A decay dataset used by `radioactivedecay`.

**Return type:**  
`DecayData`


### Example

```python
from radioactivedecay import decaydata

# Load the default decay dataset
data = decaydata.load_dataset("DEFAULTDATADecayData")
```
