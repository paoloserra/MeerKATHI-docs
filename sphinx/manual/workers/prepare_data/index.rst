.. meerkathi documentation master file, created by
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



.. _prepare_data_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*, *optional*

  Executes the data preparation step.



.. _prepare_data_fixvis:

--------------------------------------------------
**fixvis**
--------------------------------------------------

  Fixes the UVW coordinates through the CASA task fixvis.

  **enable**

    *bool*, *optional*

    Enable execution of fixvis.



.. _prepare_data_manage_flags:

--------------------------------------------------
**manage_flags**
--------------------------------------------------

  Manage MS flags

  **enable**

    *bool*, *optional*

    enable this section

  **add_bitflag_column**

    *bool*, *optional*

    Add BITFLAG and BITFLAG_ROW columns

  **init_legacy_flagset**

    *bool*, *optional*

    Save all current flags in a legacy flagset if it does not exist

  **remove_flagsets**

    *bool*, *optional*

    Remove all existing flagsets, except legacy flags



.. _prepare_data_add_spectral_weights:

--------------------------------------------------
**add_spectral_weights**
--------------------------------------------------

  Add spectral weights column to the measurement set.

  **enable**

    *bool*, *optional*

    Enables addition of spectral weights column to the measurement set.

  **weight_columns**

    *list* *of str*, *optional*

    column names

  **noise_columns**

    *list* *of str*, *optional*

    column names for noise

  **write_to_ms**

    *bool*, *optional*

    write columns to file

  **stats_data**

    *str*, *optional*

    which statistics for the file.

