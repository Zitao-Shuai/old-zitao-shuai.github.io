## Domain generalization - methods - 22

## Overview

`Title`:  SWAD: Domain Generalization by Seeking Flat Minima

`Links`: [SWAD)](https://proceedings.neurips.cc/paper/2021/file/bcb41ccdc4363c6848a1d760f26c28a0-Paper.pdf)

`contribution`: Find flat minima results in a smaller domain generalization gap.

`source`:  `NIPS2021`

`institution`: 

## Background

### introduction

Setting: traditional domain generalization

Contribution:

1. introduce flatness into DG problem
2. propose a robust risk minimization problem

### motivation

- Flatness is proven to have the capability of increasing the generalizing ability of the model. 
- Traditional optimization methods couldn't achieve flat minima.
- The DG performance is bounded by: flat minima, domain discrepancy, and confidence bound. (insight) (more components are studied, higher performance)

### Drawback

1. SWAD does not strongly utilize domain-specific information
2. SWAD is not a perfect flatness-aware optimization method

### related work

1. domain generalization
2. Stochastic Weight Averaging

## Methods

Baseline model: `SWA`

`SWA` gathers model parameters for every K epochs during the update and averages them for the model ensemble.

Modification:

1. densely sample weights for every iteration.
2. consider the trace of the validation loss

Steps:

1. Divide the training data into the training part and the validation part.
2. Find a start point $N_s$ where validation loss no longer decreases.
3. Find a end point $N_e$ where validation loss exceeds the tolerance $r$.
4. Average the checkpoints.





