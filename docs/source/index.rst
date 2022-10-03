****
TempoNest 2
****


Profile domain pulsar timing analysis (see `Lentati et al., 2017 <https://ui.adsabs.harvard.edu/abs/2017MNRAS.466.3706L/abstract>`_).
Python2 based replacement for TempoNest, GPU accelerated (CPU implemented).

Requirements
####
You will need the following libraries installed :

- PSRCHIVE (see the `Installation guide <https://psrchive.sourceforge.net/download.shtml>`_)
- PTMCMCSampler (see the `github repository <https://github.com/jellis18/PTMCMCSampler>`_)
- Libstempo (see the `github repository <https://github.com/vallis/libstempo>`_)

Installation 
####

You will need to install **Ellipsis**. Instructions for compiling **Ellipsis** can be found in GHS/Ellipsis/README.md. This results in a libellipsis.a file.  You then need to create a shared object (.so) file from this file by running:

.. code-block:: console
   $ gcc -shared -o libghs.so libellipsis.a -Wl 

The location of libghs.so then needs to be added to your LD_LIBRARY_PATH in order for python to find it by :

.. code-block:: console
   echo LD_LIBRARY_PATH=$LIBRARY_PATH:/path_to_libghs.so/

TempoNest 2 can then be installed by running:

.. code-block:: console
   python setup.py install

Using
####
See the online documentation for :

- Tutorials
- API reference

Examples
####

The Example directories include ipython notebooks with several different models. 

