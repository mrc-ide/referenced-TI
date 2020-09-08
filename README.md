# referenced-TI
Code for the referenced thermodynamic integration (TI) method of calculating model evidence, used to generate results in the paper

# Simulating normalised constants with referenced thermodynamic integration: application to COVID-19 model selection

authors: Iwona Hawryluk, Swapnil Mishra, Seth Flaxman, Neil Ferguson, Samir Bhatt and Thomas A. Mellan
MRC Centre for Global Infectious Disease Analysis, Department of Infectious Disease Epidemiology, Imperial College London
Department of Mathematics, Imperial College London

August 2020

## Abstract:

Model selection is a fundamental part of Bayesian statistical inference; a widely used tool in the field of epidemiology. Simple methods such as Akaike Information Criterion are commonly used but they do not incorporate the uncertainty of the model's parameters, which can give misleading choices when comparing models with similar fit to the data. One approach to model selection in a more rigorous way that uses the full posterior distributions of the models is to compute the ratio of the normalising constants (or model evidence), known as Bayes factors. These normalising constants integrate the posterior distribution over all parameters and balance over and under fitting. However, normalising constants often come in the form of intractable, high-dimensional integrals, therefore special probabilistic techniques need to be applied to correctly estimate the Bayes factors.
One such method is thermodynamic integration (TI), which can be used to estimate the ratio of two models' evidence by integrating over a continuous *path* between the two un-normalised densities. 
In this paper we introduce a variation of TI method, here referred to as **referenced TI,** which computes a single model's evidence in an efficient way by using a reference density such as a multivariate normal - where the normalising constant is known. 
We show that referenced TI, an *asymptotically exact* Monte Carlo method of calculating the normalising constant of a single model, in practice converges to the correct result much faster than other competing approaches such as the method of power posteriors.
We illustrate the implementation of the algorithm on informative 1- and 2-dimensional examples, and apply it to a popular linear regression problem, and use it to select parameters for a model of the COVID-19 epidemic in South Korea.

## Repository description:

The code in this repository is organised as follows:

- 1-dimensional example  - *1D_with_plots.py*
- 2-dimensional example with constrained parameters - *2D_with_correction.py*
- linear regression radiata pine example - *linear_regression* folder
  - *radiata_friel_data.csv* - radiata pine data as used in Friel and Wyse (2011)
  - *radiata_pine_example.py* - code to generate outputs of a Laplace approximation, model switch TI, referenced TI and power posterior with 11 and 100 temperature placements
  - *radiata_repeated_runs.py* - outputs of 15 runs of the referenced TI and power posteriors method evaluated over 15 runs of the algorithms
- COVID-19 for South Korea with a Bellman-Harris process - *bellman_harris* folder
  - SouthKoreaData.csv - case data for South Korea
  - *bellman_harris_AR2.py* (_AR3, _AR4) - autoregressive model with 2-3-4 days lag
  - *bellman_harris_W.py* - model with a fixed sliding window length (user has to change the parameter W value in the code)
  - *fixed_GI/bellman_harris_fixed_GI.py* - model with a fixed GI parameter
  - *load_bellman_harris_outputs.py* - loads and processes the outputs of all variants of the model; calculates log-evidence and Bayes Factors based on the Laplace approximation and the referenced TI outputs
  - *posterior_plots.py* - plots of the posterior distributions and generated quantities of different models

