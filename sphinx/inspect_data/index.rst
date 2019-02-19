.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
inspect_data
==========================================
 
.. toctree::
   :maxdepth: 1
 
Dignostic plots of the first-pass cross-calibrated data.



-------------------------------------
**enable**
-------------------------------------
  *bool*, *optional*

  Executes dignostic plotting of the first-pass cross-calibrated data.



-------------------------------------
**order**
-------------------------------------
  *int*, *optional*

  The order in which this step will be executed in the pipeline.



-------------------------------------
**label**
-------------------------------------
  *str*, *optional*

  Lable for output products (plots etc.) for this step.



-------------------------------------
**real_imag**
-------------------------------------
  Plot real vs imaginary parts of data.

    **enable**
      *bool*, *optional*
      Executed the real v/s imaginary data plotting.

    **fields**
      *optional*
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



-------------------------------------
**amp_phase**
-------------------------------------
  Plot Amplitude vs Phase for  data.

    **enable**
      *bool*, *optional*
      Executes the plotting of amplitude v/s phase for data.

    **fields**
      *optional*
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



-------------------------------------
**amp_uvwave**
-------------------------------------
  Plot data amplitude v/s  uvwave.

    **enable**
      *bool*, *optional*
      Executes plotting data amplitude as a function of uvwave.

    **fields**
      *optional*
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



-------------------------------------
**amp_ant**
-------------------------------------
  Plot data amplitde v/s antenna.

    **mapping**
    **enable**
      *bool*, *optional*
      Executes plotting data amplitude v/s antennas.

    **fields**
      *optional*
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



-------------------------------------
**phase_uvwave**
-------------------------------------
  Plot data phase v/s uvwave.

    **enable**
      *bool*, *optional*
      Executes plotting data phase v/s uvwave.

    **fields**
      *optional*
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



-------------------------------------
**amp_scan**
-------------------------------------
  Plot data amplitude v/s scan number.

    **enable**
      *bool*, *optional*
      Executes plotting data amplitude v/s scan number.

    **fields**
      *optional*
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

