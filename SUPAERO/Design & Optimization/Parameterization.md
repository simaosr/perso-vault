# CPACS
> The Common Parametric Aircraft Configuration Schema (CPACS) is a data definition for the air transportation system. CPACS enables engineers to exchange information between their tools. It is therefore a driver for multi-disciplinary and multi-fidelity design in distributed environments. 
> CPACS describes the characteristics of aircraft, rotorcraft, engines, climate impact, fleets and mission in a structured, hierarchical manner. Not only product but also process information is stored in CPACS. The process information helps in setting up workflows for analysis modules. Due to the fact that CPACS follows a central model approach, the number of interfaces is reduced to a minimum. 

- [x] Can it be used to define the shape of the nacelles?
	- **USE PANG**

# Tigl
> The TiGL library is an open source geometric library specially developed to handle CPACS files. It includes the TiGL-Viewer, an interactive user interface which can be used to inspect the CPACS geometry. 

> TiGL thus provides the interface between the parametric CPACS description of the aircraft and the simulation tools. TiGL offers functions for exporting the geometry to common CAD formats (IGES, STEP, VTK) as well as functions for calculating points and curves on the aircraft surface.

> TiGL uses the OpenCASCADE CAD kernel to model the aircraft geometry with NURBS surfaces. The library also provides interfaces to many common programming languages such as C, C++, Python, Java and MATLAB. In addition, the TiGL software package includes the TiGL Viewer that enables also the visualization of the aircraft geometries and other CAD files. 

- It's not differentiated -> for GB algorithm, derivative must be calculated using finite-differences
- Well integrated with CPACS (good for exchange of geometry and may help parameterization)
- Can be easily installed using anaconda
- The backbone of TiGL surface modeling algorithms is the curve network interpolation based on Gordon surface

# Free-Form Deformation
Developed by Sederberg (1986) to model solids, it has its recognition not only due to its versatility, but also since it does not manipulate directly the geometry of the object, in opposition of other parametrization techniques, but the lattice of a certain region in the domain where the object is embedded. 

For two-dimensional cases the region looks like a rectangle and like a parallelpiped for 3D cases. A set of control points $\bm{P}_{i,j,k}$ are defined on the surface of the enclosing region. Their number depends on the order of the chosen Bernstein polynomials. The points inside this region can then be parameterized as r

$$
	\bm{x}_\text{FFD} = \sum_{i=0}^{l}\sum_{j=0}^{m}\sum_{k=0}^{n} B^l_i(s) B^m_j(t) B^n_k(u) \bm{P}_{i,j,k},
$$

where $l, m, n$ are the degrees of the FFD function, $s, t, u \in [0,1]$ are the parametric coordinates of $\bm{x}$ and $B^l_i(s)$, $B^m_j(t)$ and $B^n_k(u)$ are the Bernstein polymonials. By modifying the control points defined along the boundaries of the parallelpiped region, the points inside (and thus, the geometry they define) inherit a smooth deformation.

## Software
1. Star-CCM+
	I believe Star-CCM+ has FFD implemented. Something to check!
	
2. [pyGeo](https://github.com/mdolab/pygeo), part of the [MACH-Aero](https://github.com/mdolab/MACH-Aero) framework from MDOlab.
	> pyGeo is an object oriented geometry manipulation framework for multidisciplinary design optimization. It provides a free form deformation (FFD) based geometry manipulation object, an interface to NASA's Vehicle Sketch Pad geometry engine, a simple geometric constraint formulation object, and some utility functions for geometry manipulation.

# CST Curves

A CST curve can be defined as 

$$
\zeta(\psi) = C^{N_2}_{N_1}(\psi) S(\psi) + \psi \zeta_T,
$$

where $C^{N_2}_{N_1}$ is the class function and $S$ is the shape function. 

The class function defines the general class of the curve (its general shape) and is defined from the terms $N_1$ and $N_2$ as

$$
C^{N_2}_{N_1} = \psi^{N_1}[1-\psi]^{N_2}.
$$

Some examples of values of $N_1$ and $N_2$ are:
| N1    	| N2    	| Description                                         	|
|-------	|-------	|-----------------------------------------------------	|
| 0.5   	| 1     	| NACA-type round nose and pointed aft end airfoil    	|
| 0.5   	| 0.5   	| elliptic airfoil or an ellipsoid body of revolution 	|
| 1.0   	| 1.0   	| biconvex airfoil or an ogive body                   	|
| 0.75  	| 0.75  	| radius distribution of a Sears–Haack body           	|
| 0.75  	| 0.25  	| low-drag projectile                                 	|
| 1.0   	| 0.001 	| cone or wedge airfoil                               	|
| 0.001 	| 0.001 	| rectangle, circular duct, or circular rod           	|


The shape function $S$ 