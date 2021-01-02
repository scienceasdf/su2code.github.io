---
title: Installation
permalink: /docs_v7/Installation/
---

---

- [Installing SU2](#installing-su2)
- [Required Software for Running SU2](#required-software-for-running-su2)
  - [Command Line Terminal](#command-line-terminal)
  - [Data Visualization](#data-visualization)
- [Optional Third-Party Software](#optional-third-party-software)
  - [Grid Generation](#grid-generation)
  - [CGNS Library](#cgns-library)
  - [Parallel Tools](#parallel-tools)
  - [Python & Python Modules](#python--python-modules)
  
---

## Installing SU2

SU2 has been designed with ease of installation and use in mind. This means that, wherever possible, a conscious effort was made to develop in-house code components rather than relying on third-party packages or libraries to maintain high portability. In simple cases (serial version with no external libraries), the flow solver can be compiled and executed with just a C++ compiler. 

However, the capabilities of SU2 can be extended using externally-provided software. For example, parallel computations require an installed implementation of MPI (Message Passing Interface) for data communication. Again, to facilitate ease of use and to promote the open source nature, whenever external software is required within the SU2 suite, packages that are free or open source have been favored, and we try to ship, build, and link them automatically for you. These dependencies and third-party packages are discussed below.

**Building from source**: This is the recommended way to get the best compatibility and performance on your machine. Refer to the guides for building SU2 on [Linux/MacOS](/su2/docs_v7/Build-SU2-Linux-MacOS/) or on [Windows](/su2/docs_v7/Build-SU2-Windows/).

The binary executables available on the download page are intended to get new users up and running as quickly as possible. This option is best for new CFD users or those looking to quickly sample some of the features of SU2. To make these binary distributions available to a wide range of potential users, some advanced features requiring external libraries and dependencies have been disabled. For example the Discrete Adjoint method is not available.

No compilation is required for users who select the binary distribution of SU2. Simply extract the binaries, open a terminal, and proceed to the Quick Start Tutorial. Binaries are available for all three platforms. Proceed to the installation guides for [Linux/MacOS](/su2/docs_v7/SU2-Linux-MacOS) or [Windows](/su2/docs_v7/SU2-Windows).

## Required Software for Running SU2

### Command Line Terminal

In general, all SU2 execution occurs via command line arguments within a terminal. For Unix/Linux or Mac OS X users, the native terminal applications are needed. For Windows users, Console is recommended.

### Data Visualization

Users of SU2 need a data visualization tool to post-process solution files. The software currently supports ASCII and binary output formats natively read by ParaView and Tecplot, respectively. ParaView provides full functionality for data visualization and is freely available under an open source license. Tecplot is a commercially-licensed software package widely used by the scientific computing community and is available for purchase. Some SU2 results are also output to comma-separated value (.csv) files, which can be read by a number of software packages. Additional output formats may be added in the future. The two most typical packages used by the development team are the following:
- ParaView
- Tecplot

## Optional Third-Party Software

Although not required, several third-party packages help extend the capabilities of SU2 for particular purposes.  Details of the capabilities enabled in SU2 by adding the packages and how to obtain them are provided here.

### Grid Generation

Users wishing to perform analyses on their own meshes must have a means of generating them. The native SU2 grid format is designed for readability and ease of use: users with simple computational domains can write scripts to generate the appropriate meshes (and some example scripts are provided in the mesh files page). For more complex configurations, grid generation software is recommended, and it should have the capability to export to SU2 or CGNS file formats. Several open-source and commercial products are available, and a list of common options is included below.
- Pointwise
- Gmsh
- ICEM CFD
- Gambit

Note that there are also a number of excellent contributions from the open-source community for creating and converting meshes between various formats (e.g., OpenFOAM to SU2 format). The developers encourage members of the community to share their contributions in this regard, and many of these contributions can be found in the threads of the SU2 forum on CFD Online.

### CGNS Library

To make creating your own meshes easier and more accessible, support for the open CGNS data standard has been included within SU2. The main advantage gained is that complex meshes created in a third-party software package (one that supports unstructured, single-zone CGNS file export) can be used directly within SU2 without the need for conversion to the native format. Moreover, as CGNS is a binary format, the size of the mesh files can be significantly reduced.  If needed, a converter from CGNS to the SU2 format has been built into SU2 (See the inviscid wedge tutorial). Starting with SU2 v4.3, the source code of the CGNS library is shipped with SU2 in the externals/ directory, and it is automatically built and linked for you when compiling SU2. **NOTE: SU2 supports only CGNS files in the ADF format at this time.**

### Parallel Tools

Users wishing to run simulations on distributed-memory computers will need an implementation of the Message Passing Interface (MPI) standard. In these situations, SU2 performs the grid partitioning using the ParMETIS software package. ParMETIS comes packaged with the SU2 source code in the externals/ directory, and it will be automatically built and linked for you. However, you will still need access to an MPI implementation alongside your C/C++ compiler on your system. A variety of implementations of the MPI standard exist, and they can often be installed using package managers on Linux or Mac OS X. Alternatively, users can download and build their own MPI implementations from source. The following are some well-known, freely-available implementations of MPI:
- OpenMPI
- MPICH
- MVAPICH

### Python & Python Modules

Each of the C++ modules for SU2 can be called directly from the command line and do not require Python, including parallel calculations with MPI. However, the coupling of the C++ modules needed for, for example, design optimization problems can be automated via the execution of the appropriate Python scripts included in the software distribution. For instance, when performing shape design, the shape_optimization.py script is available to automate all steps.  Note that this script has additional dependencies on the NumPy and SciPy modules for scientific computing in Python, including optimization routines in the SciPy library. These packages are freely available at the sites linked below:
- Python
- NumPy
- SciPy

Alternatively, Python and these packages can be found in prebuilt installations, such as the Anaconda Distribution, or from package managers like Homebrew for Mac OS X.
