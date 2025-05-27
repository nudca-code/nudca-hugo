+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'DecayDiagram'
weight = 3
+++

## DecayDiagram

```py { title="python" }
from nudca.decay_database import load_decay_database
from nudca.decay_diagram import DecayDiagram

nuclide = 'Sr88'

decay_database = load_decay_database(data_source='ENDF-B-VIII.1_decay')
decay_diagram = DecayDiagram(nuclide, decay_database)

radionuclide     = decay_diagram.nuclide
half_life        = decay_diagram.half_life
decay_modes      = decay_diagram.decay_modes
progeny          = decay_diagram.progeny
branching_ratios = decay_diagram.branching_ratios
```



```python
fig, axes = decay_diagram.plot_decay_chains()
fig.tight_layout()
```


```python
fig, axes = decay_diagram.plot_reverse_decay_chains()
fig.tight_layout()
```

