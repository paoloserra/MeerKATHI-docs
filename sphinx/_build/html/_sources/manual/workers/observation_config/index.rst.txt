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



.. _observation_config_obsinfo:

--------------------------------------------------
**obsinfo**
--------------------------------------------------

  Get observation information

  **enable**

    *bool*

    Execute this section

  **listobs**

    *bool*, *optional*, *default = True*

    Run CASA listobs task to get observation information

  **summary_json**

    *bool*, *optional*, *default = True*

    Run MSUtils summary function to get observation information as JSON file which can be used to automatically configure pipeline

  **vampirisms**

    *bool*, *optional*, *default = False*

    Returns sun free time range

  **plot_elevation_tracks**

    *bool*, *optional*, *default = False*

    Make Elevation vs Hour angle plots for observed fields

  **plotter**

    *{"plotms", "owlcat"}*, *optional*, *default = owlcat*

    Application to use for making plots



.. _observation_config_target:

--------------------------------------------------
**target**
--------------------------------------------------

  *list* *of str*, *optional*, *default = all*

  Field name of target field. Or 'all' for all the target fields.



.. _observation_config_gcal:

--------------------------------------------------
**gcal**
--------------------------------------------------

  *list* *of str*, *optional*, *default = all*

  Field name of gain (amplitude/phase) calibrator field. Or set as 'all' for all the gcal fields, 'longest' to setlect the gcal field observed for the longest time, 'nearest' to select the gcal field closest to the target. Note that if multiple targets and gcals are present, then 'all' (for both) means each target will be paired with the closest gcal.



.. _observation_config_bpcal:

--------------------------------------------------
**bpcal**
--------------------------------------------------

  *list* *of str*, *optional*, *default = longest*

  Field name of bandpass calibrator field. Or set as 'all' for all the bpcal fields, 'longest' to setlect the bpcal field observed for the longest time, 'nearest' to select the bpcal field closest to the target.



.. _observation_config_fcal:

--------------------------------------------------
**fcal**
--------------------------------------------------

  *list* *of str*, *optional*, *default = longest*

  Field name of fluxscale calibrator field. Or set as 'all' for all the fcal fields, 'longest' to setlect the fcal field observed for the longest time, 'nearest' to select the fcal field closest   to the target.



.. _observation_config_xcal:

--------------------------------------------------
**xcal**
--------------------------------------------------

  *list* *of str*, *optional*, *default = longest*

  Crosshand phase angle calibrator. This calibrator must be linearly polarized and have a non-zero parallactic angle coverage at the time of observation to solve for the X-Y offsets in digitizers and the absolute polarization angle of the system. Successful calibration derotates U from V.



.. _observation_config_reference_antenna:

--------------------------------------------------
**reference_antenna**
--------------------------------------------------

  *str*

  Reference antenna.

