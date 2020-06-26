﻿# BeSim Toolbox
Matlab toolbox for quick design and simulation of advanced building climate control algorithms.

## Features
- Interface for [linearized white-box building envelope models from Modelica](http://www.ep.liu.se/ecp/article.asp?issue=118&article=005&volume=)
- Automated construction and tuning of model predictive control (MPC) and state estimation algorithms
- Closed-loop simulation, plotting, and performance analysis
- [Approximate MPC via machine learning](https://www.sciencedirect.com/science/article/pii/S0306261918302903) (deep lerarning in particular)
- For quick start and more details check out the presentation about algorithms and tools behind [BeSim](https://www.researchgate.net/publication/328171184_Tools_and_Techniques_for_Advanced_Model_Predictive_Building_Control)

## Installation
### tbxmanager
- Install [tbxmanager](http://www.tbxmanager.com/) 
- Install BeSim via:  `tbxmanager install besim`
- Check for updates:  `tbxmanager update` 
### manual
- clone  BeSim repository 
- save BeSim folder with its subfolders to Matlab path  

## Prerequisities
- Matlab: developed and tested on R2017a and R2017b
- [Yalmip](https://yalmip.github.io/) mathematical modeling and optimization toolbox (BeSim's backbone)
- Optimization solver, e.g. Quadprog or commercial solver such as [Gurobi](http://www.gurobi.com/) (solution of implicit MPC and MHE problems)
- Matlab toolboxes: Deep Learning, Machine learning (approximate MPC functionality)

## Getting Started - Demos
run following scripts in Matlab to get quick results:
- [BeInit.m](https://github.com/drgona/BeSim/blob/master/Be_Run/BeInit.m): design and simulation of optimization-based MPC and state estimator for selected building model
- [BeInitML.m](https://github.com/drgona/BeSim/blob/master/Be_Run/BeInitML.m): design and simulation of approximate MPC via machine learning for selected buiding model

## Structure
**Functional Structure:** Graphical overview of BuiSim structure with data-flow dependencies.
![BuiSim structure](/Data/Page/BeSim_structure2.png)

**Repository Structure:**
List of repository folders with associated functionality.
- [Be_Run](https://github.com/drgona/BeSim/tree/master/Be_Run) (run files and demos)
- [Be_Modeling](https://github.com/drgona/BeSim/tree/master/Be_Modeling) (model loading, discretization, model order reduction)
- [Be_Disturbances](https://github.com/drgona/BeSim/tree/master/Be_Disturbances) (disturbance trajectories loading)
- [Be_References](https://github.com/drgona/BeSim/tree/master/Be_References) (reference trajectories loading)
- [Be_Estimation](https://github.com/drgona/BeSim/tree/master/Be_Estimation) (estimator design)
- [Be_Control](https://github.com/drgona/BeSim/tree/master/Be_Control) (controller design)
- [Be_Simulation](https://github.com/drgona/BeSim/tree/master/Be_Simulation) (main simulation and plotting functions)
- [Be_Learn](https://github.com/drgona/BeSim/tree/master/Be_Learn) (machine learning functions, synthesis of approximate MPC)
- [buildings](https://github.com/drgona/BeSim/tree/master/buildings) (building models files)
- [Data](https://github.com/drgona/BuiSim/tree/master/Data) (stored results)

## Algorithms 
List of key enabling algorithms implemented in BeSim.

**Model Order Reduction**
- [Balanced truncation](https://nl.mathworks.com/help/robust/ref/reduce.html)

**State Estimation**
- Kalman filters (KF)
- Moving horizon estimation (MHE)

**Optimal Control**
- Model predictive control (MPC)
- [Approximate MPC via machine learning](https://www.sciencedirect.com/science/article/pii/S0306261918302903)

**Machine Learning Models**
- Deep learning (DL)
- Regression trees (RT)

## Building Models

**Model Structure**
- [Linearized white-box building envelope models](http://www.ep.liu.se/ecp/article.asp?issue=118&article=005&volume=)
- arbitrary linear time invariant model in state space format

**Available Building Models**

Building type | Location      |  Label        | floor area [m2] | #states         | #outputs       | #inputs         | #disturbances
------------  | ------------- | ------------- | -------------   | -------------  | -------------   | -------------  | ------------- 
Residential   |  Belgium      | 'Old', 'Reno', 'RenoLight' | 56 | 283,286,250    | 6               | 6               | 44
Office        |  Belgium      | 'HollandschHuys' | 3760         | 700            | 12              | 20               | 289
Office        |  Belgium      | 'Infrax'         | 2232         | 1262           | 19              | 28               | 259
Borehole      |  Belgium      | 'Borehole '      | -            | 190            | 1               | 1                   | 0

## Author
Email: jan.drgona@pnnl.gov

[Ján Drgoňa](https://www.linkedin.com/in/drgona/)  
postdoctoral researcher  
Pacific Northwest National Laboratory  
Optimization and Control Group  
Richland, WA, USA  

## Acknowledgement

The first stage of the toolbox emerged from the code development of the author during his PhD study held at [Institute of Information Engineering, Automation, and Mathematics, Slovak University of Technology in Bratislava](https://www.uiam.sk/) under the supervision of [prof. Michal Kvasnica](https://www.uiam.sk/~kvasnica/).

The second stage with detailed white-box building models was developed during the visiting PhD and post-doc position at [Thermal Systems Simulation (The SySi) research group](https://www.mech.kuleuven.be/en/tme/research/thermal_systems), Department of Mechanical Engineering
Division of Applied Mechanics and Energy Conversion (TME), KU Leuven under the supervision of [prof. Lieve Helsen](https://www.kuleuven.be/wieiswie/en/person/00009689).

An early contribution of [Damien Picard](https://www.kuleuven.be/wieiswie/nl/person/00085306) towards the code development and building modeling, conceptual contributions of [Martin Klaučo](https://www.uiam.sk/~klauco/) and [Michal Kvasnica](https://www.uiam.sk/~kvasnica/), and modeling work of [Filip Jorissen](https://www.kuleuven.be/wieiswie/nl/person/00091751) and [Iago Cupeiro Figueroa](https://www.kuleuven.be/wieiswie/en/person/00112721) on Infrax building and borehole models are gratefully acknowledged.

The financial support by the European Union through  the [EU-H2020-GEOTeCH 
project ‘Geothermal Technology for conomic Cooling and Heating’](http://www.geotech-project.eu/) is acknowledged.


Finally, later stages of this work partially emerged from the [IBPSA Project 1](https://ibpsa.github.io/project1/), an international project conducted under the umbrella of the International Building Performance Simulation Association (IBPSA). Project 1 will develop and demonstrate a BIM/GIS and Modelica Framework for building and community energy system design and operation.


<img src="/Data/Page/kuleuven_logo.png" alt="drawing" width="300"/> <img src="/Data/Page/SySi.png" alt="drawing" width="300"/>

![geotech](/Data/Page/GEOTeCH.png)
<img src="/Data/Page/IBPSA-project1.png" alt="drawing" width="500"/>

<img src="/Data/Page/IAM.png" alt="drawing" width="130"/> <img src="/Data/Page/logo_fchpt.png" alt="drawing" width="250"/>

## References

1. Cupeiro Figueroa I., Drgona J., Helsen L., State estimators applied to a linear white-box geothermal borefield controller model, 16th International Building Performance Simulation Association Conference, Rome, Italy, 02 Sep 2019 - 04 Sep 2019. N/A. Proceedings of the 16th IBPSA Conference 2019

2. Cupeiro Figueroa I., Drgona J., Abdollahpouri M., Picard D., and Helsen L., State Observer for Optimal Control using White-box Building Models, Purdue Conferences - 5th International High Performance Building Conference, Purdue University, West Lafayette, IN, USA. INTERNATIONAL HIGH PERFORMANCE BUILDINGS CONFERENCE. Purdue e-Pubs. Jul 2018.

3. Drgona J., Picard D., Kvasnica M., Helsen L. (2018). Approximate model predictive building control via machine learning. APPLIED ENERGY, 218, 199-216. doi: 10.1016/j.apenergy.2018.02.156. 

4. Picard D., Drgoňa J., Kvasnica M., Helsen L. (2017). Impact of the controller model complexity on model predictive control performance for buildings. Energy and Buildings, 152, 739-751. 

