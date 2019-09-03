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

  *bool*

  Executes the data preparation step.



.. _prepare_data_fixvis:

--------------------------------------------------
**fixvis**
--------------------------------------------------

  Fixes the UVW coordinates through the CASA task fixvis.

  **enable**

    *bool*, *optional*, *default = False*

    Enable execution of fixvis.



.. _prepare_data_manage_flags:

--------------------------------------------------
**manage_flags**
--------------------------------------------------

  Manage MS flags

  **enable**

    *bool*, *optional*, *default = true*

    enable this section

  **add_bitflag_column**

    *bool*, *optional*, *default = true*

    Add BITFLAG and BITFLAG_ROW columns

  **init_legacy_flagset**

    *bool*, *optional*, *default = true*

    Save all current flags in a legacy flagset if it does not exist

  **remove_flagsets**

    *bool*, *optional*, *default = true*

    Remove all existing flagsets, except legacy flags



.. _prepare_data_add_spectral_weights:

--------------------------------------------------
**add_spectral_weights**
--------------------------------------------------

  Add spectral weights column to the measurement set.

  **enable**

    *bool*, *optional*, *default = false*

    Enables addition of spectral weights column to the measurement set.

  **weight_columns**

    *list* *of str*, *optional*, *default = WEIGHT, WEIGHT_SPECTRUM*

    column names

  **noise_columns**

    *list* *of str*, *optional*, *default = SIGMA, SIGMA_SPECTRUM*

    column names for noise

  **write_to_ms**

    *bool*, *optional*, *default = true*

    write columns to file

  **stats_data**

    *str*, *optional*, *default = use_package_meerkat_spec*

    which statistics for the file.

