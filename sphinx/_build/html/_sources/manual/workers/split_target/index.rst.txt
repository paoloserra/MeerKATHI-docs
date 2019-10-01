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

  *bool*

  Execute this worker



.. _split_target_label_in:

--------------------------------------------------
**label_in**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Label of the input dataset



.. _split_target_label_out:

--------------------------------------------------
**label_out**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of the output dataset



.. _split_target_split_target:

--------------------------------------------------
**split_target**
--------------------------------------------------

  Split data

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **time_average**

    *str*, *optional*, *default = ' '*

    Time averaging

  **freq_average**

    *int*, *optional*, *default = 1*

    Frequency averaging

  **column**

    *str*, *optional*, *default = corrected*

    Column to split, default is 'data'. Which means use otf calibration.

  **correlation**

    *str*, *optional*, *default = ' '*

    Select correlations

  **spw**

    *str*, *optional*, *default = ' '*

    Select spectral windows and channels

  **otfcal**

    Apply OTF calibration

    **enable**

      *bool*, *optional*, *default = True*

      Execute this section

    **callabel**

      *str*, *optional*, *default = 1gc1*

      Label of calibration tables to be used

    **apply_delay_cal**

      Apply the delay correction calibration table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of delay correction calibration table.

      **field**

        *list* *of str*

        Field to select in the delay correction calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

    **apply_bp_cal**

      Apply the bandpass table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of bandpass table.

      **field**

        *list* *of str*

        Field to select in the bandpass table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

    **apply_gain_cal_gain**

      Apply the gain calibration table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = False*

        Executes application of gain calibration table.

      **field**

        *list* *of str*

        Field to select in the gain calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.

    **apply_transfer_fluxscale**

      Apply the fluxscale table to specified fields via the CASA applycal task.

      **enable**

        *bool*, *optional*, *default = True*

        Executes application of fluxscale table.

      **field**

        *list* *of str*, *optional*, *default = gcal*

        Field to select in the fluxscale table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.



.. _split_target_changecentre:

--------------------------------------------------
**changecentre**
--------------------------------------------------

  changes the phase centre

  **enable**

    *bool*, *optional*, *default = False*

    Execute this section

  **ra**

    *str*, *optional*, *default = 0h0m0.0s*

    J2000 RA of new phase centre, format XXhXXmXX.XXs, default is empty string

  **dec**

    *str*, *optional*, *default = 0d0m0.0s*

    J2000 Dec of new phase centre, format XXdXXmXX.XXs, default is empty string



.. _split_target_obsinfo:

--------------------------------------------------
**obsinfo**
--------------------------------------------------

  Get observation information

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **listobs**

    *bool*, *optional*, *default = True*

    Run CASA listobs

  **summary_json**

    *bool*, *optional*, *default = True*

    Run MSUtils function



.. _split_target_init_legacy_flagset:

--------------------------------------------------
**init_legacy_flagset**
--------------------------------------------------

  Save existing flags to legacy flagset

  **enable**

    *bool*

    Run this section

