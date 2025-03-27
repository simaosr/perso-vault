Aerodynamic shape optimization has been...

For the previous decade, with the increase in computational power, the use of high-fidelity numerical tools in the design phase of aircraft components, or even whole aircraft configurations has been an increase. The developments on the field of sensitivity analysis, such as the development of adjoint solvers, has also been a potentiating factor, allowing the use of efficient gradient-based optimization.

The aerodynamic shape optimization problem can be divided into the parameterization, the analysis and the optimization itself. The right choice of the parameterization technique will allow the optimizer to search the whole design space, in the most efficient manner (i.e. using the less amount of design variables). A numerous amount of parameterization techniques exist, such as Hicks-henne bump functions, Free-Form Deformation, NURBS curves, CRS(???), etc; from which the FFD has seen the most use lately. (REF: Samareh, Zang et al...)

Most of this techniques perform some deformation on an initial shape, defined by a discretized set of points, which, is not of particular interest to the industry, where the CAD definition is necessary in order to use the optimal shapes .... Recent developments on the definition of shapes using bla bla bla Diferentiation of the ESP and OpenCascade.

Firstly introduced to the aviation by James, the Adjoint Method (REF: Martins) has seen an increase in use in use in optimization, particularlly due to development of SU2, Adflow, DAfoam, two open-source solvers, but also on proprietary and commercial solvers (Star-CCM+, Fluent, etc). Has led to the more use bla bla bla.

The adjoint has not only been used directly to compute the gradients given to the optimizer, but also to increase the robustness of surrogate-based optimization, as is the case of the Gradient Enhanced Krigging.

ASO is a key factor in 

The use of surrogate-models in the ASO has seen large improvements in the latter years, with the various improvements to the Efficient Gobal Optimization, and SEGOMOE (Super Efficient Global Optimization wih Mixture of Experts).


Codes: SU2, MACH, OpenMDAO, 

Applications: 

BLI shape optimization

Turbomachinery

External aerodynamics