.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _observation_config:
 
==========================================
observation_config
==========================================
 
.. toctree::
   :maxdepth: 1
 
Setup some basic observation information



.. _observation_config_order:

-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Order in queue of workers



.. _observation_config_obsinfo:

-------------------------------------
**obsinfo**
-------------------------------------

  Get observation information

  **enable**

    *bool*, *optional*

    Execute this section

  **listobs**

    *bool*, *optional*

    Run CASA listobs task to get observation information

  **summary_json**

    *bool*, *optional*

    Run MSUtils summary function to get observation information as JSON file which can be used to automatically configure pipeline

  **vampirisms**

    *bool*, *optional*

    Returns sun free time range



.. _observation_config_Check_Cals:

-------------------------------------
**Check_Cals**
-------------------------------------

  *bool*, *optional*

  Should the existence of the  calibrators be checked for or only the target. Setting this to false allows the pipeline to run on split datasets. Default True



.. _observation_config_target:

-------------------------------------
**target**
-------------------------------------

  *str*, *optional*

  Target field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



.. _observation_config_gcal:

-------------------------------------
**gcal**
-------------------------------------

  *str*, *optional*

  Gain calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



.. _observation_config_bpcal:

-------------------------------------
**bpcal**
-------------------------------------

  *str*, *optional*

  Bandpass calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



.. _observation_config_fcal:

-------------------------------------
**fcal**
-------------------------------------

  *str*, *optional*

  Fluxscale calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



.. _observation_config_xcal:

-------------------------------------
**xcal**
-------------------------------------

  *str*, *optional*

  Crosshand phase angle calibrator. This calibrator must be linearly polarized and have a non-zero parallactic angle coverage at the time of observation to solve for the X-Y offsets in digitizers and the absolute polarization angle of the system. Successful calibration derotates U from V.



.. _observation_config_reference_antenna:

-------------------------------------
**reference_antenna**
-------------------------------------

  *str*, *optional*

  Reference antenna. If 'auto' then MeerKATHI will automatically pick the reference antenna from the .JSON metadata file if available. The file name is the same as the input .MS file but with .JSON extension. This file is typically available only for old (ROACH2) MeerKAT data. For all other data the pipeline will likely throw an error and gracefully terminate. In that case the reference antenna should be set manually.



.. _observation_config_primary_beam:

-------------------------------------
**primary_beam**
-------------------------------------

  Generate primary beam model

  **enable**

    *bool*, *optional*

    Execute this section

  **freq**

    *str*, *optional*

    A single freq, or the start, end freqs, and channel width in MHz

  **diameter**

    *float*, *optional*

    Diameter of the required beam

  **pixels**

    *int*, *optional*

    Number of pixels on one side

  **coefficients_file**

    *str*, *optional*

    Coeficients file name

