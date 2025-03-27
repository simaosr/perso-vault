## RCE
> RCE is an Open Source distributed, workflow-driven integration environment. It is used by engineers and scientists to design and simulate complex systems (e.g., aircraft, ships, or satellites) by using and integrating their own design and simulation tools. There are special wrapping functionalities for CPACS implemented in RCE, making the integration of CPACS compatible tools fairly easy. 

- Comes together with DAKOTA optimizers
- Can *easily* use pyOpt (via python script)

## OpenMDAO
> OpenMDAO is an open-source optimization framework and a platform to building new analysis tools with analytic derivatives.
- Might not be as user friendly (visualy)
- Better suited for Multidisciplinary Optimization
## DAKOTA
https://dakota.sandia.gov/
> DAKOTA contains algorithms for optimization with gradient and nongradient-based methods; uncertainty quantification with sampling, reliability, stochastic expansion, and epistemic methods; parameter estimation with nonlinear least squares methods; and sensitivity/variance analysis with design of experiments and parameter study methods. 
- Bunch of optimizers and tools for design of experiments, uncertainty quantification, etc.
## pyOpt(Sparse)
https://github.com/mdolab/pyoptsparse
> pyOptSparse is an object-oriented framework for formulating and solving nonlinear constrained optimization problems in an efficient, reusable, and portable manner. It is a fork of pyOpt that uses sparse matrices throughout the code to more efficiently handle large-scale optimization problems. Many optimization techniques can be used in pyOptSparse, including both gradient-based and gradient-free methods. A visualization tool called OptView also comes packaged with pyOptSparse, which shows the optimization history through an interactive GUI.

> pyOptSparse provides Python interfaces for a number of optimizers. ALPSO, CONMIN, IPOPT, NLPQLP, NSGA2, PSQP, SLSQP, ParOpt and SNOPT are currently tested and supported. NOMAD interface is also provided, but it is not tested nor supported.

## SMT: Surrogate Modeling Toolbox
https://github.com/SMTorg/SMT
>The surrogate modeling toolbox (SMT) is an open-source Python package consisting of libraries of surrogate modeling methods (e.g., radial basis functions, kriging), sampling methods, and benchmarking problems. SMT is designed to make it easy for developers to implement new surrogate models in a well-tested and well-document platform, and for users to have a library of surrogate modeling methods with which to use and compare methods.

