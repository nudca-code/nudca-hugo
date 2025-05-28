+++
title = 'Heating Rate'
weight = 3
+++

## Radioactive Heating Rate

$$
\dot{q}_{\mathrm{p}}(t) = \sum_{i} N_{A} \lambda_{i}Y_{i}(t)E_{i}   \text{    p} \in \{\alpha, \beta, \gamma\}
$$


### Analytic description
$$
\dot{q}(t) = \dot{\epsilon}_{0}\left( \frac{1}{2} - \frac{1}{\pi}\arctan\left[\frac{t-t_{0}}{\sigma}\right] \right)^{\alpha}
$$


$$
\dot{q}(t) = \dot{\epsilon}_{0}\left( \frac{1}{2} - \frac{1}{\pi}\arctan\left[\frac{t-t_{0}}{\sigma}\right] \right)^{\alpha} \left( \frac{1}{2} + \frac{1}{\pi}\arctan\left[\frac{t-t_{1}}{\sigma_{1}}\right] \right)^{\alpha_{1}} + C_{1}e^{-t/\tau_{1}} + C_{2}e^{-t/\tau_{2}} + C_{3}e^{-t/\tau_{3}}
$$



## Effective Heating Rate


$$
\dot{Q}(t) = \sum_{\mathrm{p}}f_{\mathrm{p}}(t)\dot{q}_{\mathrm{p}}(t)   \text{    p} \in \{\alpha, \beta, \gamma\}
$$