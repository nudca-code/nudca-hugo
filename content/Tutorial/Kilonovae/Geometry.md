+++
title = 'class:Geometry'
weight = 1
+++


```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.colors import LogNorm
from matplotlib import cm

from nudca.kilonovae import Geometry, DensityProfile, VelocityProfile

geometry = Geometry(
    velocity_scheme="Default",
    # density_scheme="Metzger2017",
    density_scheme="Kasen2017",
    mass_ejecta=2.e-2,
    vel_ejecta=0.15
)

vel_profile = VelocityProfile(velocity_scheme='Other', vel_min=-0.3, vel_max=0.3)

vel_x, vel_y = np.meshgrid(
    vel_profile.velocity_distribution(500),
    vel_profile.velocity_distribution(500)
)

# vel_x, vel_y = np.meshgrid(
#     np.linspace(0, 0.3, 500),
#     np.linspace(0, 0.3, 500)
# )

times = 86400.0
vel_shells = np.sqrt(vel_x**2 + vel_y**2)
vel_min, vel_max = 0.1, 0.3
rho_shells = geometry.density_shells(times, vel_shells)
rho_shells[(vel_shells < vel_min) | (vel_shells > vel_max)] = np.nan

norm = LogNorm(vmin=np.nanmin(rho_shells), vmax=np.nanmax(rho_shells))

fig, ax = plt.subplots(figsize=(8, 8))
cax = ax.imshow(
    rho_shells, 
    origin='lower', 
    aspect='equal',
    cmap=cm.plasma, 
    extent=[vel_x.min(), vel_x.max(), vel_y.min(), vel_y.max()], 
    norm=norm
)

# ax.set_xlim(-0.3, 0.3)
# ax.set_ylim(-0.3, 0.3)
ax.set_xlim(0, 0.3)
ax.set_ylim(0, 0.3)
ax.set_xlabel(r'$v_{x}/c$', fontsize=12)
ax.set_ylabel(r'$v_{z}/c$', fontsize=12)

cbar = fig.colorbar(cax, ax=ax, orientation='vertical', fraction=0.05, pad=0.05)
cbar.set_label(r'$\rho$ [g/ccm]', fontsize=12)
ax.set_title('Density Distribution', fontsize=14)
plt.show()
```

![Geometry](../../../images/Tutorial/Geometry.png)

