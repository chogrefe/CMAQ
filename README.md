CMAQv5.4
==========

Community Multiscale Air Quality Model US EPA CMAQ Website: (https://www.epa.gov/cmaq).

**Add DOI link**

CMAQ is an active open-source development project of the U.S. EPA's Office of Research and Development that consists of a suite of programs for conducting air quality model simulations.
CMAQ is supported by the CMAS Center: (http://www.cmascenter.org).

CMAQ combines current knowledge in atmospheric science and air quality modeling with multi-processor
computing techniques in an open-source framework to deliver fast, technically sound estimates of ozone,
particulates, toxics, and acid deposition.


## CMAQ version 5.4 Overview:

* [CMAQv5.4 Release Notes](https://github.com/USEPA/CMAQ/wiki/CMAQv5.4-Release-Notes) - Release Notes are available on the CMAQ GitHub wiki.
* [Frequently asked questions for upgrading to the latest CMAQ version](DOCS/Release_Notes/CMAQ_FAQ.md) **- Updated for v5.3.3 release.** 
* [Tutorials for setting up and running CMAQ](DOCS/Users_Guide/Tutorials/README.md) **- Tutorials on running CMAQ, CMAQ-ISAM, CMAQ-DDM, and WRF-CMAQ test cases.**

## New features in CMAQ version 5.4 include:

* Updated chemistry for ozone (O3) and particulate matter (PM) formation from global-to-local scales
* Introduction of the Community Regional Atmospheric Chemistry Multiphase Model (CRACMM)
* Biogenic emissions algorithm options have been expanded
* MEGAN emission model now available online
* Revised algorithms for modeling the dry deposition of particles from the atmosphere (M3DRY and STAGE updates)
* Streamlined building of the WRF-CMAQ compatible with WRFv4.4+ 
* Improved efficiency, accuracy, and user experience for CMAQ instrumented model extensions like CMAQ-DDM and CMAQ-ISAM
* Expansion of emissions diagnostic output features
* Introduction of a domain-wide Budget calculation tool 
* Online integration of common pollutant post-processing tasks (i.e. output total PM2.5 mass and more directly!)
* Community Contribution: Incorporation of the Two-Dimensional Volatility Bases Set (2D-VBS) chemical mechanism

## Important update for WRF-CMAQ users
A bug was identified within the CMAQ to WRF coupling routine (twoway_feedback.F90) where aerosol feedback information is transferred from CMAQ to WRF. In doing so, it was found that WRF was not receiving the correct aerosol feedback information due to a looping error relating to the number of layers set to 1 in some cases. The bug impacts the WRF-CMAQ coupled system in the CMAQv5.3 release series (v5.3, v5.3.1, v5.3.2, v5.3.3) when running with short wave radiative feedback. The bug was not present in prior WRF-CMAQ versions. The bugfix in CMAQv5.4 now correctly captures the variations in the aerosol optical properties and consequently the direct feedback effects through all layers.  **Users of WRF-CMAQ are strongly encouraged to update to CMAQv5.4.** 

## Getting the CMAQ Repository
This CMAQ Git archive is organized with each official public release stored as a branch on the main USEPA/CMAQ repository. The most recently released version of the the model will always be on the branch called 'main'. To clone code from the CMAQ Git archive, specify the branch (i.e. version number) and issue the following command from within
a working directory on your server:

```
git clone -b main https://github.com/USEPA/CMAQ.git CMAQ_REPO
```

## CMAQ Repository Guide
Source code and scripts are organized as follows:
* **CCTM (CMAQ Chemical Transport Model):** code and scripts for running the 3D-CTM at the heart of CMAQ.
* **DOCS:** CMAQ User's Guide, developers guidance, and short tutorials.
* **PREP:** Data preprocessing tools for important input files like initial and boundary conditions, meteorology, etc.
* **POST:** Data postprocessing tools for aggregating and evaluating CMAQ output products (e.g. Combine, Site-Compare, etc)
* **UTIL:** Utilities for generating code and using CMAQ (e.g. chemical mechanism generation)

## Documentation
Code documentation is included within this repository (they are version-controlled along with the code itself).  

* [CMAQ User's Guide](DOCS/Users_Guide/README.md)   
* [CMAQv5.4 Release Notes](https://github.com/USEPA/CMAQ/wiki)   
* [Tutorials](DOCS/Users_Guide/Tutorials/README.md)   
* [Developers' Guide](DOCS/Developers_Guide/CMAQ_Dev_Guide.md)   
* [FAQ for upgrading to the latest CMAQ version](DOCS/Release_Notes/CMAQ_FAQ.md) 

## CMAQ Test Cases   
Benchmark/tutorial data for the CMAQv5.4 release are available from the CMAS Data Warehouse.  The input and output files are stored on Google Drive and an annoymous FTP server.  CMAQv5.4 comes with new input and output benchmark data for July 1-2, 2018 over the Northeast US (links provided below). Tutorials are provided for using the benchmark data to test running of the base [CMAQ model](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_benchmark.md), [WRF-CMAQ](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_WRF-CMAQ_Benchmark.md), [CMAQ-ISAM](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_ISAM.md), and [CMAQ-DDM-3D](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_DDM.md).  The input datasets include a grid mask file for the United States (GRIDMASK_STATES_12SE1.nc). The grid mask file is used for running the new ISAM and DDM-3D test cases, or to test out regional emissions scaling with [DESID](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_emissions.md).  The input datasets also include ocean files with new variables needed to use the cb6r5_ae7 and cb6r5m_ae7 mechanisms.  See the [Ocean File tutorial](DOCS/Users_Guide/Tutorials/CMAQ_UG_tutorial_oceanfile.md) for more information on changes to the ocean file in v5.4.  

|**CMAQ Version**|**Data Type**|**Domain**|**Simulation Dates**|**Data Access**| 
|:----:|:----:|:--------------:|:----:|:--------:|
|v5.4|Input and Output| Northeast US| July 1 - 2, 2018|[Google Drive Link](https://drive.google.com/drive/folders/1AFUB-4kzIXXoZr4hOHNBqRvy9JQ9_MDp)  <br /> [FTP Link](https://gaftp.epa.gov/exposure/CMAQ/V5_3_3/)  |

 
## User Support
* [Frequent CMAQ Questions](https://www.epa.gov/cmaq/frequent-cmaq-questions) are available on our website. 
* [The CMAS User Forum](https://forum.cmascenter.org/) is available for users and developers to discuss issues related to using the CMAQ system.
 [**Please read and follow these steps**](https://forum.cmascenter.org/t/please-read-before-posting/1321) prior to submitting new questions to the User Forum.

## EPA Disclaimer
The United States Environmental Protection Agency (EPA) GitHub project code is provided on an "as is" basis and the user assumes responsibility for its use. EPA has relinquished control of the information and no longer has responsibility to protect the integrity, confidentiality, or availability of the information. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by EPA. The EPA seal and logo shall not be used in any manner to imply endorsement of any commercial product or activity by EPA or the United States Government.

* [Open source license](license.md)
