.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _inspect_data:
 
==========================================
inspect_data
==========================================
 
.. toctree::
   :maxdepth: 1
 
Dignostic plots of the first-pass cross-calibrated data.



.. _inspect_data_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Executes dignostic plotting of the first-pass cross-calibrated data.



.. _inspect_data_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Label for output products (plots etc.) for this step.



.. _inspect_data_correlation:

--------------------------------------------------
**correlation**
--------------------------------------------------

  *str*, *optional*, *default = XX, YY*

  Label specifying the correlations.



.. _inspect_data_uvrange:

--------------------------------------------------
**uvrange**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Set the U-V range for data selection, e.g. '>50'.



.. _inspect_data_fields:

--------------------------------------------------
**fields**
--------------------------------------------------

  *list* *of str*, *optional*, *default = pbcal, gcal*

  Fields to plot. Specify by field id, index or keys like, gcal, bpcal.



.. _inspect_data_real_imag:

--------------------------------------------------
**real_imag**
--------------------------------------------------

  Plot real vs imaginary parts of data.

  **enable**

    *bool*, *optional*, *default = True*

    Executed the real v/s imaginary data plotting.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like, gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.



.. _inspect_data_amp_phase:

--------------------------------------------------
**amp_phase**
--------------------------------------------------

  Plot Amplitude vs Phase for  data.

  **enable**

    *bool*, *optional*, *default = True*

    Executes the plotting of amplitude v/s phase for data.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.



.. _inspect_data_amp_uvwave:

--------------------------------------------------
**amp_uvwave**
--------------------------------------------------

  Plot data amplitude v/s  uvwave.

  **enable**

    *bool*, *optional*, *default = True*

    Executes plotting data amplitude as a function of uvwave.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.



.. _inspect_data_amp_ant:

--------------------------------------------------
**amp_ant**
--------------------------------------------------

  Plot data amplitde v/s antenna.

  **enable**

    *bool*, *optional*, *default = True*

    Executes plotting data amplitude v/s antennas.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.



.. _inspect_data_phase_uvwave:

--------------------------------------------------
**phase_uvwave**
--------------------------------------------------

  Plot data phase v/s uvwave.

  **enable**

    *bool*, *optional*, *default = True*

    Executes plotting data phase v/s uvwave.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.



.. _inspect_data_amp_scan:

--------------------------------------------------
**amp_scan**
--------------------------------------------------

  Plot data amplitude v/s scan number.

  **enable**

    *bool*, *optional*, *default = True*

    Executes plotting data amplitude v/s scan number.

  **fields**

    *list* *of str*, *optional*, *default = ' '*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*, *default = corrected*

    Data column to plot.

  **avgtime**

    *str*, *optional*, *default = 10*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*, *default = 10*

    Number of channels to average for plotting.

