- Simulations are performed via python scripts
	- Python -> Java file (macro) -> Star-CCM+
- Meshing is automated
- Sensitivity to surfaces is computed assuming a spring-analogy based mesh deformation (from the manual)
- Body forces are introduced using custom field variables (?)

- Difference between .java file and .sim file (both are needed?)


- Asks me for password everytime, not good for optimization...



# Defining pressure valures
Simcenter STAR-CCM+ simulates various pressure quantities, depending on the model selection.
- **Reference Pressure**— a device that reduces the numerical roundoff error in the numerical calculations involving pressure.
- **Working Pressure**— the solution variable that is used in the flow models in Simcenter STAR-CCM+. In the code and in the documentation, this variable is mentioned most of the time as Pressure. Its definition is a matter of computational convenience and depends on the model selection. It is always expressed relative to the Reference Pressure.
In laminar flows without the influence of gravity, Pressure is equal to the static gauge pressure. If the gravity model is active, Pressure is equal to the piezometric pressure, as shown in Eqn. (766) for variable and constant density flows.
When a turbulence model is used, Working Pressure includes the contribution of . This contribution can be considered negligible in most flows of engineering interest.
- **Static Pressure**— the spherical part of the stress tensor acting in fluids (see Eqn. (846)). It happens that the static pressure is the same as the thermodynamic pressure, which is one of the state variables.
- **Absolute Pressure**— static pressure + reference pressure.
- **Relative Total Pressure**— the static pressure that results from isentropically bringing the flow to rest in the relative frame of motion.
- **Total Pressure**— For compressible fluid, total pressure is calculated assuming an isentropic expansion from the total (stagnation) to the actual flow conditions.
For incompressible fluid, total pressure is working pressure + dynamic pressure, .
- **Absolute Total Pressure**— total pressure + reference pressure + where is the reference density, is the altitude, and is the reference altitude.


For simulations using the Ideal Gas model the following guidelines are suggested for setting the reference pressure:
- If the Mach numbers are low (say 0.3 or less), set the reference pressure to some ambient value such that the working pressures are small.
- If the Mach numbers are substantial, you can do one of the following:
	- Set the reference pressure to an ambient value such that the working pressures are small.
	- Set the reference pressure to zero so that working pressures are identical to the absolute pressures.
Specify the pressure location manually when conditions require it.


## From Helicopter tutorial
The interesting parameter in our case is the « Reference Pressure ». The default value is the standard atmospheric pressure (101 325 Pa). It is important to note that « Pressure » (i.e. the static pressure) and « Total Pressure » are defined and calculated in star CCM+ with gauge values relative to that « Reference Pressure ». We obtain the following equations respectively for the static and total pressures :
- Absolute Pressure=Reference Pressure+ Pressure
- Absolute Total Pressure=Reference Pressure+Total Pressure

### For incompressible flow or compressible flow with low pressure fluctuations, 

it is recommended to choose a value of « Reference Pressure » to have fluctuations of pressure around a mean value of 0. In our case, we will define 
- a « Reference Pressure » of 101 325 Pa
- initial and boundary pressures (explained further) of 0 Pa

The computed values for the pressure at the end of the simulation will vary slightly around 0. We do not need to change the default value of 101 325 Pa for « Reference Pressure ». 

### If the simulation were calculated at high altitude conditions with an atmospheric pressure of 25 000 Pa, we would define :
- a « Reference Pressure » of 25 000 Pa
- initial and boundary pressures (explained further) of 0 Pa

The computed values for the pressure at the end of the simulation would also vary slightly around 0. 

### For high compressible flow with high pressure fluctuations (ex : presence of shock waves), 

it is recommended to set the value of «Reference Pressure» to 0, and the pressures and the absolute pressures are equal. If it were our case, we would define :
- a « Reference Pressure » of 0 Pa
- initial and boundary pressures (explained further) of 101 325 Pa

The computed values for the pressure at the end of the simulation would vary strongly around
101 325 Pa.


# Available version
STAR-CCM+ 13.04.011 (linux-x86_64-2.12/gnu7.1-r8 Double Precision)

# Adjoint Solver
The Star-CCM+ adjoint solver can handle the SA turbulence model. All other turbulence models convert into the Constant Eddy Viscosity (CEV) simplification.


# Python integration

OpenMDAO wrapper: https://github.com/OpenMDAO-Plugins/StarCCM_wrapper

This guy: https://github.com/zhzclb/STAR-CCM-Aerodynamic-Shape-Optimization

# Macros (JAVA)

To create a framework, must be compiled calling the java API located in $INSTALLDIR/star/lib/java/platform/modules/etc (I think this is enough)

This to create a .jar file and call it in starccm with the classpath. The macros are called directly as .java files and do not need compiling (if not using any framework it is simpler to call).


# Running with classpath and macro file

`starccm+ -podkey 99x/BY9DTLo8CTxlwSQ4FA -licpath 1999@flex.cd-adapco.com -power -np {#NODES} -classpath {JARFOLDER} -batch {JAVAMACROFILE} -new {SIMFILE} > {OUTPUTFILE} & tail -f {OUTPUTFILE}`


# How to load bodies into Star-CCM so they remain with individual bodies.

STEP files created with export_shapes are not always read as we intend them to by STAR-CCM+.
