+++
date = '2025-05-22T21:59:15+08:00'
draft = false
title = 'Opacity'
weight = 1
+++

we adopt grey opacity ranging from 1.0 cm2 g−1 to 10.0 cm2 g−1, which we take to be a function of the initial Ye. Our choice is motivated by the study of Tanaka et al. (2018), which showed that bolometric light curves computed assuming grey opacity in this range are in good agreement with those obtained with wavelength-dependent radiation transfer results. We use the following formula to set the opacity:
$$
\kappa = 1.0 + \frac{9}{1 + \left(4 Y_{\mathrm{e}} \right)^{12}} \text{  [cm}^{-2}\text{/g]}
$$


For $\kappa$, we use the results from [Tanaka et al. (2020)](/References/References/#Tanaka2020) for Ye ∼ 0.15 − 0.4 (κ for Ye = 0.1 is likely underestimated due to a lack of atomic data for the actinides). For the typical BHNS dynamical ejecta and the thermal CCSNe cases, we estimate κ in this Ye range by fitting an exponential function to the available opacity data to get
$$
\kappa = 211.98 \exp(-12.33Y_{\mathrm{e}})
$$