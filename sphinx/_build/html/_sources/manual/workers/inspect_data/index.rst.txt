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

-------------------------------------
**enable**
-------------------------------------

  *bool*, *optional*

  Executes dignostic plotting of the first-pass cross-calibrated data.



.. _inspect_data_order:

-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  The order in which this step will be executed in the pipeline.



.. _inspect_data_label:

-------------------------------------
**label**
-------------------------------------

  *str*, *optional*

  Lable for output products (plots etc.) for this step.



.. _inspect_data_correlation:

-------------------------------------
**correlation**
-------------------------------------

  *str*, *optional*

  Lable specyfying the correlations used XX,YY is default



.. _inspect_data_real_imag:

-------------------------------------
**real_imag**
-------------------------------------

  Plot real vs imaginary parts of data.

  **enable**

    *bool*, *optional*

    Executed the real v/s imaginary data plotting.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like, gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.



.. _inspect_data_amp_phase:

-------------------------------------
**amp_phase**
-------------------------------------

  Plot Amplitude vs Phase for  data.

  **enable**

    *bool*, *optional*

    Executes the plotting of amplitude v/s phase for data.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.



.. _inspect_data_amp_uvwave:

-------------------------------------
**amp_uvwave**
-------------------------------------

  Plot data amplitude v/s  uvwave.

  **enable**

    *bool*, *optional*

    Executes plotting data amplitude as a function of uvwave.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.



.. _inspect_data_amp_ant:

-------------------------------------
**amp_ant**
-------------------------------------

  Plot data amplitde v/s antenna.

  **enable**

    *bool*, *optional*

    Executes plotting data amplitude v/s antennas.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.



.. _inspect_data_phase_uvwave:

-------------------------------------
**phase_uvwave**
-------------------------------------

  Plot data phase v/s uvwave.

  **enable**

    *bool*, *optional*

    Executes plotting data phase v/s uvwave.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.



.. _inspect_data_amp_scan:

-------------------------------------
**amp_scan**
-------------------------------------

  Plot data amplitude v/s scan number.

  **enable**

    *bool*, *optional*

    Executes plotting data amplitude v/s scan number.

  **fields**

    *list* *of str*, *optional*

    Fields to plot. Specify by field id, index or keys like: gcal, bpcal.

  **column**

    *str*, *optional*

    Data column to plot.

  **avgtime**

    *str*, *optional*

    Time to average for plotting, in seconds.

  **avgchannel**

    *str*, *optional*

    Number of channels to average for plotting.

