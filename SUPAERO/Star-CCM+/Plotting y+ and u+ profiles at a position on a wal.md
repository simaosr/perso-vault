

Plotting y+ and u+ profiles at a position on a wall

To illustrate the procedure, the flow around a NACA airfoil is analyzed. A point has been defined as a derived part on the lower surface by intersecting planes and surfaces.

The velocity profile normal to the wall is analyzed at this point.

Flow around a NACA airfoil

A local coordinate system is created at the point. First, the wall normal is extracted in a table:

    Input parts: the derived part "point on surface"
    Scalar: all components of the Area vector

This table consists of 6 columns and 1 row: Area, Area, Area, X,Y,Z

 

Create local coordinate system

The next step is to create a new Cartesian coordinate system "Cartesian 1" in Tools > Coordinate Systems:

    origin : (X,Y,Z) from the previous table.
    j Direction : (Area, Area, Area) from the previous table
    i Direction : (-Area, Area, 0) is a possible vector perpendicular to the j Direction

Create a new Cartesian coordinate system

For an accurate positioning of the coordinate system, it is recommended to export the previous table as a csv file and to open the file that contains the data with all digits.

After that, a derived part is created by intersecting a plane normal to the Y direction of "Cartesian 1" and a plane in the streamwise direction.
To achieve this, select "Cartesian 1" as the Coordinate System when creating the derived part.

The intersection of the 2 planes produces a line section.

A threshold is then used to extract just a part of this line section near the wall:

Derived part created

 

The velocity profile can be plotted directly on the threshold, as illustrated in the following image. Here, the boundary layer can be seen:

 

Threshold from normal section

In order to plot the velocity in the dimensionless parameters u+ and y+, the following report and field functions must be written :

1. Maximum report:

    name: WallShearStress
    input parts: "point on surface"
    scalar: "Wall Shear Stress Magnitude"

2. Field function:

    name: Utau
    definition: sqrt($WallShearStressReport/$Density)

In this procedure, the reference velocity is defined as a friction velocity based on the wall shear stress report. This can only be done once the wall shear stress in known. In practice, STAR-CCM+ computes the reference velocity prior to the computation of the wall shear stress, using turbulent quantities specific to the particular turbulence model.

3. Field function:

    name : y+
    definition : $Utau*$WallDistance*$Density/$DynamicViscosity

4. Field function:

    name : u+
    definition : 

In the previous expression, the magnitude of the velocity parallel to the wall is required. In the local coordinate system, the direction i and k are parallel to the wall, therefore the magnitude of (Vx, 0, Vz) in the local coordinate system is chosen.

The field functions u+ and y+ can then be displayed in an X-Y plot using the threshold line section as an input part:

Viscous sublayer plot

In this plot, the viscous sublayer, transition layer, log layer and far field are visible. The y+ range for which the data points match the log layer correlation will depend on the Reynolds number.