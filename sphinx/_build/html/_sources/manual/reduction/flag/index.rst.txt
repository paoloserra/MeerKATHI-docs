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
MeerKATHI at various stages of the pipeline (e.g., by the :ref:`split_target` worker).
In the latter case the name of the .MS files to be flagged is based on that of the input
.MS files, with a label added before the extension. Users can set the label with the
:ref:`flagging: label <flagging_label>` parameter in this worker.

The :ref:`flagging` worker allows users to flag the data in a variety of ways. Unless
otherwise stated below, flagging is done with the CASA task FLAGDATA. Follow the links
below for a detailed documentation of the individual flagging modes.


* Flag on autocorrelations to catch antennas with obvious problems using the custom
  program POLITSIYAKAT (:ref:`flagging: autoflag_autocorr_powerspectra <flagging_autoflag_autocorr_powerspectra>`).
  Individual scans are compared to the median of all scans per field and channel; and
  individual antennas are compared to the median of all antennas per scan, field and channel.
  Both methods have their own flagging threshold, which users can tune. Users can also set
  which column and which fields to flag.
* Flag all autocorrelations (:ref:`flagging: flag_autocorr <flagging_flag_autocorr>`).
* Flag specific portions of the beginning and/or end of each scan
  (:ref:`flagging: quack_flagging <flagging_quack_flagging>`).
  As in the CASA task FLAGDATA, users can set the time interval that should be flagged
  and the quackmode.
* Flag shadowed antennas (:ref:`flagging: flag_shadow <flagging_flag_shadow>`).
  Users can tune the amount of shadowing allowed before flagging an antenna.
  For observations obtained with a MeerKAT subarray it is possible to include offline
  antennas in the shadowing calculation.
* Flag selected channel ranges (:ref:`flagging: flag_spw <flagging_flag_spw>`).
* Flag selected time ranges (:ref:`flagging: flag_time <flagging_flag_time>`).
* Flag selected antennas (:ref:`flagging: flag_antennas <flagging_flag_antennas>`).
  Within this task, users can limit the flagging of selected antennas to a
  selected timerange.
* Flag selected scans (:ref:`flagging: flag_scan <flagging_flag_scan>`).
* Flag according to a static mask of bad frequency ranges using the custom program
  RFIMASKER (:ref:`flagging: static_mask <flagging_static_mask>`). The mask file should
  be located at the *input* directory set by :ref:`general: input <general_input>`.
  Users can decide to limit the flagging to a selected UV range. This could be useful
  to flag short baselines only.
* Flag with AOFlagger (:ref:`flagging: autoflag_rfi <flagging_autoflag_rfi>`). The
  AOFlagger strategy file should be located at the *input* directory set by
  :ref:`general: input <general_input>`.
  MeerKATHI comes with a number of strategy files, which are located in the
  meerkathi/data/meerkat_files directory and are copied to the *input* directory by the
  :ref:`general` worker. However, users can copy their own strategy file to the same
  *input* directory and use it within MeerKATHI.
  Additional parameters allow users to limit the execution of AOFlagger to selected
  columns, fields or frequency bands of the .MS files. AOFlagger is described by
  Offringa et al. (2012), A&A, 539, A95.

Finally, a summary of the flags can be obtained with :ref:`flagging: flagging_summary <flagging_flagging_summary>`.
The summary is available at the relevant log file (see :ref:`products`).
