.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Flag data
=========================
 
.. toctree::
   :maxdepth: 1
 
**[relevant workers:** :ref:`flagging`\ **]**

The :ref:`flagging` worker can be run on the input .MS files or on .MS files created at
various stages of MeerKATHI based on the input .MS files (e.g., by the :ref:`split_target`
worker). The name of the .MS files created by MeerKATHI is based on that of the input .MS
files with a label added before the extension. Users can run the :ref:`flagging` worker on
such files by setting the *flagging:label* parameter in this worker.

The :ref:`flagging` worker allows users to flag the data in a variety of ways using the
CASA FLAGDATA task (unless otherwise stated below):


* based on autocorrelations to catch antennas with obvious problems using the custom
  program POLITSIYAKAT (*flagging:autoflag_autocorr_powerspectra*); a number of additional
  parameters are available for this flagging mode;
* flag all autocorrelations (*flagging:flag_autocorr*);
* flag specific parts of all scans' beginning and/or end (*flagging:quack*); a number of
  additional parameters are available for this flagging mode;
* flag shadowed antennas (*flagging:flag_shadow*); for observations obtained with a
  MeerKAT subarray it is possible to include offline antennas in the shadowing
  calculation; a number of additional parameters are available for this flagging mode;
* flag selected channel ranges (*flagging:flag_spw*);
* flag selected time ranges (*flagging:flag_time*);
* flag selected antennas (*flagging:flag_antennas*);
* flag selected scans (*flagging:flag_scan*);
* flag according to a static mask of bad frequency ranges using the custom program
  RFIMASKER (*flagging:static_mask*); the mask file should be located at the *input*
  directory set with the :ref:`general` worker; users can decide to limit the mask to a
  selected UV range;
* flag with AOFlagger (Offringa et al. 2012, A&A, 539, A95); the AOFlagger strategy file
  should be located at the *input* directory set with the :ref:`general` worker;
  additional parameters allow users to limit the execution of AOFlagger to selected
  columns, fields or frequency bands of the .MS files.

Finally, a summary of the flags can be obtained with *flagging:flagging_summary*. The
summary is available at the relevant log file (see :ref:`products`).