+++
linktitle = 'NuDCA'
title = 'NuDCA'
type = 'home'
+++

## NuDCA Core Package Documentation

![NuDCA](images/logo.png?inlinecontent&purple&width=30vh)


`NuDCA` is an open-source Python program specifically designed for calculating the decay chains of radioactive nuclides. We have developed a versatile computational framework that efficiently handles decay chains with complex branching ratios. This framework employs a matrix-based numerical solving method, ensuring both analytical accuracy and computational efficiency, enabling rapid resolution of decay chain differential equations.

The primary goal of `NuDCA` is to provide researchers with a flexible and reliable tool for simulating the accumulation, decay, and associated physical phenomena of radioactive nuclides. The program supports a wide range of complex scenarios, including the splitting and merging of multi-branch decay chains and the superposition of various decay modes. This flexibility makes it invaluable across fields such as nuclear science, geochronology, and astrophysics. As an open-source Python-based software, `NuDCA` offers excellent extensibility, allowing researchers to easily customize its functionality to meet specific requirements.

In extreme astrophysical environments like core-collapse supernovae (CCSN) and neutron star mergers (NSM), significant energy is released through radioactive decay, powering transient phenomena such as supernovae (SN) and kilonovae (KN). To address the needs of this research area, `NuDCA` features a specialized module for calculating the light curves of kilonovae. This capability provides critical support for studying the synthesis of r-process elements, the physical properties of ejecta, and the radiation characteristics of kilonovae.

Furthermore, the development of `NuDCA` emphasizes user experience and community collaboration. With its intuitive interface and comprehensive documentation, even beginners can quickly start using the program. As an open-source project, `NuDCA` fosters collaboration between academia and industry, aiming to drive technological advancements and scientific research, establishing itself as a benchmark tool in the field of radioactive decay simulation.


By default `NuDCA` uses decay data from [ENDF-B-VIII.1](https://www-nds.iaea.org/public/download-endf/ENDF-B-VIII.1/).

In order to use `NuDCA`, you will need Python 3.9+ with the [NumPy](https://numpy.org/), [SciPy](https://scipy.org/), [Astropy](https://www.astropy.org/), [Pandas](https://pandas.pydata.org/), [Matplotlib](https://matplotlib.org/), [NetworkX](https://networkx.org/) and [Numba](https://numba.pydata.org/) packages installed. The code is platform independent and has been tested on Windows, MacOS and Linux systems.

## Contents

{{% children depth="999" description="False" %}}