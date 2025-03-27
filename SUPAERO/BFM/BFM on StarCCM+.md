# BFM in StarCCM+

The BFM model implemented on StarCCM+ is based on the implementation by Vincent Maillet. It makes use of Field Functions, for each of the variables, and in the end, for the source terms to be imposed in the flow governing equations.

The normal force implemented is defined as
$$
Fn = \frac{1}{2} K_\text{Mach} K_n \frac{2 \pi \delta}{s b |n_\theta|} W^2
$$


The tangential force is defined as
$$
Fp = \frac{1}{2} \left(  \frac{ 2 C_f K_{pc} +  K_{p0} + K_{p1} K_\text{Mach} 2 \pi (\delta - \delta_\text{ref})}{s b |n_\theta|} W^2 \right)
$$

with the correction term $K_{p1}$ being defined as
$$
K_{p1} = K_{p1} (Q_\text{min}) + \frac{Q-Q_\text{min}}{Q_\text{max}-Q_\text{min}} \left(K_{p1} (Q_\text{max}) - K_{p1} (Q_\text{min})  \right).
$$

Setting $K_{p0} = K_{p1} = 0.0$ and $K_{pc}=1.0$ leads to the model by Hall and Thollet without calibration.

At the writting of this document, only the uncalibrated version of the model has been used. There might be some issues (bugs) if one tries to run the model with calibration.

## Folder contents

This folder contains the following files/folders:
- */*
	- *BodyForceModel.java* : The java macro that implents the BFM sources into an existent StarCCM+ simulation (given that it meets the requirements written below)
- */2D* : 
	- *2d_bfm_example.sim* : Basic 2D (axysimmetric) BFM simulation example.
- */3D* : 
	- *3d_bfm_example.sim* : Basic 3D BFM simulation example.

## Requirements for the simulation

The macro file that implements the BFM into a StarCCM+ containts comments that try to clearly explain how the model is implemented. Here is a brief description of the requirements for the simulation to be ready for the macro to be run.

In general, there should be a different region for each BFM model (stator, rotor)

### Naming
The naming of the parts has to be consistent with what the java macro that implements the BFM in a simulation is expecting. This naming is flexible (the macro allows for customization). The defaults are:
  - X_rotor; X_inter; X_stator -> naming for rotor, inter space, and stator regions, where X goes from 1 to the number of stages/propulsors
  - X_FI (fluid in, the region/part where the flow comes from and enters the rotor region/part)
  - X_FO (outlet region, where the flow comes out of the rotor or stator region)
  
In the case there is only a rotor (and no inter and stator parts), the macro requires that the name of the "Inter Region" should be defined as the same as the outlet region (X_FO by default). This is explained in the macro file

### Positioning of the parts
Here it will be assumed that the simulation is to be used in an optimization (or parametric study). Having the BFM parts in a fixed position, no mather of how the other geometries change, makes things easier. If the BFM parts positions change, the position of the local coordinate system of the rotor (and stator) will have to change as well, which traduces in an extra step to be performed whenever the geometry changes.

The (x,y) = (0,0) is located at the intersection of the rotor leading edge and the shroud (the BFM tables should be defined consistently with this).