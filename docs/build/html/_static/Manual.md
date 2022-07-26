# Welcome to the very first Manual for the ***wave function propagtaion*** module

This manual will decribe the methodology a user should apply  
when using this module. Only then he/she can benefit the best  
from what this module can do.

## Brief introduction to the module structure

The module contains several sub-modules that each one of them  
has a different functionallity that contibutes to the upper goal  
which is the wave-function propagation.  
  
Here is a short list for module's sub-modules:  

> 1. Stage_1.py
> 2. Stage_2.py
> 3. Locpot_class.py
> 4. Help_function_library_yair.py
> 5. Structure_vis.py
> 6. Main_execution.py
  
**In the next sections, each one of the sub-modules will be described  
with more details about its capalities, and about its role in the bigger
work-flow of the wave-function propagation module**
  
-------


### Stage_1

*Stage_1* sub-module was built mainly for performing grid-density convergence  
and for calculating and determing the initial parameters of the initial wave-function  
of an electron occupying the bottom of the conduction band.
In this part, we have to supply the algorithm with the initial total energy of the electron ***$E_0$***  in units of *Joule*.
     
The user also have to supply the *standard deviation*, ***$\sigma$*** , of the *gaussian* wave-function. The electron initial wave-function is of the form of *gaussians* wave-packets that centered at $z_0$. This is the initial position where the most likelyhood to find the electorn at the initial conditions.   
   
The beginning of oprerating the complete ***wave-function propagation*** module, will always be with extracting the relevant parameters of the initial wave-function.   
If the *grid-density convergence-test* was also required to be taken by the user, it would be performed at that point, at the ***Stage_1*** sub-module calling.
   
#### To sum up this section:

> ***Stage_1***:
>> - The importance of extracting the necessary parameters for the electron wave-function such as: ***$E_0$***, *grid-density*, ***$\sigma$***.  
>> These parameters will be given as an input for the next step of the algorithm with no dependence whether the grid-density convergence test was held or not.
>> - Performing the Convergence test for the grid density. Usually it will be preferable to converge the simplest system we have. Namely, if we can apply the convergence test to one of the bulk-material system it will end with cheaper computitional cost.
>> - All kind of systems should be undergone a grid-density convergence test: an interface system, slabs (with or without a vaccuum), and bulk continiuos materials.
>> - None of the changes that will be performed at this level will not affect the next steps in the algorithm. It just passes the crucial parameters for the next steps.   
    
     

----
    
### Stage_2

*Stage_2* sub-module may be considered as the core and the most important part of entire project. It holds all the practice and logics of the propagation procedure.  
At this level, all the user's decisions regarding his system have to be acounted for. The user has to tell the program what kind of system he has, or where is the position it should refer as a reference point for many types of calculations.  
In *Stage_2* the user also defines all the operations he would like to perform. Whether to extend the Locpot vector, and in what way to do so. In addition, there are several functions included in this sub-module that aim to calculate important qunatities and properties of the system: cumulative probabilty through the reference point and even transmission coefficient at that point.  
Eventually, this sub-module propose other two convergence tests that are:   

<div align="center"> ***System size***</div>
    
    
It stands for acheiving the convegred system's length in which the transmission coefficient difference between two consecutive iterations does not surpass 0.01. In addition, it demands energy conservation thus two successive iterations yeild initial total energies that do not deviate in more than 0.01 eV.  
      
      
      
<div align="center">**Time step convergence test**</div>

It stands for acheiving the converged time step, dt. It should be a trade-off between accuracy, animation time length and computer resources cost. For the accuracy we would like it to be the smallest as far as it can be. However, for too small time step, the animation of the simulation would not display any change since each frame represents negligibale changes that cannot be observed. In ddition, too small dt's would end-up with enormous amount of frames and memory for storage.    
The importance the reflected from the written above, should taken into consideration by the user. This convegence test module is not completed perfectly. Each user has different motives and standards and reaching convergence can be defined in vaious ways. Therefore, ***The user should examine the final dt resulted from this sub-moudle function and decide if it satisfies his/her demands*** 

Some more capabilties of **Stage_2**:

> ***Stage_2***:
>> - It enables to elongate to local potential vector of any form of system.
>> - It enables to apply all the parameters describing the *wave-function* that found in ***Stage_1*** in the new local potential interface system.
>> - It allows to propagte the wave-function in time across our system applying the **split-step** method.
>> - It offers the option of creating the simultion animation.
>> - It can calculates the cumulative probabilty through the interface position or any other specified reference position.
>> - System size and time step convergence tests.



### Using the Gui for executing some opertaions
***First what it requires to be installed in order to use:***
> - python 3.7 and above
> - installed packages and modules:
>> - Anaconda environment 
>> - Pymatgen
>> - PySimpleGUI 



**How it looks like** :   
      

![image](https://user-images.githubusercontent.com/89647386/167392844-0ce0c6de-7b1e-4a62-b14f-297ef7e56dcf.png)
     

**Work-flow**:
> -  Loading the locpot file. If you have an interface, you can load the bulk-materials locpots too.
> - Define your system. Do you have an interface? Do you refer to a certain range within your local potential (in cases of vaccum or any slabs form). Pay attention that chossing this will result in popping up another window to supply the range. (It will pop-up after submiting the entire form).
> - The next step is choosing whether or not to perform any kind of convergence test. Please notice that if you decided not to perform any convergence test you will be asked to provide the initial conditions manually after submitting the entire form.
> - Providing initial paramters for initializing the wave-function.
> - Choosing the main axis that all the calculations will be referenced at. The default is *z*.
> - Last but not least, you can choose what operations you would like to do. 
![image](https://user-images.githubusercontent.com/89647386/167394929-f089c2b1-9529-4564-b9d1-ed2cc067721c.png)

    

---    
> **_NOTE:_** Do not try to test all the combinations of all possibilites, it will fail. It desined to perform only the reasonable paths, and it has not have a self-failiure proof.
---










