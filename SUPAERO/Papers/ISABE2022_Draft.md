# Intoduction
- **BWB concept**
The concept of the Blended Wing Body (BWB), where there is no distinction between the wing and the main body of the aircraft appeard in the 1920s and has since been recurently approached due to its potential advantages regarding increased fuel efficiency, or lower noise emissions, amongst others.

- **BLI**
Closely related to the BWB is the aero-propulsive concept of Boundary Layer Ingestion (BLI), in which the propulsor ingest the boundary layer that develops over the airframe. By doing so, it is able to improve the overall efficiency of the aircraft. This advantage comes with certain drawbacks, as the lower speed flow entering the fan can cause instabilities on the propulsor, reducing its efficiency or leading to its premature failure.

- **S-ducts**
The intakes of embebed engines usually take the shape of S-ducts
The difusion of the air in a s-duct occurs faste than in a conventional straight duct, leading to shorter more compact ducts, facilitating an easier integration and lower weight.
S-ducts can be very varied in terms of their cross-section shape and area, starting with rectangular, oval, semi-elliptical, etc. cross sectional shapes at the inlet, and transictioning to a circular shape at the fan face. Other key parameters that define an S-duct are its length and its offset (the difference in height between the inlet and the outlet of the duct).

- **(CST) parameterization**

- **Paper goal**
This paper presents the methodology for the design of a  

# Methodology

The methodology for aerodynamic shape optimization can vary considerably depending on the type of optimization algorithm used (gradient-based vs gradient-free) or even on the capabilities of the solvers involved. They can generaly be divided into three steps, or components: geometry control and mesh generation, solving of the flow governing equations and optimization algorithm. 

On the first step, a geometry is created (or modified), resultant of a process the receives a certain number of inputs as 


## Geometry parameterization

The key paramerization feature of the present work is the use of CST curves. They were chosen due to their intuitive input parameters and proven results in aerodynamic shape optimization. The S-duct geometry is defined by five CST curves, as can be seen in Fig.XXX, two defining the inlet and outlet cross-section shape and three that define the lengthwise shape of the duct. The curves are interpolated into B-Splines and then a Gordon-Surface is generated from the later.

## Optimization framework

Due to the antecipated long length of time that each simulation will take, as well as the "relatively" large number of design variables, a surrogate-based optimization approach is chosen. For 

##

# Study Case

This paper focus on the case of an XXX s-duct as seen in FIGXXX. Its length, offset and inlet and outlet cross section shape dimensions are presented in TableXXX.

- Mesh convergence

- Flow field analysis

- Definition of objectives for optimization 

### Performance metrics
The pressure recovery is defined as
$$
PR = \frac{p_{0,\text{out}}}{p_{0,\text{in}}}
$$

Circumferential flow distortion can be described by

$$
IDC =
$$

often called the circumferential distortion index (IDC).

# Results

In this section, the results of the previous ...

# Conclusions
