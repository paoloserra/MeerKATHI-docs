.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Flag data
=========================
 
.. toctree::
   :maxdepth: 1
 
**[relevant workers:** :ref:`flagging`\ **]**

The :ref:`flagging` worker can run on the input .MS files or on .MS files created by
MeerKATHI from the input ones (e.g., by the :ref:`split_target` worker). In the
latter case the name of the .MS files to be flagged is based on that of the input .MS
files, with a label added before the extension. Users can set the label with the
*flagging:label* parameter in this worker.

The :ref:`flagging` worker allows users to flag the data in a variety of ways. Unless
otherwise stated below, flagging is done with the CASA task FLAGDATA.


* Flag on autocorrelations to catch antennas with obvious problems using the custom
  program POLITSIYAKAT (*flagging:autoflag_autocorr_powerspectra*). A number of additional
  parameters are available for this flagging mode.
* Flag all autocorrelations (*flagging:flag_autocorr*).
* Flag specific parts of all scans' beginning and/or end (*flagging:quack*). A number of
  additional parameters are available for this flagging mode.
* Flag shadowed antennas (*flagging:flag_shadow*). For observations obtained with a
  MeerKAT subarray it is possible to include offline antennas in the shadowing
  calculation. A number of additional parameters are available for this flagging mode.
* Flag selected channel ranges (*flagging:flag_spw*).
* Flag selected time ranges (*flagging:flag_time*).
* Flag selected antennas (*flagging:flag_antennas*).
* Flag selected scans (*flagging:flag_scan*).
* Flag according to a static mask of bad frequency ranges using the custom program
  RFIMASKER (*flagging:static_mask*). The mask file should be located at the *input*
  directory set with the :ref:`general` worker. Users can decide to limit the mask to a
  selected UV range.
* Flag with AOFlagger (Offringa et al. 2012, A&A, 539, A95). The AOFlagger strategy file
  should be located at the *input* directory set with the :ref:`general` worker.
  Additional parameters allow users to limit the execution of AOFlagger to selected
  columns, fields or frequency bands of the .MS files.

Finally, a summary of the flags can be obtained with *flagging:flagging_summary*. The
summary is available at the relevant log file (see :ref:`products`).
