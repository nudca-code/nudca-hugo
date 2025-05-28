+++
title = 'NucleoDecay'
weight = 5
+++

```python
import numpy as np
from nudca import load_decay_database, load_decay_matrix, RadioactiveDecay

decay_database = load_decay_database(data_source='ENDF-B-VIII.1_decay')
decay_matrix = load_decay_matrix(data_source='ENDF-B-VIII.1_decay')

init_Y = {'Kr88': 1.e-5}
radioactive_decay = RadioactiveDecay( init_Y, decay_database, decay_matrix )

times = np.geomspace(1.e-2, 1.e3, 10000) * 86400
nuclides, Y = radioactive_decay.decay_abundance(times)
```