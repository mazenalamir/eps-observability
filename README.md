# Python module for checking partial observability of general nonlinear uncertain dynamical systems

This modules implements the observability check proposed in the paper:

M. Alamir. Observability Certification and Optimal Design of Nonlinear Observation Parameters in the Presence of Measurement Noise and Model Mismatches. arXiv:2006.11112. June 2021

**Code citation**: 

[![DOI](https://zenodo.org/badge/368786756.svg)](https://zenodo.org/badge/latestdoi/368786756)


## Problem statement 

We consider general uncertain nonlinear dynamical system that can be described by a set of Ordinary Differential System (ODE) of the form:

```python
def syst(x,t,u,p):
  ...
  xdot=...
  return xdot
```
where:
- ```x``` stands for the state 
- ```u``` stands for the exogenous input 
- ```p``` stands for a vector of uncertain parameters

Assume that sensors are available that provides outputs through a dedicated map such as:

```python
def output(x, u, p):

    # The equation that defines the measured output other than the input u
    output = ...
    return output
```
Note that we are mainly interested in the case where measurement noise is present that is to be added to the above defined output map. 
### The observability problem 
The problem of observability amounts at finding the current values of the state and the parameter vector based on a observation windown 
(spanning from the recent past up to the current time. This is a standard dynamic reconstruction problem knwon as the extended observability problem 
(due to the fact that not only the state is to be reconstructed but also the vector of parameters). This feasibility of this task in the general nonlinear 
setting is quite difficult and many works exists that gives sufficient condition for the existence of nonlinear observer that might converges asymptotically to 
the true values. 

### The partial eps-observability 
This version of the problem differs from the general above mentioned case by two features:

1. The quantities that one is interested in reconstructing is not necessarily the whole extended vector ```(x,p)```. Rather a function ```z=T(x,p)``` is to be reconstructed which is called **the observation target**. 
2. One is not necessarily interested by a situation where a perfect reconstruction is possible but also by situation where on can be sure that the reconstruction error is lower than some eps>0

Note that one commonly interesting 
### The partial almost eps-observability 
Even in its above mentioned relaxed version, the assessment of an upper bound eps on the **observation target** might be impossible. That is the reason why the module focus on deriving 
statistically assessment with some precision and confidence levels that are generally associted to probabilistic certification via randomized optimization framework 
which is the approach adopted in this module. 

## Package content

The solution includes two python files and one jupyter notebook:

### observability_certification.py 

The generic module that implements the solution 

### problem_specific_def.py

The problem specific definitions including the definition of the dynamics, the functions that enable to generate the cloud of scenarios for the probabilistic 
certification framework. 

### check_partial_almost_eps_observability.ipynb

A Jupyter notebook that illustrate the use of the module. 


## References

M. Alamir. Observability Certification and Optimal Design of Nonlinear Observation Parameters in the Presence of Measurement Noise and Model Mismatches. arXiv:2006.11112. June 2021 
(also submitted in a revised version to IEEE TRansactions on automatic control. 
