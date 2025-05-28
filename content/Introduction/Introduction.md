+++
title = 'Introduction'
weight = 1
+++

## Introduction
`nudca` is a Python package for radioactive decay calculations.

The original goal was to create a light-weight Python package for radioactive decay calculations, with full support for branching decays, multi-step decay chains, and metastable states. By default radioactivedecay uses decay data from [ENDF-B-VIII.1](https://www-nds.iaea.org/public/download-endf/ENDF-B-VIII.1/). It solves the radioactive decay differential equations analytically using basic linear algebra operations.

In order to use radioactivedecay, you will need Python 3.9+ with the [Matplotlib](https://matplotlib.org/), [NumPy](https://numpy.org/), [Pandas](https://pandas.pydata.org/), [SciPy](https://scipy.org/), [NetworkX](https://networkx.org/), Setuptools and Numba packages installed. The code is platform independent and has been tested on Windows, MacOS and Linux systems.