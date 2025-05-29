+++
title = 'Light Curves'
weight = 4
+++

## One-zone Arnett Model

we use simple one-zone models of transients within the framework laid out by Arnett (1980) for SN I light curves. For each heating source we assume the following:

- The ejecta are spherically symmetric and undergo homologous expansion, unless otherwise stated.
- Radiation pressure dominates over electron and gas pressure in the equation of state.
- The heating source is located in the center of the ejecta, unless otherwise stated.
- The optical opacity is a constant, unless otherwise stated.
- The initial radius is small, unless otherwise stated.

We can write the first law of thermodynamics as
$$
\frac{\mathrm{d}E}{\mathrm{d}t} = m\dot{Q}_{\mathrm{eff}}(t) -p\frac{\mathrm{d}V}{\mathrm{d}t} - L(t)
$$
where $E = u V = a T^{4}V$ is the internal energy, $u = a T^{4}$ is the internal energy density, $p = \frac{1}{3}aT^{4}$ is the pressure density, $V = \frac{4}{3}\pi r^{3}$ is the volume, $L$ is the radiated bolometric luminosity, $\dot{Q}_{\mathrm{eff}}$ is the energy generation rate of the heating source, $T$ is the temperature, and $\rho$ is the density. In this framework, all available energy from the heating source supplies either the expansion of the ejecta or observable radiation, and we ignore neutrino losses. Following our assumption of homologous expansion, the radius grows as $r(t) = vt$ (assuming a negligible initial radius), where we approximate $v$ as the photospheric velocity, $v = v_{\mathrm{ph}}$. This assumption also means that no significant additional kinetic energy is added to the ejecta during the duration of the transient (i.e., the ejecta does not accelerate).

The radiative diffusion leads to heat losses from the surface that are approximately given by
$$
L(r) \equiv 4\pi r^{2} F(r) \sim -\frac{4\pi r^{2}}{\kappa(r)\rho(r)}\frac{\partial u}{\partial r}
$$

where $F(r) \equiv -\kappa_{\gamma} \frac{\partial T}{\partial r}$, and we can approximate the value of a spatial derivative as some quantity over the characteristic length scale
$$
\frac{\partial u}{\partial r} \simeq -\frac{u}{r}
$$

We model the bolometric light curve and temperature by adding photons diffusing out from spherical mass shells, where each mass shell is characterized by a mass $m_{i}$, expansion velocity $v_{i}$, and gray opacity $\kappa$. The internal energy of each mass shell is calculated by solving the first law of thermodynamics of radiation-dominated gas:

$$
\frac{\mathrm{d}E_{i}}{\mathrm{d}t} = m_{i}\dot{Q}_{\mathrm{eff}}(t) -\frac{E_{i}}{t} - L_{i}(t)
$$


### Optical depth
$$
\tau_{i} = \int_{R_{i}}^{\infty} \kappa(r)\rho(r, t) \mathrm{d}r
$$


### Bolometric Luminosity

The observed luminosity contributed by the ith layer can be estimated by
$$
L_{i} = \frac{E_{i}}{t_{\mathrm{lc},i} + t_{\mathrm{diff}, i}}
$$

The total bolometric luminosity of the merger ejecta can be obtained by summarizing the contributions of all layers:
$$
L_{bol} = \sum L_{i}
$$



### Apparent Magnitude

The effective temperature of kilonova emission can be determined by
$$
T_{\mathrm{eff}} = \left( \frac{L_{\mathrm{bol}}}{4\pi \sigma_{\mathrm{SB}} R_{\mathrm{ph}}^{2}} \right)^{1/4}
$$

where $\sigma_{SB}$ is the Stefan–Boltzmann constant. The radius of the photosphere $R_{ph}$ is defined by the layer at which the optical depth is unity, i.e.
$$
\tau_{\mathrm{ph}} = \int_{R_{\mathrm{ph}}}^{\infty} \kappa(r) \rho(r, t) \mathrm{d}r = 1
$$


Then, the flux density of the kilonova emission at photon frequency $\nu$ can be given by
$$
F_{\nu}(t) = \frac{2\pi h \nu^{3}}{c^{2}} \frac{1}{\exp{(h\nu /kT_{\mathrm{eff}}) - 1}} \frac{R_{\mathrm{ph}}^{2}}{D_{L}^{2}}
$$

Finally, we  determine the monochromatic AB magnitude by
$$
M_{\nu}(t) = -2.5 \log_{10}\left( \frac{F_{\nu}(t)}{3631 \text{ Jy}} \right)
$$


## Density Profile

$$
\rho(r, t) = \rho_{0}(t) \left( \frac{r}{R_{\min}} \right)^{-n}
$$


$$
M_{\mathrm{ej}} = \int_{R_{\min}}^{R_{\max}} 4\pi r^{2} \rho(r, t) \mathrm{d}{r}
$$