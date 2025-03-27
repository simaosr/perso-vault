The parameterization of the s-ducts can be done in many different ways. In my work I present what I call the Arbitrary Section Parametrization (ASP). This consists in defining arbitrary shaped sections along the length of the duct, and creating a surface from this sections (also called guides), either with a sweep operating, or by constructing a gordon surface from a network of curves.

The sections can be defined either at their absolute position or their relative position along a defined spine. Along with their position, a rotation can also be defined, either by their absolute value (and axis), or a rotation according to the spine (perpendicular to the spine).


## Shape of sections (or guides)
The sections are defined by a NURBS curve. This NURBS curve can be either defined directly from their control points, or generated according to a wrapper parameterization that generates the NURBS curve (or B-Spline) from a given set of parameters:

### iCST curves
These intuitive Class Shape Transformation curves are defined 

### Super-ellipse

A superellipse, also known as a Lamé curve, is a closed curve resembling an ellippse. It retains the geometric fectures of semi-major and semi-minor axes, as well as the symmetry about them, while presenting a different overall shape. It is defined, in the cartesian coordinate system, as 
$$
\left|\frac{x}{a}\right|^n + \left|\frac{y}{b}\right|^n = 1.
$$

When $n=1$, the curve is an ordinary ellipse (a circle if $a=b$), while for $n>2$, the curve looks like a rectangle with rounded corners. Curvature is zero at (+-a, 0) and (0, +-b).


## Gordon surface (curve network)

To generate the gordon surface, the sections curves are not enough. There is a requirement of aditional lengthwise curves (hereby called profiles) that intersect all the sections (see Fig). These can be generated in two ways.