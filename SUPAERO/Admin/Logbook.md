# 8/10/2021
- Setup wedge simulation
- Try to solve StarCCM+ problems with convergence
	- Shock is created after stator
- Everything takes longer because of license problem (~one week ago)
# /10/2021
- Setup axi simulation
- Change macro for BFM to fit axi 2D sim
- Create geometry for 2d axi sim

# 27/10/2021
- Finished macro for IDC rings and IDC report
# 26/10/2021
- Creating more tests for geometry generation
- Testing new geometry of fan with constraints
- BFM table generation reading (trying to remember Emmanuel's procedure)

# Inbetween
- Finished pystarccm
	- Capable of sending and retrieving files from PANDO
	- Launch jobs easily on PANDO
- Finished working optimization framework for airfoils
	- Creates DOE and generates geometries by replacing part in template simulation
	- Runs all the geometries by uploading them to PANDO and running a job for each
		- Requires specific macros
	- Manually retrieve data from CSV's:
		- Create pandas dataframe
	- Creates Surrogate(s) using SMT
	- Use surrogate in optimization with pyoptsparse
	- Create new geometry from optimal
	- This framework is adaptable to any aerodynamic shape optimization case:
		- Create template simulation
		- Create shape translator (form design vars to geometry)
		- Reuse all other functions
- Rewrote geometry shape functions into classes
	- CSTDuct
	- FanCore
	- CSTAirfoil
	- Nacelle
This was done to understand the geometry creation code and to make it easily usable in an optimization case.
- Changed CST's to be able to use b's directly*
	- Testes that with DOE and optimization:
		- Provides better control of shapes
		- iCSTS are too nonlinear
- Helped Billal in his questions and problems with StarCCM+
- Abstract ISABE
- Simulation on initial imothep s-duct geometry with BFM
- Try to implement 2D case
- Explore StarCCM+ (meshing, etc)
- Create multiple StarCCM+ macros for automation
- Define Metrics (including bibliographic study/report)

# 27/04/2021
- managed to get starccm+ to run on pando multiple times in one job.

# 26/04/2021
- documentation
- reading
- meeting

# 22/04/2021


# 21/04/2021


# 20/04/2021
- Managed to call starccm+ via a python script, running with a defined macro and output an objective function
- meeting in the afternoon

**TODO**
- Create script to read design variables from csv file
- try running on PANDO
- READ ABOUT PARTS BASED MESHING VS REGION BASED MESHING

# 19/04/2021
- Managed to compile .java into .jar with netbeans (by adding libraries) 
- Managed to run a simulation with the macro that calls the (now FASTA) framework
- Managed to output Cd (defined as a report and a variable on a csv file)
- FASTA needs 3d version of some functions to be implemented.
- parts based meshing!

**TODO**: 
- call via a python script (**CHECK**)
- try running on PANDO

# 16/04/2021
- Meeting, in the afternoon.
- Try compiling .java into .jar

# 15/04/2021

- RDV
- install OpenMDAO and try it
- Read about .java .sim and starccm with python

# 14/04/2021

- RDV
- StarCCM+ Tutorial
- Try pyOptSparse
- Look for python interfaces to StarCCM+

# 13/04/2021

- Computer arrived
- Try installing everything
- Try pyOptSparse
- Try RCE

# 12/04/2021

- B-Splines/NURBS, CST reading
- Reunião

# 09/04/2021
- Read pang documentation
- Pang jupyter notebooks
- Reunião

# 08/04/2021

- "Welcome" zoom call

# 07/04/2021

# 06/04/2021

# 02/04/2021

# 01/04/2021
- Arriving