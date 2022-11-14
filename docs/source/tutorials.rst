=========
Tutorials
=========

This is a guide you can follow to start a basic pulsar analysis with TempoNest2. If you want more details on the functions below, see :ref:`API references`. More detailed examples can be found in the Examples provided in the original `github repository <https://github.com/LindleyLentati/TempoNest2/tree/master/GHS>`_.

Initialization
==============
To perform the analysis, you will need the pulsar observations, a .tim file and a .par file. You will need to instanciate a Likelihood object for each analysis. The parameter *useGPU* allows you to choose to perform the sampling on GPU or CPU (default is False).


.. code-block:: python

   import TempoNest as tn
   #For CPU-uses
   lfunc = tn.Lilekihood(useGPU=False)

   #For GPU-uses
   lfunc = tn.Lilekihood(useGPU=True)

   #Load the data
   lfunc.loadPulsar("parfile.par", "timfile.tim", root='./results/-', iters=1)


Scrunch and get initial profile model
=====================================

To scrunch fully in time, you can use the function **TScrunch**, and indicates the frequency resolution you want to keep for the analysis. The **getInitialParams** function will fit the pulse phase, the width and the shapelets needed to modelize the pulse.

.. code-block:: python

    lfunc.TScrunch(doplot = False, channels = 1, FromPickle = False, FromTM = True)
    lfunc.getInitialParams(pmin = [-0.5, -2, 0], pmax = [0.5, -1, 2], MaxCoeff = 100, resume=True, outDir = './Init/', sampler='multinest', incScattering = False, mn_live = 1000,  fitNComps = 1, doplot = False)


Precompute the shapelet interpolation matrix
============================================

To reduce the computing time, TempoNest2 interpolates the shapelet profiles (see `L. Lentati, 2016 <https://arxiv.org/abs/1612.05258>`_). These shapelet profiles will then be fitted during the sampling by adjusting the model parameters.

.. code-block:: python

   lfunc.PreComputeFFTShapelets(interpTime = 2, MeanBeta = lfunc.MeanBeta, doplot=False)


Set up the model
================

You need to add parameters to the model before the sampling. The example below includes adding the profile noises, the profile amplitudes, the phase, the timing parameters and the profiles. If you do not add these parameters to the model, they will not be fitted during the sampling and may lead to a bad performance.

.. code-block:: python

   #Add some parameters to the model
   lfunc.addPNoise(Fit = True, write=True)
   lfunc.addPAmps(Fit = True, Dense=False, write=True)
   lfunc.addPhase(Fit = True, ML=np.array([0]))
   lfunc.addLinearTM(Fit = True)
   lfunc.addProfile(Fit = True, ML = lfunc.MLShapeCoeff[1:,0].flatten())



