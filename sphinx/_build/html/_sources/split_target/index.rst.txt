.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
split_target
==========================================
 
.. toctree::
   :maxdepth: 1
 
Split and average target data



-------------------------------------
**enable**
-------------------------------------
  *bool*, *optional*

  Execute this worker



-------------------------------------
**order**
-------------------------------------
  *int*, *optional*

  Order of worker in queue



-------------------------------------
**label**
-------------------------------------
  *str*, *optional*

  Label for new data set



-------------------------------------
**split_target**
-------------------------------------
  Split data

    **enable**
      *bool*, *optional*
      Execute this section

    **time_average**
      *str*, *optional*
      Time averaging

    **freq_average**
      *int*, *optional*
      Frequency averaging

    **column**
      *str*, *optional*
      Column to split, default is 'corrected'

    **correlation**
      *str*, *optional*
      Select correlations, default is '' = all

    **spw**
      *str*, *optional*
      Select spectral windows and channels, default is '' = all



-------------------------------------
**hires_split**
-------------------------------------
  Splits data while keeping the frequency resolution

    **enable**
      *bool*, *optional*
      Execute this section

    **hires_label**
      *str*, *optional*
      Label for high resolution data set

    **hires_spwid**
      *int*, *optional*
      SPW ID for full resolution data.

    **hires_spw**
      *str*, *optional*
      SPW for full resolution data.



-------------------------------------
**changecentre**
-------------------------------------
  changes the phase centre

    **enable**
      *bool*, *optional*
      Execute this section

    **ra**
      *str*, *optional*
      J2000 RA of new phase centre, format XXhXXmXX.XXs, default is empty string

    **dec**
      *str*, *optional*
      J2000 Dec of new phase centre, format XXdXXmXX.XXs, default is empty string



-------------------------------------
**obsinfo**
-------------------------------------
  Get observation information

    **enable**
      *bool*, *optional*
      Execute this section

    **listobs**
      *bool*, *optional*
      Run CASA listobs

    **summary_json**
      *bool*, *optional*
      Run MSUtils function



-------------------------------------
**prepms**
-------------------------------------
  Run MSUtils prepms function

    **enable**
      *bool*, *optional*
      Run this section

