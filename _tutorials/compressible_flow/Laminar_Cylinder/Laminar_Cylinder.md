---
title: Laminar Cylinder
permalink: /tutorials/Laminar_Cylinder/
written_by: economon
for_version: 7.0.0
revised_by: talbring
revision_date: 2020-03-03
revised_version: 7.0.2
solver: Navier_Stokes
requires: SU2_CFD
complexity: basic
follows: 
---

![Cylinder Mach](../../tutorials_files/compressible_flow/Laminar_Cylinder/images/cylinder_mach.png)

## Goals

Upon completing this tutorial, the user will be familiar with performing a simulation of external, laminar flow around a 2D geometry. The specific geometry chosen for the tutorial is a cylinder. Consequently, the following capabilities of SU2 will be showcased:
- Steady, 2D Laminar Navier-Stokes equations 
- Multigrid
- Roe convective scheme in space (2nd-order, upwind)
- Corrected average-of-gradients viscous scheme
- Euler implicit time integration
- Navier-Stokes wall (no-slip) and far-field boundary conditions

In this tutorial, we discuss some numerical method options, including how to activate a slope limiter for upwind methods.

## Resources

The resources for this tutorial can be found in the [compressible_flow/Laminar_Cylinder](https://github.com/su2code/Tutorials/tree/master/compressible_flow/Laminar_Cylinder) directory in the [tutorial repository](https://github.com/su2code/Tutorials). You will need the configuration file ([lam_cylinder.cfg](https://github.com/su2code/Tutorials/tree/master/compressible_flow/Laminar_Cylinder/lam_cylinder.cfg)) and the mesh file ([mesh_cylinder_lam.su2](https://github.com/su2code/Tutorials/tree/master/compressible_flow/Laminar_Cylinder/mesh_cylinder_lam.su2)).

Experimental results for drag over a cylinder at low Reynolds numbers are reported in the following article:
D. J. Tritton, "Experiments on the flow past a circular cylinder at low Reynolds numbers," Journal of Fluid Mechanics, Vol. 6, No. 4, pp. 547-567, 1959. Note that the mesh used for this tutorial is rather coarse, and for comparison of the results with literature, finer meshes should be used.

## Tutorial

The following tutorial will walk you through the steps required when solving for the external flow around a cylinder using SU2. It is assumed you have already obtained and compiled the SU2_CFD code for a serial computation. If you have yet to complete these requirements, please see the [Download](/su2/docs_v7/Download/) and [Installation](/su2/docs_v7/Installation/) pages.

### Background

The flow around a 2D circular cylinder is a case that has been used extensively both for validation purposes and as a legitimate research case over the years. At very low Reynolds numbers of less than about 46, the flow is steady and symmetric. As the Reynolds number is increased, asymmetries and time-dependence develop, eventually resulting in the well-known Von Karmann vortex street, and then on to turbulence.

### Problem Setup

This problem will solve the for the external, compressible flow over the cylinder with these conditions:
- Freestream temperature = 273.15 K
- Freestream Mach number = 0.1
- Angle of attack (AOA) = 0.0 degrees
- Reynolds number = 40 for a cylinder radius of 1 m 

### Mesh Description

The problem geometry is 2D. The mesh has 26,192 triangular elements and 13,336 points. It is fine near the surface of the cylinder to resolve the boundary layer. The exterior boundary is approximately 15 diameters away from the cylinder surface to avoid interaction between the boundary conditions. Far-field boundary conditions are used at the outer boundary. No-slip boundary conditions are placed on the surface of the cylinder. 

![Cylinder Mesh](../../tutorials_files/compressible_flow/Laminar_Cylinder/images/cylinder_mesh.png)
Figure (1): The computational mesh for the 2D cylinder test case. 

The outer boundary in red is the far-field, and the small circle in the center is the cylinder which uses the Navier-Stokes Wall boundary condition.

### Configuration File Options

Several of the key configuration file options for this simulation are highlighted here. This case exhibits exceptional convergence, given the combination of very aggressive CFL, linear solver settings, and multigrid. In this tutorial, we would like to highlight the options concerning the specification of convective schemes:

```
% -------------------- FLOW NUMERICAL METHOD DEFINITION -----------------------%
%
% Convective numerical method (JST, LAX-FRIEDRICH, CUSP, ROE, AUSM, HLLC,
%                              TURKEL_PREC, MSW)
CONV_NUM_METHOD_FLOW= ROE
%
% Monotonic Upwind Scheme for Conservation Laws (TVD) in the flow equations.
%           Required for 2nd order upwind schemes (NO, YES)
MUSCL_FLOW= YES
%
% Slope limiter (NONE, VENKATAKRISHNAN, VENKATAKRISHNAN_WANG,
%                BARTH_JESPERSEN, VAN_ALBADA_EDGE)
SLOPE_LIMITER_FLOW= NONE
%
% Coefficient for the Venkat's limiter (upwind scheme). A larger values decrease
%             the extent of limiting, values approaching zero cause
%             lower-order approximation to the solution (0.05 by default)
VENKAT_LIMITER_COEFF= 0.05
```

For laminar flow around the cylinder, we choose the Roe upwind scheme with 2nd-order reconstruction (`MUSCL_FLOW = YES`). This low-speed case is executed without a slope limiter. Note that, in order to activate the slope limiter for the upwind methods, `SLOPE_LIMITER_FLOW` must be set to something other than `NONE`. Otherwise, no limiting will be applied to the convective flux during the higher-order reconstruction. Limiting is not applicable if `MUSCL_FLOW = NO`, as there is no higher-order reconstruction, and thus, no need to limit the gradients. The viscous terms are computed with the corrected average-of-gradients method (by default). Several limiters are available in SU2, including the popular `VENKATAKRISHNAN` limiter for unstructured grids. It is recommended that users experiment with the `VENKAT_LIMITER_COEFF` value for their own applications.

Lastly, it should be mentioned that the MUSCL reconstruction and slope limiting apply *only to the upwind schemes*. If you choose one of the centered convective schemes, e.g., JST or Lax-Friedrich, there is no reconstruction process. JST and Lax-Friedrich are 2nd-order and 1st-order by construction, respectively, and the scalar dissipation for these schemes can be tuned with the `JST_SENSOR_COEFF` and `LAX_SENSOR_COEFF` options, respectively.

### Running SU2

The cylinder simulation for the 13,336 node mesh is small and will execute relatively quickly on a single workstation or laptop in serial. To run this test case, follow these steps at a terminal command line:
 1. Move to the directory containing the configuration file ([lam_cylinder.cfg](https://github.com/su2code/Tutorials/tree/master/compressible_flow/Laminar_Cylinder/lam_cylinder.cfg)) and the mesh file ([mesh_cylinder_lam.su2](https://github.com/su2code/Tutorials/tree/master/compressible_flow/Laminar_Cylinder/mesh_cylinder_lam.su2)). Make sure that the SU2 tools were compiled, installed, and that their install location was added to your path.
 2. Run the executable by entering 
 
    ```
    $ SU2_CFD lam_cylinder.cfg
    ```
   
    at the command line.
 3. SU2 will print residual updates with each iteration of the flow solver, and the simulation will terminate after meeting the specified convergence criteria.
 4. Files containing the results will be written upon exiting SU2. The flow solution can be visualized in ParaView (.vtk) or Tecplot (.dat for ASCII).

### Results

The following results show the flow around the cylinder as calculated by SU2 (note that these were for a slightly higher Mach number of 0.3).

![Cylinder Pressure](../../tutorials_files/compressible_flow/Laminar_Cylinder/images/cylinder_pressure.png)
Figure (2): Pressure contours around the cylinder.

![Cylinder Viscosity](../../tutorials_files/compressible_flow/Laminar_Cylinder/images/cylinder_lam_visc.png)
Figure (3): Laminar viscosity contours for this steady, low Reynolds number flow.

![Cylinder Mach](../../tutorials_files/compressible_flow/Laminar_Cylinder/images/cylinder_mach.png)
Figure (4): Mach number contours around the cylinder with streamlines. Note the large laminar separation region behind the cylinder at Re = 40.
