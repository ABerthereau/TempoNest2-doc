.. TempoNest2 documentation master file, created by
   sphinx-quickstart on Fri Oct  7 12:48:32 2022.
   contain the root `toctree` directive.

Welcome to TempoNest2's documentation!
======================================

   
The profile domain pulsar timing analysis method (see `Lentati et al., 2017 <https://ui.adsabs.harvard.edu/abs/2017MNRAS.466.3706L/abstract>`_).
Python2 based replacement for TempoNest, GPU accelerated (CPU implemented). 

The TempoNest2 method fully modelizes the impulsion by using shapelet profiles before sampling the likelihood in the parameters space. By modeling the impulsion, the method can include profile variations from scattering or jitter. The sampling is performed by an Hamiltonian Monte-Carlo method and can be used either on GPU or CPU. 

Examples 

   The `Example directories <https://github.com/LindleyLentati/TempoNest2/tree/master/GHS>`_ include ipython notebooks with two analysis, including the TOAs, the parfile and the observations. 



.. toctree::
   :maxdepth: 2
   :caption: Sections:
   
   start
   TempoNest2
   tutorials
   


