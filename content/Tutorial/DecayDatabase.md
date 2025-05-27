+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'DecayDatabase'
weight = 2
+++

## DecayDatabase

```py { title="python" }
import matplotlib.pyplot as plt
from nudca import load_decay_database

decay_database = load_decay_database(data_source='ENDF-B-VIII.1_decay')
fig = decay_database.plot_nuclear_chart()
plt.tight_layout()
plt.show()
```

![Nuclide](../../images/nuclide_chart.png)


{{% notice style="primary" title="There may be pirates" icon="skull-crossbones" %}}
It is all about the boxes.
{{% /notice %}}