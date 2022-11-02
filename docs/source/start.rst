===========
Quick start
===========

Requirements
============
You will need the following libraries installed :

- PSRCHIVE (see the `Installation guide <https://psrchive.sourceforge.net/download.shtml>`_)
- PTMCMCSampler (see the `github repository <https://github.com/jellis18/PTMCMCSampler>`_)
- Libstempo (see the `repository <https://github.com/vallis/libstempo>`_)

Installation 
============

You will need to install **Ellipsis**. Instructions for compiling **Ellipsis** can be found in GHS/Ellipsis/README.md. This results in a libellipsis.a file.  You then need to create a shared object (.so) file from this file by running:

.. code-block:: bash

  gcc -shared -o libghs.so libellipsis.a -Wl `

The location of libghs.so then needs to be added to your LD_LIBRARY_PATH in order for python to find it by :

.. code-block:: bash

  echo LD_LIBRARY_PATH=$LIBRARY_PATH:/path_to_libghs.so/

TempoNest 2 can then be installed by running:

.. code-block:: bash

  python setup.py install





