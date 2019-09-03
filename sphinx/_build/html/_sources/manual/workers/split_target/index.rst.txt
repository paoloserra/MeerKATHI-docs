.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _split_target:
 
==========================================
split_target
==========================================
 
.. toctree::
   :maxdepth: 1
 
Split and average target data



.. _split_target_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*, *optional*

  Execute this worker



.. _split_target_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*, *optional*

  Label of the input dataset



.. _split_target_label_out:

--------------------------------------------------
**label_out**
--------------------------------------------------

  *str*, *optional*

  Label of the output dataset



.. _split_target_split_target:

--------------------------------------------------
**split_target**
--------------------------------------------------

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

    Column to split, default is 'data'. Which means use otf calibration.

  **correlation**

    *str*, *optional*

    Select correlations

  **spw**

    *str*, *optional*

    Select spectral windows and channels

  **otfcal**

    Apply OTF calibration

    **enable**

      *bool*, *optional*

      Execute this section

    **callabel**

      *str*, *optional*

      Label of calibration tables to be used

    **apply_delay_cal**

      Apply the delay correction calibration table to specified fields via the CASA applycal task.

    **apply_bp_cal**

      Apply the bandpass table to specified fields via the CASA applycal task.

    **apply_gain_cal_gain**

      Apply the gain calibration table to specified fields via the CASA applycal task.

    **apply_transfer_fluxscale**

      Apply the fluxscale table to specified fields via the CASA applycal task.



.. _split_target_changecentre:

--------------------------------------------------
**changecentre**
--------------------------------------------------

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



.. _split_target_obsinfo:

--------------------------------------------------
**obsinfo**
--------------------------------------------------

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



.. _split_target_init_legacy_flagset:

--------------------------------------------------
**init_legacy_flagset**
--------------------------------------------------

  Save existing flags to legacy flagset

  **enable**

    *bool*, *optional*

    Run this section

