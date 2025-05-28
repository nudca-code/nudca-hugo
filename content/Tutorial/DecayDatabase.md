+++
title = 'class:DecayDatabase'
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

![Nuclide](../../images/Tutorial/nuclide_chart.png)


{{% notice style="primary" title="There may be pirates" icon="skull-crossbones" %}}
It is all about the boxes.
{{% /notice %}}