# Tigramite – Causal inference and causal discovery for time series datasets
Version 5.0

(Python Package)

[Github](https://github.com/jakobrunge/tigramite.git)

[Documentation](https://jakobrunge.github.io/tigramite/)

[Tutorials](https://github.com/jakobrunge/tigramite/tree/master/tutorials/)

[Simple GUI](https://github.com/stbachinger/TigramiteGui)

## Overview

__Update:__ Tigramite now has a new CausalEffects class that allows to estimate (conditional) causal effects and mediation based on a causal graph. Have a look at the tutorial.

Further, Tigramite provides several causal discovery methods that can be used under different sets of assumptions. An application always consists of a method and a chosen conditional independence test, e.g. PCMCI together with ParCorr. The following two tables give an overview of the assumptions involved:

| Method | Assumptions         | Output |
|--------|---------------------------------------------------------------------------|----|
|         |   (in addition to Causal Markov Condition and Faithfulness)   |    |
| PCMCI  | Causal stationarity, no contemporaneous causal links, no hidden variables |  Directed lagged links, undirected contemporaneous links (for tau_min=0)  |
| PCMCIplus | Causal stationarity, no hidden variables    | Directed lagged links, directed and undirected contemp. links (Time series CPDAG) |
| LPCMCI | Causal stationarity    | Time series PAG |


| Conditional independence test | Assumptions                                  |
|--------|---------------------------------------------------------------------------|
| ParCorr  | univariate variables with continuous, linear Gaussian dependencies |
| GPDC / GPDCtorch | univariate variables with continuous, additive dependencies        |
| CMIknn | multivariate variables with continuous, general dependencies           |
| CMIsymb | univariate with discrete/categorical dependencies           |

## General Notes

Tigramite is a causal time series analysis python package. It allows to efficiently estimate causal graphs from high-dimensional time series datasets (causal discovery) and to use graphs for robust forecasting and the estimation and prediction of direct, total, and mediated effects. Causal discovery is based on linear as well as non-parametric conditional independence tests applicable to discrete or continuously-valued time series. Also includes functions for high-quality plots of the results. You can find a simple GUI version on https://github.com/stbachinger/TigramiteGui. Please cite the following papers depending on which method you use:

- PCMCI: J. Runge, P. Nowack, M. Kretschmer, S. Flaxman, D. Sejdinovic, Detecting and quantifying causal associations in large nonlinear time series datasets. Sci. Adv. 5, eaau4996 (2019). https://advances.sciencemag.org/content/5/11/eaau4996
- PCMCI+: J. Runge (2020): Discovering contemporaneous and lagged causal relations in autocorrelated nonlinear time series datasets. Proceedings of the 36th Conference on Uncertainty in Artificial Intelligence, UAI 2020,Toronto, Canada, 2019, AUAI Press, 2020. http://auai.org/uai2020/proceedings/579_main_paper.pdf
- LPCMCI: Gerhardus, A. & Runge, J. High-recall causal discovery for autocorrelated time series with latent confounders Advances in Neural Information Processing Systems, 2020, 33. https://proceedings.neurips.cc/paper/2020/hash/94e70705efae423efda1088614128d0b-Abstract.html
- Generally: J. Runge (2018): Causal Network Reconstruction from Time Series: From Theoretical Assumptions to Practical Estimation. Chaos: An Interdisciplinary Journal of Nonlinear Science 28 (7): 075310. https://aip.scitation.org/doi/10.1063/1.5025050
- Nature Communications Perspective paper: https://www.nature.com/articles/s41467-019-10105-3
- Mediation class: J. Runge et al. (2015): Identifying causal gateways and mediators in complex spatio-temporal systems. Nature Communications, 6, 8502. http://doi.org/10.1038/ncomms9502
- Mediation class: J. Runge (2015): Quantifying information transfer and mediation along causal pathways in complex systems. Phys. Rev. E, 92(6), 62829. http://doi.org/10.1103/PhysRevE.92.062829
- CMIknn: J. Runge (2018): Conditional Independence Testing Based on a Nearest-Neighbor Estimator of Conditional Mutual Information. In Proceedings of the 21st International Conference on Artificial Intelligence and Statistics. http://proceedings.mlr.press/v84/runge18a.html
- J. Runge, Necessary and sufficient graphical conditions for optimal adjustment sets in causal graphical models with hidden variables, Advances in Neural Information Processing Systems, 2021, 34. https://proceedings.neurips.cc/paper/2021/hash/8485ae387a981d783f8764e508151cd9-Abstract.html

## Features

- high detection power even for large-scale time series datasets
- flexible conditional independence test statistics adapted to
  continuously-valued or discrete data, and different assumptions about
  linear or nonlinear dependencies
- automatic hyperparameter optimization for most tests
- parallel computing script based on mpi4py
- handling of missing values and masks
- p-value correction and confidence interval estimation
- causal effect class to  non-parametrically estimate (conditional) causal effects and also linear mediated causal effects
- prediction class based on sklearn models including causal feature selection
- GUI covering basic functionality on https://github.com/stbachinger/TigramiteGui


## Required python packages

- python=3.7/3.8/3.9
- numpy==1.21.5
- scipy==1.8.0
- numba==0.55.1

## Optional packages depending on used functions
- scikit-learn>=0.21  # Gaussian Process (GP) Regression
- matplotlib>=3.4.0   # Plotting
- networkx>=2.4       # Plotting
- torch>=1.11.0       # GPDC pytorch version (in conda install pytorch)
- gpytorch>=1.4       # GPDC gpytorch version
- dcor>=0.5.3         # GPDC distance correlation version

## Installation

python setup.py install

This will install tigramite in your path.

To use just the ParCorr, CMIknn, and CMIsymb independence tests, only numpy/numba and scipy are required. For other independence tests more packages are required:

- GPDC: scikit-learn is required for Gaussian Process regression and dcor for distance correlation

- GPDCtorch: gpytorch is required for Gaussian Process regression

Note: Due to incompatibility issues between numba and numpy/scipy, we currently freeze their versions.

## User Agreement

By downloading TIGRAMITE you agree with the following points: TIGRAMITE is provided without any warranty or conditions of any kind. We assume no responsibility for errors or omissions in the results and interpretations following from application of TIGRAMITE.

You commit to cite above papers in your reports or publications.


## License

Copyright (C) 2014-2022 Jakob Runge

See [license.txt](https://github.com/jakobrunge/tigramite/blob/master/license.txt) for full text.

TIGRAMITE is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version. TIGRAMITE is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
