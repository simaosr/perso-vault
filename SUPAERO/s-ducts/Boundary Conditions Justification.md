# Boundary conditions

## Inlet boundary conditions

The inlet boundary conditions for the s-duct simulation are defined from flight mach number, with total pressure being imposed with a BLI profile, and total temperature being directly obtained from the insentropic relations.

## Boundary Layer ingestion

The boundary layer resultant from the airframe can be modeled at the inlet using the following velocity profile

$$
u = u_\infty f_\text{BLI}
$$
with
$$
 f_\text{BLI} = \left\{\begin{matrix}
\left(\frac{Y}{\delta} \right)^\frac{1}{7} &    & Y <  \delta\\ 
1.0 &  & Y \geq \delta
\end{matrix}\right.,
$$
where $Y$ is the vertical position along measuring from the bottom of the inlet, and $\delta$ is the height of the boundary layer. Inserting this profile in the equation for total pressure leads to
$$
p_{t1} = p_1 \left(1+  \frac{\gamma-1}{2} f_\text{BLI}^2 M_1^2\right)^{\frac{\gamma}{\gamma - 1}}.
$$
Total temperature is kept constant at the inlet.