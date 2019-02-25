.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _prepare_data:
 
==========================================
prepare_data
==========================================
 
.. toctree::
   :maxdepth: 1
 
Prepare the data for calibration and imaging.



-------------------------------------
**enable**
-------------------------------------

  *bool*, *optional*

  Executes the data preparation step.



-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Order in queue of workers.



-------------------------------------
**fixvis**
-------------------------------------

  Fixes the UVW coordinates through the CASA task fixvis.

    **enable**
      *bool*, *optional*

      Enable execution of fixvis.



-------------------------------------
**prepms**
-------------------------------------

  Add BITFLAG column to MS.

    **enable**
      *bool*, *optional*

      Enable addition of BITFLAG column to MS.



-------------------------------------
**add_spectral_weights**
-------------------------------------

  Add spectral weights column to the measurement set.

    **enable**
      *bool*, *optional*

      Enables addition of spectral weights column to the measurement set.

