Welcome to the very first Manual for the **wave function propagtaion** module
=============================================================================

| This manual will describe the methodology a user should apply
| when using this module. Only then he/she can benefit the best
| from what this module can do.

Brief introduction to the module structure
------------------------------------------

| The module contains several sub-modules, each one of them
| has different functionality that contributes to the upper goal
| which is the wave-function propagation.

Here is a short list of module’s sub-modules:

   1. Stage_1.py
   2. Stage_2.py
   3. Locpot_class.py
   4. Help_function_library_yair.py
   5. Structure_vis.py
   6. Main_execution.py

**In the following sections, each one of the sub-modules will be described
with more details about its capabilities and its role in the bigger
work-flow of the wave-function propagation module**

--------------

Stage_1
~~~~~~~

| *Stage_1* sub-module was built mainly for performing grid-density
  convergence
| and for calculating and determining the initial parameters of the
  initial wave-function
| of an electron occupying the bottom of the conduction band. In this
  part, we have to supply the algorithm with the initial total energy of
  the electron :math:`E_0` in units of *Joule*.

The user also has to supply the *standard deviation*,
:math:`\sigma` , of the *gaussian* wave-function. The electron
initial wave-function is of the form of *gaussians* wave-packet that
centered at :math:`z_0`. This is the initial position where the most
likelihood to find the electron at the initial conditions.

| The beginning of operating the complete **wave-function propagation**
  the module will always be with extracting the relevant parameters of the
  initial wave-function.
| If the *grid-density convergence-test* was also required to be taken
  by the user, it would be performed at that point, at the **Stage_1**
  sub-module calling.

To sum up this section:
^^^^^^^^^^^^^^^^^^^^^^^

   | **Stage_1**: 
     The importance of extracting the necessary
     parameters for the electron wave-function such as:  :math:`E_0`,
     *grid-density*, :math:`\sigma`.
   | These parameters will be given as input for the next step of
     the algorithm with no dependence whether the grid-density
     convergence test was held or not. 
     Performing the Convergence
     test for the grid density. Usually, it will be preferable to
     converge the simplest system we have. Namely, if we can apply the
     convergence test to one of the bulk-material systems, it will end
     with a cheaper computational cost. 
     -- All kinds of systems should be
     undergone a grid-density convergence test: an interface system,
     slabs (with or without a vacuum), and continuous bulk materials. 
     -- None of the changes that will be performed at this level will
     affect the next steps in the algorithm. It just passes the crucial
     parameters for the next steps.

--------------

Stage_2
~~~~~~~

| *Stage_2* sub-module may be considered the core and the most
  essential part of the entire project. It holds all the practice and logic
  of the propagation procedure.
| At this level, all the user’s decisions regarding his system have to
  be accounted for. The user has to tell the program what kind of system
  he has or where the position it should refer to as a reference point
  for many types of calculations.
| In *Stage_2*, the user also defines all the operations he would like to
  perform. Whether to extend the Locpot vector and in what way to do
  so. In addition, there are several functions included in this
  sub-module that aim to calculate the necessary quantities and properties
  of the system: cumulative probability through the reference point and
  even transmission coefficient at that point.
| Eventually, this sub-module proposes other two convergence tests that
  are:

.. container::

   **System size**

It stands for achieving the converged system’s length in which the
transmission coefficient difference between two consecutive iterations
does not surpass 0.01. In addition, it demands energy conservation, thus
two successive iterations yield initial total energies that do not
deviate in more than 0.01 eV.

.. container::

   **Time step convergence test**

| It stands for achieving the converged time step, dt. It should be a
  trade-off between accuracy, animation time length, and computer
  resource cost. For accuracy, we would like it to be the smallest
  as far as it can be. However, for too small a time step, the animation
  of the simulation would not display any change since each frame
  represents negligible changes that cannot be observed. In addition,
  too small dt’s would end up with an enormous amount of frames and memory
  for storage.
| The importance reflected in the written above should be taken into
  consideration by the user. This convergence test module is not
  completed perfectly. Each user has different motives and standards, and
  reaching convergence can be defined in various ways. Therefore, **The
  user should examine the final dt resulting from this sub-module
  function and decide if it satisfies his/her demands**

Some more capabilities of **Stage_2**:

   **Stage_2**: 
   > - It enables the elongation of the local potential vector of
   any form of system. 
   > - It allows to apply of all the parameters
   describing the *wave-function* that are found in **Stage_1** in the new
   local potential interface system. 
   > - It allows to propagate the
   wave-function in time across our system by applying the **split-step**
   method. 
   > - It offers the option of creating the simulation animation.
   > - It can calculate the cumulative probability through the interface
   position or any other specified reference position. 
   > - System size
   and time step convergence tests.

Using the Gui for executing some operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**First, what it requires to be installed to use:** 
> - python
3.7 and above 
> - installed packages and modules: 
  >> - Anaconda
environment 
  >> - Pymatgen 
  >> - PySimpleGUI

**How it looks like** :


.. image:: https://user-images.githubusercontent.com/89647386/167392844-0ce0c6de-7b1e-4a62-b14f-297ef7e56dcf.png

  

**Work-flow**: > - Loading the locpot file. If you have an interface,
you can load the bulk-materials locpots too. 
> - Define your system. Do
you have an interface? Do you refer to a specific range within your local
potential (in cases of vacuum or any slabs form). Pay attention that
choosing this will result in popping up another window to supply the
range. (It will pop-up after submitting the entire form). 
> - The next
step is choosing whether or not to perform any type of convergence test.
Please notice that if you decide not to perform any convergence test,
you will be asked to provide the initial conditions manually after
submitting the entire form. 
> - Providing initial parameters for
initializing the wave function. 
> - Choosing the central axis that all the
calculations will be referenced. The default is *z*. 
> - Last but not
least, you can choose what operations you would like to do.

+----------------------------------------------------------------------+
| > **NOTE:** Do not try to test all the combinations of all           |
| possibilities, it will fail. It is designed to perform only the           |
| reasonable paths, and it has not had a self-failure proof.         |
+----------------------------------------------------------------------+

.. image:: https://user-images.githubusercontent.com/89647386/167392844-0ce0c6de-7b1e-4a62-b14f-297ef7e56dcf.png
