+++
date = '2025-05-26T15:49:27+08:00'
draft = false
title = 'DecayMatrix'
weight = 4
+++

```python
from nudca.decay_database import load_decay_database
from nudca.decay_matrix import MatrixBuilder

decay_database = load_decay_database()
matrix_builder = MatrixBuilder(decay_database)

matrix_A = matrix_builder.build_matrix_A()
matrix_P = matrix_builder.build_matrix_P(matrix_A)
matrix_P_inv = matrix_builder.build_matrix_P_inv(matrix_A, matrix_P)
```



```python
from nudca.decay_matrix import load_decay_matrix

decay_matrix = load_decay_matrix()

print(decay_matrix)
```