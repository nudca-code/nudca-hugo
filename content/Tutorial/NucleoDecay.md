+++
title = 'NucleoDecay'
weight = 5
+++

```python
import numpy as np
import matplotlib.pyplot as plt
from nudca import load_decay_database, load_decay_matrix, RadioactiveDecay

decay_database = load_decay_database(data_source='ENDF-B-VIII.1_decay')
decay_matrix = load_decay_matrix(data_source='ENDF-B-VIII.1_decay')

init_Y = {'Ni56': 1.e-5, 'Co56':1.e-7, 'Fe56':1.e-9}
radioactive_decay = RadioactiveDecay( init_Y, decay_database, decay_matrix )

times = np.geomspace(1.e-2, 1.e3, 10000) * 86400
nuclides, Y = radioactive_decay.decay_nuclide_abundances(times)

fig, ax = plt.subplots(figsize=(8, 6), dpi=300)
ax.plot(times/86400, Y[:, 0], label=f'{nuclides[0]}')
ax.plot(times/86400, Y[:, 1], label=f'{nuclides[1]}')
ax.plot(times/86400, Y[:, 2], label=f'{nuclides[2]}')

ax.set_xlim(1.e-2, 1.e3)
ax.set_ylim(1e-10, 1e-3)
ax.set_xscale('log')
ax.set_yscale('log')
ax.set_xlabel('Time [days]', fontsize=14)
ax.set_ylabel('Y', fontsize=14)

ax.legend()
plt.show()
```

![Y_Ni56Decay](../../images/Tutorial/Y_Ni56Decay.png)

<br>

```python
import numpy as np
import matplotlib.pyplot as plt
from nudca import load_decay_database, load_decay_matrix, RadioactiveDecay

decay_database = load_decay_database(data_source='ENDF-B-VIII.1_decay')
decay_matrix = load_decay_matrix(data_source='ENDF-B-VIII.1_decay')

init_Y = {'Ni56': 1.e-5, 'Co56':1.e-7, 'Fe56':1.e-9}
radioactive_decay = RadioactiveDecay( init_Y, decay_database, decay_matrix )

times = np.geomspace(1.e-2, 1.e3, 10000) * 86400
q_EM = radioactive_decay.decay_heating_rates(times, energy_type='EM')
q_LP = radioactive_decay.decay_heating_rates(times, energy_type='LP')
q_HP = radioactive_decay.decay_heating_rates(times, energy_type='HP')
q = radioactive_decay.decay_heating_rates(times)

fig, ax = plt.subplots(figsize=(8, 6), dpi=300)
ax.plot(times/86400, q_EM, ls='--', lw=1, label='Electromagnetic')
ax.plot(times/86400, q_LP, ls='--', lw=1, label='Light particle')
# ax.plot(times/86400, q_HP, ls='--', lw=1,  label='Heavy particle')
ax.plot(times/86400, q, ls='-', lw=2, color='b', label='Total')

ax.set_xlim(1.e-2, 1.e3)
ax.set_ylim(1e4, 1e9)
ax.set_xscale('log')
ax.set_yscale('log')
ax.set_xlabel('Time [days]', fontsize=14)
ax.set_ylabel('Heating Rate [erg / g / s]', fontsize=14)

ax.legend()
plt.show()
```

![HeatingRate_Ni56Decay](../../images/Tutorial/HeatingRate_Ni56Decay.png)
