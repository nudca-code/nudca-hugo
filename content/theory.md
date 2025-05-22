+++
date = '2025-05-22T21:59:15+08:00'
draft = false
title = 'Theory'
+++

# Decay chains

```shell
dsasfd
```

$$
\left\{
\begin{aligned}
	\frac{\mathrm{d}N_{1}(t)}{\mathrm{d}t} &= -\lambda_{1}N_{1}(t)                              \\ 
	\frac{\mathrm{d}N_{2}(t)}{\mathrm{d}t} &= b_{12}\lambda_{1}N_{1}(t) - \lambda_{2}N_{2}(t)         \\
	\frac{\mathrm{d}N_{3}(t)}{\mathrm{d}t} &= b_{13}\lambda_{1}N_{1}(t) + b_{23}\lambda_{2}N_{2}(t) - \lambda_{3}N_{3}(t)         \\
	&\vdots                                           \\
	\frac{\mathrm{d}N_{n}(t)}{\mathrm{d}t} &= b_{1n}\lambda_{1}N_{1}(t) + b_{2n}\lambda_{2}N_{2}(t) + \cdots + b_{n-1,n}\lambda_{n-1}N_{n-1}(t) - \lambda_{n}N_{n}(t)
\end{aligned}
\right.
$$