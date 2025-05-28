+++
title = 'class:KNOpacity'
weight = 2
+++


```python
import numpy as np
import matplotlib.pyplot as plt
from nudca.kilonovae.opacity import KNOpacity

Ye = np.linspace(0.10, 0.50, 5000)

Ye_table = [0.10, 0.15, 0.20, 0.25, 0.30, 0.35, 0.40]
kappa_table = [19.5, 32.2, 22.3, 5.60, 5.36, 3.30, 0.96]

kappa_tanaka = KNOpacity(opacity_type='Tabular', opacity_method='Tanaka_OneVar')(Ye)
kappa_wu = KNOpacity(opacity_type='Formula', opacity_method='Wu2022')(Ye)
kappa_ekanger = KNOpacity(opacity_type='Formula', opacity_method='Ekanger2023')(Ye)


fig, ax = plt.subplots(figsize=(8,6), dpi=150)
ax.plot(Ye, kappa_tanaka, label='Tanaka2020_OneVar')
ax.plot(Ye, kappa_wu, label='Wu2022')
ax.plot(Ye, kappa_ekanger, label='Ekanger2023')
ax.scatter(Ye_table, kappa_table, label='Tanaka2020_Table')
ax.set_xlim(0.095, 0.5)
ax.set_ylim(1.e-1, 100)
ax.set_yscale('log')

ax.set_xlabel(r'$Y_{e}$')
ax.set_ylabel(r'$\kappa \quad [cm^{2} g^{-1}]$')

ax.legend()
plt.show()
```

![Opacity](../../../images/Tutorial/Opacity.png)