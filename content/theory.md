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
\begin{cases}
	\dv{N_{1}(t)}{t} &= -\lambda_{1}N_{1}(t)                              \\ 
	\dv{N_{2}(t)}{t} &= b_{12}\lambda_{1}N_{1}(t) - \lambda_{2}N_{2}(t)         \\
	\dv{N_{3}(t)}{t} &= b_{13}\lambda_{1}N_{1}(t) + b_{23}\lambda_{2}N_{2}(t) - \lambda_{3}N_{3}(t)         \\
	&\vdots                                           \\
	\dv{N_{n}(t)}{t} &= b_{1n}\lambda_{1}N_{1}(t) + b_{2n}\lambda_{2}N_{2}(t) + \cdots + b_{n-1,n}\lambda_{n-1}N_{n-1}(t) - \lambda_{n}N_{n}(t)
\end{cases}
$$