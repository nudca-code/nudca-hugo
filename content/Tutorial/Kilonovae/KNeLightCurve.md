+++
title = 'class:KNeLightCurve'
weight = 4
+++

```python
import numpy as np
import matplotlib.pyplot as plt

from nudca.kilonovae import KNeLightCurve

times = np.geomspace(1e-3, 1e2, 5000) * 86400  # days
t, Lbol = KNeLightCurve(
        lightcurve_type = 'Luminosity',       # ['Luminosity', 'Magnitude']
        velocity_scheme= 'Default',           # Uniform distribution
        density_scheme= 'Metzger2017',        # ['Metzger2017', 'Kasen2017', 'Wollaeger2018']
        thermal_scheme= 'Barnes2016_Default', # ['Barnes2016_Default', 'Barnes2016_1D', 'Barnes2016_2D']
        heating_scheme= 'Korobkin2012',       # ['Korobkin2012', 'Rosswog2024', 'Table']
    #   heating_rate_table = (t, q_dot)
        mass_ejecta = 2.e-3,   # units: M_sun
        vel_ejecta = 0.15,     # units: c
        opacity = 10.0,        # ['Wu2022', 'Ekanger2023', 'Tanaka_OneVar', 'Tanaka_FourVar']
    #   luminosity_distance    # units: Mpc
    #   wavelength             # units: cm
    #   **kwargs   (n_shells ...)
)(times=times)


fig, ax = plt.subplots()

ax.plot(t/86400, Lbol)
ax.set_xlim(-0.5, 30)
ax.set_ylim(1e37, 1e42)
ax.set_yscale('log')

ax.set_xlabel('Time [days]')
ax.set_ylabel('Lbol [erg]')

plt.show()
```

![Lbol](../../../images/Tutorial/Lbol.png)


```python
import numpy as np
import matplotlib.pyplot as plt

from nudca.kilonovae import KNeLightCurve

times = np.geomspace(1e-3, 1e2, 5000) * 86400
t, Mv = KNeLightCurve(
    lightcurve_type='Magnitude',
    mass_ejecta=2.e-3,            # units: M_sun
    vel_ejecta=0.15,              # units: c
    opacity=10.0,                 # units: cm^2 / g
    luminosity_distance = 200,    # units: Mpc
    wavelength = 2e-4,            # units: cm
)(times=times)

fig, ax = plt.subplots()
ax.plot(t/86400, Mv)
ax.set_xlim(-0.5, 30)
ax.set_ylim(20, 40)
ax.invert_yaxis()
ax.set_xlabel('Time [days]')
ax.set_ylabel('Magnitude')

plt.show()
```
![Magnitude](../../../images/Tutorial/Mag.png)