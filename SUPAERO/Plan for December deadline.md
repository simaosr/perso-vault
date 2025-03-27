
## Priority
- [ ] 2D Axysim case
    Change model...
        Change computation of velocities to cylindrical
    Use Emmanuels geometry/cases

## TO-DO

- [x] Figure out which dimensions to assume:
	- [x] Use new geometry from last IMOTHEP meeting (ES_1)
- [ ] Create Initial Geometries:
	- [ ] 2D case (for cowl shape optimization)
	- [ ] S-duct with/without BFM
	- [ ] Nozzle
	- [ ] Full geometry (cowl+sduct+fan+nozzle+interfan)
- [ ] Create tables for BFM of new geometry/fan design

- [ ] Define Metrics
	- [ ] **Define location of AIP**
		- Many papers use 1 radius after end of s-duct. We dont have that...
	- [ ] Swirl
	- [x] Total pressure loss
	- [ ] Distortion
	- [x] Efficiency
	- [x] Pressure Ratio
- [ ] Mesh and Run Simulations
	- [x] Mesh convergence
		- **Changing parts makes non-convergence...**
	- [ ] Geometry tweaks for unwanted flow features
	- [x] *Adjoint-based sensitivity
		- **Does not work with BFM AFAIK**
## Post
- [ ] Design of Experiments
	- [ ] Define parameters and bounds for DOE
	- [ ] Run DOE
- [ ] Optimization
	- [ ] Use DOE for Surrogate-based Optimization
		- Check for DOE feasibility
		- Try to bound correctly not to have bad geometries
	- [ ] Improve Surrogate with new datapoints
		- WB2
		- Exploration (use optimum as new infill point)