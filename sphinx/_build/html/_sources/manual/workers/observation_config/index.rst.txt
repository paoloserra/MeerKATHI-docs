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



-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Order in queue of workers



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



-------------------------------------
**target**
-------------------------------------

  *str*, *optional*

  Target field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



-------------------------------------
**gcal**
-------------------------------------

  *str*, *optional*

  Gain calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



-------------------------------------
**bpcal**
-------------------------------------

  *str*, *optional*

  Bandpass calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



-------------------------------------
**fcal**
-------------------------------------

  *str*, *optional*

  Fluxscale calibrator field. If set to 'auto' then will automatically set using JSON file from 'obsinfo'



-------------------------------------
**reference_antenna**
-------------------------------------

  *str*, *optional*

  Reference antenna. If set to 'auto' then will automatically set using metadata file (only for meerkat data)



-------------------------------------
**nchans**
-------------------------------------

  *int*, *optional*

  Number of channels. If set to 0 then will automatically set using metadata file (only for meerkat data)



-------------------------------------
**firstchanfreq**
-------------------------------------

  *str*, *optional*

  First frequency channel. If set to 0 then will automatically set using metadata file (only for meerkat data)



-------------------------------------
**lastchanfreq**
-------------------------------------

  *str*, *optional*

  Last frequency. If set to 0 then will automatically set using metadata file (only for meerkat data)



-------------------------------------
**chanwidth**
-------------------------------------

  *str*, *optional*

  Channel width. If set to 0 then will automatically set using metadata file (only for meerkat data)



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

