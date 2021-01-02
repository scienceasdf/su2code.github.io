---
title: The SU2 Tutorial Collection
permalink: /tutorials/home/
redirect_from: /tutorials/index.html
disable_comments: true
disable_header: true
written_by: economon
for_version: 6.0.0
revised_by: talbring
revision_date: 2019-11-27
revised_version: 7.0.0
---

## Getting started with SU2

Rather than writing a long manual on all available (and constantly evolving) configuration options available in SU2, the approach has been taken to teach the various aspects of the SU2 code through a range of tutorials. If you would like to see all of the available config options, we keep a configuration file template in the root directory of the source distribution (see [config_template.cfg](https://github.com/su2code/SU2/blob/master/config_template.cfg)).

The tutorials are numbered roughly in order of their complexity and how experienced with the code the user may need to be, noting that the more advanced tutorials may assume the user has already worked through the earlier ones. Each tutorial attempts to present new features of SU2 and contains explanations for the key configuration file options. More information on the exact learning goals of a tutorial can be seen at the beginning of each.

You can get all the mesh and config files either by cloning or downloading the [tutorial repository](https://github.com/su2code/Tutorials) or by downloading them separately using the provided links on each tutorial page.

**Note:** Before beginning with the tutorials, please make sure to check out the information on how to [download](/su2/docs_v7/Download/) and [install](/su2/docs_v7/Installation/).

## Summary of tutorials
------

#### Compressible Flow

* [Inviscid Bump in a Channel](/su2/Tutorials/Inviscid_Bump/)   
A simulation of internal, inviscid flow through a 2D geometry.
* [Inviscid Supersonic Wedge](/su2/Tutorials/Inviscid_Wedge/)    
Get familiar with a basic supersonic flows with analytical solution.
* [Inviscid ONERAM6](/su2/Tutorials/Inviscid_ONERAM6/)    
Simulation of external, inviscid flow around a 3D geometry (isolated wing).
* [Laminar Flat Plate](/su2/Tutorials/Laminar_Flat_Plate/)   
Simulation of external, laminar flow over a flat plate (classical Navier-Stokes validation).
* [Laminar Cylinder](/su2/Tutorials/Laminar_Cylinder/)    
Simulation of external, laminar flow around a 2D cylinder.
* [Turbulent Flat Plate](/su2/Tutorials/Turbulent_Flat_Plate/)    
Simulation of external, turbulent flow over a flat plate (classical RANS validation).
* [Transitional Flat Plate](/su2/Tutorials/Transitional_Flat_Plate/)    
Simulation of external, transitional flow over a flat plate (transitional latminar-turbulent case).
* [Turbulent ONERAM6](/su2/Tutorials/Turbulent_ONERAM6/)     
Simulation of external, viscous flow around a 3D geometry (isolated wing) using a turbulence model.
* [Unsteady NACA0012](/su2/Tutorials/Unsteady_NACA0012/)     
Simulation of unsteady, external, viscous flow around an airfoil.
* [Epistemic Uncertainty Quantification of RANS predictions of NACA 0012 airfoil](/su2/Tutorials/UQ_NACA0012/)    
Perform uncertainty quantification of errors arising due to assumptions inherent in turbulence models.
* [Non-ideal compressible flow in a supersonic nozzle](/su2/Tutorials/NICFD_nozzle/)    
Simulation of compressible flow in a nozzle using non-ideal thermodynamic models.

#### Incompressible Flow

* [Inviscid Hydrofoil](/su2/Tutorials/Inc_Inviscid_Hydrofoil/)   
A simulation of internal, inviscid, incompressible flow around a NACA 0012 hydrofoil.
* [Laminar Flat Plate with Heat Transfer](/su2/Tutorials/Inc_Laminar_Flat_Plate/)    
Simulation of external, laminar, incompressible flow over a flat plate (classical Navier-Stokes case).
* [Turbulent Flat Plate](/su2/Tutorials/Inc_Turbulent_Flat_Plate/)    
Simulation of external, turbulentm incompressible flow over a flat plate (classical RANS case).
* [Turbulent NACA 0012](/su2/Tutorials/Inc_Turbulent_NACA0012/)    
Simulation of external, viscous, incompressible flow around the NACA 0012 using a turbulence model.
* [Laminar Backward-facing Step](/su2/Tutorials/Inc_Laminar_Step/)    
Simulation of internal, laminar, incompressible flow over a backward-facing step with an inlet velocity profile input from file.
* [Laminar Buoyancy-driven Cavity](/su2/Tutorials/Inc_Laminar_Cavity/)    
Simulation of internal, laminar, incompressible flow in a differentially-heated cavity under the influence of gravity (classical natural convection case).
* [Heated Cylinders with Conjugate Heat Transfer](/su2/Tutorials/Inc_Heated_Cylinders/)     
Simulation of a coupled CHT problem incorporating multiple physical zones.

#### Structural Mechanics
* [Linear Elasticity](/su2/Tutorials/Linear_Elasticity/)  
Simulation of an elasticity problem with small deformations
* [Linear Dynamics](/su2/Tutorials/Linear_Dynamics/)  
Simulation of a dynamic structural problem with small deformations
* [Non-linear Elasticity](/su2/Tutorials/Nonlinear_Elasticity/)  
Simulation of a non-linear structural problem with large deformations
* [Multiple Materials](/su2/Tutorials/Multiple_Material/)  
Simulation of a non-linear problem with multiple material definitions

#### Multiphysics
* [Static Fluid-Structure Interaction](/su2/Tutorials/Static_FSI/)  
Non-linear structural mechanics coupled with incompressible Navier-Stokes flow

#### Shape Design Features

* [Unconstrained shape design of an transonic inviscid airfoil at a cte. AoA](/su2/Tutorials/Inviscid_2D_Unconstrained_NACA0012/)
Get a basic introduction to the SU2 design capabilities by performing an optimal shape design of a 2D geometry (isolated airfoil) without constraints.
* [Constrained shape design of a transonic turbulent airfoil at a cte. C<sub>L</sub>](/su2/Tutorials/Turbulent_2D_Constrained_RAE2822/)    
Perform an optimal shape design of a 2D geometry (isolated airfoil at turbulent regime) with flow and geometrical constraints.
* [Constrained shape design of a transonic inviscid wing at a cte. C<sub>L</sub>](/su2/Tutorials/Inviscid_3D_Constrained_ONERAM6/)    
Learn the basis of 3D design by performing an optimal shape design of an isolated wing with geometrical constraints.
* [Multi-Objective Shape Design of an Inviscid Supersonic Ramp](/su2/Tutorials/Multi_Objective_Shape_Design/)    
 Perform an optimal shape design with multiple objectives and a penalty function
* [Unsteady Shape Optimization](/su2/Tutorials/Unsteady_Shape_Opt_NACA0012/)  
 Shape optimization of an 2D airfoil in unsteady flow conditions.
