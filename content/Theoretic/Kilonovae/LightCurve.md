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


$$
L(r) \equiv 4\pi r^{2} F(r) \sim -\frac{4\pi r^{2}}{\kappa(r)\rho(r)}\frac{\partial u}{\partial r}
$$

$F(r) \equiv -\kappa_{\gamma} \frac{\partial T}{\partial r}$


- we can approximate the value of a spatial derivative as some quantity over the characteristic length scale
$$
\frac{\partial u}{\partial r} \simeq -\frac{u}{r}
$$


$$
M_{\mathrm{ej}} = \int_{R_{\min}}^{R_{\max}} 4\pi r^{2} \rho(r, t) \mathrm{d}{r}
$$


$$
\frac{\mathrm{d}E_{i}}{\mathrm{d}t} = m_{i}\dot{Q}_{\mathrm{eff}}(t) -\frac{E_{i}}{t} - L_{i}(t)
$$


$$
L_{i} = \frac{E_{i}}{t_{\mathrm{lc},i} + t_{\mathrm{diff}, i}}
$$

$$
\tau_{i} = \int_{R_{i}}^{\infty} \kappa(r)\rho(r, t) \mathrm{d}r
$$


$$
L_{bol} = \sum L_{i}
$$



## Density Profile

$$
\rho(r, t) = \rho_{0}(t) \left( \frac{r}{R_{\min}} \right)^{-n}
$$