+++
date = '2025-05-22T21:59:15+08:00'
draft = false
title = 'Theory'
+++

## Decay chains


$$
\begin{cases}
	\frac{\mathrm{d}N_{1}(t)}{\mathrm{d}t} &= -\lambda_{1}N_{1}(t)                              \\ 
	\frac{\mathrm{d}N_{2}(t)}{\mathrm{d}t} &= b_{12}\lambda_{1}N_{1}(t) - \lambda_{2}N_{2}(t)         \\
	\frac{\mathrm{d}N_{3}(t)}{\mathrm{d}t} &= b_{13}\lambda_{1}N_{1}(t) + b_{23}\lambda_{2}N_{2}(t) - \lambda_{3}N_{3}(t)         \\
	&\vdots                                           \\
	\frac{\mathrm{d}N_{n}(t)}{\mathrm{d}t} &= b_{1n}\lambda_{1}N_{1}(t) + b_{2n}\lambda_{2}N_{2}(t) + \cdots + b_{n-1,n}\lambda_{n-1}N_{n-1}(t) - \lambda_{n}N_{n}(t)
\end{cases}
$$

and
$$
	\frac{\mathrm{d}}{\mathrm{d}t}
	\begin{bmatrix}
		N_{1}(t) \\
		N_{2}(t) \\
		N_{3}(t) \\
		\vdots   \\
		N_{i}(t) \\
		\vdots   \\
		N_{n}(t)
	\end{bmatrix} =
	\begin{bmatrix}
		-\lambda_{1}      &                &                   &              &                        &                    &                     \\
		b_{12}\lambda_{1} & -\lambda_{2}      &                   &              &                        &                    &                     \\
		b_{13}\lambda_{1} & b_{23}\lambda_{2} & -\lambda_{3}      &              &                        &                    &                     \\
		\vdots            & \vdots            & \vdots            & \ddots       &                  &                    &        &              \\
		b_{1i}\lambda_{1} & b_{2i}\lambda_{2} & b_{3i}\lambda_{3} & \cdots   & -\lambda_{i}       &        &               \\
		\vdots            & \vdots            & \vdots            & \vdots       & \vdots            & \ddots             &                \\
		b_{1n}\lambda_{1} & b_{2n}\lambda_{2} & b_{3n}\lambda_{3} & \cdots       &  b_{in}\lambda_{i} & \cdots & -\lambda_{n}
	\end{bmatrix} \times
	\begin{bmatrix}
		N_{1}(t) \\
		N_{2}(t) \\
		N_{3}(t) \\
		\vdots   \\
		N_{i}(t) \\
		\vdots   \\
		N_{n}(t)
	\end{bmatrix}
$$

matrix A reads:
$$
\boldsymbol{A} = 
\begin{bmatrix}
	-\lambda_{1}      &                   &                   &              &                        &                    &                     \\
	b_{12}\lambda_{1} & -\lambda_{2}      &                   &              &                        &                    &                     \\
	b_{13}\lambda_{1} & b_{23}\lambda_{2} & -\lambda_{3}      &              &                        &                    &                     \\
	\vdots            & \vdots            & \vdots            & \ddots       &                  &                    &        &              \\
	b_{1i}\lambda_{1} & b_{2i}\lambda_{2} & b_{3i}\lambda_{3} & \cdots   & -\lambda_{i}       &        &               \\
	\vdots            & \vdots            & \vdots            & \vdots       & \vdots            & \ddots             &                \\
	b_{1n}\lambda_{1} & b_{2n}\lambda_{2} & b_{3n}\lambda_{3} & \cdots       &  b_{in}\lambda_{i} & \cdots & -\lambda_{n}
\end{bmatrix}
$$

and
$$
A_{ij} =
\begin{cases} 
  0 & \text{if } i < j, \\
  -\lambda_{i} & \text{if } i = j, \\
  b_{ji}\lambda_{j} & \text{if } i > j.
\end{cases}
$$



$$
\frac{\mathrm{d}\boldsymbol{N}}{\mathrm{d}t} = \boldsymbol{A} \boldsymbol{N}
$$




$$
\boldsymbol{A} - \alpha \boldsymbol{I} = 
\begin{bmatrix}
	-\lambda_{1} - \alpha      &                   &                   &              &                        &                    &                     \\
	b_{12}\lambda_{1} & -\lambda_{2} - \alpha     &                   &              &                        &                    &                     \\
	b_{13}\lambda_{1} & b_{23}\lambda_{2} & -\lambda_{3} - \alpha     &              &                        &                    &                     \\
	\vdots            & \vdots            & \vdots            & \ddots       &                  &                    &        &              \\
	b_{1i}\lambda_{1} & b_{2i}\lambda_{2} & b_{3i}\lambda_{3} & \cdots   & -\lambda_{i} - \alpha       &        &               \\
	\vdots            & \vdots            & \vdots            & \vdots       & \vdots            & \ddots             &                \\
	b_{1n}\lambda_{1} & b_{2n}\lambda_{2} & b_{3n}\lambda_{3} & \cdots       &  b_{in}\lambda_{i} & \cdots & -\lambda_{n} - \alpha
\end{bmatrix}
$$


$$
\alpha_{j} = -\lambda_{j} = A_{jj} \quad(j = 1,2,3,\dots,n)
$$


$$
\boldsymbol{p}_{j} = 
\begin{bmatrix}
	P_{1j}    \\
	P_{2j}    \\
	P_{3j}    \\
	\vdots   \\
	P_{ij}    \\
	\vdots   \\
	P_{nj}
\end{bmatrix}
$$


$$
\begin{cases}
	(A_{11} - A_{jj})P_{1j} &= 0                           \\ 
	A_{21}A_{1j} + (A_{22} - A_{jj})P_{2j} &= 0        \\
	A_{31}A_{1j} + A_{32}P_{2j} - (A_{33} - A_{jj})P_{3j} &= 0         \\
	\vdots                                           \\
	A_{n1}P_{1j} + A_{n2}P_{2j} + A_{n3}P_{3j} + \cdots - (A_{nn} - A_{jj})P_{nj} &= 0
\end{cases}
$$


$$
\begin{bmatrix}
	A_{11} - A_{jj} &                 &                 &              &                 &                    &                                                   \\
	A_{21}          & A_{22} - A_{jj} &                 &              &                        &                    &                     \\
	A_{31}          & A_{32}          & A_{33} - A_{jj} &              &                        &               &                     \\
	\vdots            & \vdots            & \vdots            & \ddots       &                  &                    &        &              \\
	A_{i1}          & A_{i2}          & A_{i3}          & \cdots   & A_{ii} - A_{jj}       &        &               \\
	\vdots            & \vdots            & \vdots            & \vdots       & \vdots            & \ddots             &                \\
	A_{n1} & A_{n2} & A_{n3} & \cdots       &  A_{ni} & \cdots & A_{nn} - A_{jj}
\end{bmatrix} \times
\begin{bmatrix}
	P_{1j}    \\
	P_{2j}    \\
	P_{3j}    \\
	\vdots   \\
	P_{ij}    \\
	\vdots   \\
	P_{nj}
\end{bmatrix} = 
\begin{bmatrix}
	0   \\
	0   \\
	0   \\
	\vdots \\
	0    \\
	\vdots  \\
	0
\end{bmatrix}
$$




$$
P_{ij} =
\begin{cases} 
  0 & \text{if } i < j, \\
  1 & \text{if } i = j, \\
  \frac{1}{A_{jj} - A_{ii}} \sum_{k=j}^{i-1} A_{ik}P_{kj} & \text{if } i > j.
\end{cases}
$$



$$
P^{-1}_{ij} =
\begin{cases} 
  0 & \text{if } i < j, \\
  1 & \text{if } i = j, \\
  -\sum_{k=j}^{i-1} P_{ik}P^{-1}_{kj} & \text{if } i > j.
\end{cases}
$$