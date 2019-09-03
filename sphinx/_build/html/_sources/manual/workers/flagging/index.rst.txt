.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _flagging:
 
==========================================
flagging
==========================================
 
.. toctree::
   :maxdepth: 1
 
Flagging of the data.



.. _flagging_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute flagging of the data.



.. _flagging_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  The label is added to the input .MS file name to define the name of the .MS file that should be flagged, <input>-<label>.ms. Default is an empty string, i.e., the original .MS is flagged.



.. _flagging_autoflag_autocorr_powerspectra:

--------------------------------------------------
**autoflag_autocorr_powerspectra**
--------------------------------------------------

  Flags antennas based on drifts in the scan average of the auto correlation spectra per field. This doesn't strictly require any calibration. It is also not field structure dependent, since it is just based on the DC of the field. Compares scan to median power of scans per field per channel. Also compares antenna to median of the array per scan per field per channel. This should catch any antenna with severe temperature problems.

  **enable**

    *bool*, *optional*, *default = False*

    Enables flagging of antennas based on drifts in the scan average of the auto correlation spectra per field.

  **scan_to_scan_threshold**

    *int*, *optional*, *default = 3*

    Threshold for flagging in sigma above the rest of the scans per field per channel.

  **antenna_to_group_threshold**

    *int*, *optional*, *default = 5*

    Threshold for flagging in sigma above array median power spectra per scan per field per channel.

  **column**

    *str*, *optional*, *default = DATA*

    Data column to flag.

  **fields**

    *str*, *optional*, *default = auto*

    Fields to flag. Given as 'auto' or comma-seperated keys (keys in gcal, bpcal, target).

  **calibrator_fields**

    *str*, *optional*, *default = auto*

    Calibrator fields. Given as 'auto' or comma-seperated keys (keys in gcal, bpcal).

  **threads**

    *int*, *optional*, *default = 8*

    Number of threads to use.



.. _flagging_flag_autocorr:

--------------------------------------------------
**flag_autocorr**
--------------------------------------------------

  Flag autocorrelations. Through CASA flagdata task.

  **enable**

    *bool*, *optional*, *default = False*

    Enables flagging of autocorrelations.



.. _flagging_quack_flagging:

--------------------------------------------------
**quack_flagging**
--------------------------------------------------

  Do quack flagging, i.e. flag the begining and/or end chunks of each scan. Again, through FLAGDATA.

  **enable**

    *bool*, *optional*, *default = False*

    Enable quack flagging.

  **quackinterval**

    *float*, *optional*, *default = 8.*

    Time interval (in seconds) to flag.

  **quackmode**

    *{"beg", "endb", "end", "tail"}*, *optional*, *default = beg*

    Quack flagging mode. Either 'beg', which flags scan begining, 'endb', which flags end of the scan, 'end', which flags everything but the first specified seconds of the scan and 'tail' which flags all but the last specified seconds of the scan.



.. _flagging_flag_shadow:

--------------------------------------------------
**flag_shadow**
--------------------------------------------------

  Flag shadowed antennas through the CASA task FLAGDATA.

  **enable**

    *bool*, *optional*, *default = False*

    Enables flagging of shadowed antennas.

  **tolerance**

    *float*, *optional*, *default = 0.*

    Amounts of shadow allowed (in metres). Default is 0. A positive number allows antennas to overlap in projection. A negative number forces antennas apart in projection.

  **include_full_mk64**

    *bool*, *optional*, *default = False*

    Consider all MeerKAT-64 antennas in the shadowing calculation even if only a subarray is used. Default is False.



.. _flagging_flag_spw:

--------------------------------------------------
**flag_spw**
--------------------------------------------------

  Flag spectral windows/channels. Of course, through FLAGDATA.

  **enable**

    *bool*, *optional*, *default = False*

    Enable flagging spectral windows/ channels.

  **channels**

    *str*, *optional*, *default = *:856~880MHz , *:1658~1800MHz, *:1419.8~1421.3MHz*

    Channels to flag. Given as "spectral window index:start channel ~ end channel" e.g. "\*:856~880MHz". End channel not inclusive.

  **ensure_valid_selection**

    *bool*, *optional*, *default = False*

    Check whether the channel selection returns any data. If it does not FLAGDATA is not executed preventing the pipeline from crashing. This check only works with the following spw formats (multiple, comma-separated selections allowed), "\*:firstchan~lastchan"; "firstspw~lastspw:firstchan~lastchan"; "spw:firstchan~lastchan"; "firstchan~lastchan". Channels are assumed to be in frequency (Hz, kHz, MHz, GHz allowed; if no units are given it assumes Hz).



.. _flagging_flag_time:

--------------------------------------------------
**flag_time**
--------------------------------------------------

  Flag timerange in the data using CASA FLAGDATA task.

  **enable**

    *bool*, *optional*, *default = False*

    Enabla flagging timeranges.

  **timerange**

    *str*, *optional*, *default = ' '*

    Timerange to flag. Given in format 'YYYY/MM/DD/HH:MM:SS-YYYY/MM/DD/HH:MM:SS'.



.. _flagging_flag_antennas:

--------------------------------------------------
**flag_antennas**
--------------------------------------------------

  Flag bad antennas. Or just the ones you have sworn a vendetta against.

  **enable**

    *bool*, *optional*, *default = False*

    Enables flagging of bad antennas.

  **antennas**

    *str*, *optional*, *default = 0*

    Antennas to flag. Follows the CASA Flagdata syntax.

  **timerange**

    *str*, *optional*, *default = ' '*

    Timerange to flag. Given in format 'YYYY/MM/DD/HH:MM:SS-YYYY/MM/DD/HH:MM:SS'.



.. _flagging_flag_scan:

--------------------------------------------------
**flag_scan**
--------------------------------------------------

  Flag bad scans. Uses CASA Flagdata task.

  **enable**

    *bool*, *optional*, *default = False*

    Enables flagging of bad scans.

  **scans**

    *str*, *optional*, *default = 0*

    Scans to flag. CASA flagdata syntax.



.. _flagging_static_mask:

--------------------------------------------------
**static_mask**
--------------------------------------------------

  Apply static mask to flag out known RFI, Meerkat specific.

  **enable**

    *bool*, *optional*, *default = False*

    Enables the application of static mask on the data.

  **mask**

    *str*, *optional*, *default = labelled_rfimask.pickle.npy*

    The mask to apply.

  **uvrange**

    *str*, *optional*, *default = ' '*

    UV range to select (CASA style range, e.g. lower~upper) for flagging. Leave blank for entire array.



.. _flagging_autoflag_rfi:

--------------------------------------------------
**autoflag_rfi**
--------------------------------------------------

  Flag RFI using AOFlagger software.

  **enable**

    *bool*, *optional*, *default = True*

    Enable RFI flagging with AOFlagger or tricolour (not active yet)

  **flagger**

    *{"aoflagger", "tricolour"}*, *optional*, *default = aoflagger*

    Choose flagger for automatic flagging

  **strategy**

    *str*, *optional*, *default = firstpass_QUV.rfis*

    The AOFlagger strategy file to use.

  **column**

    *str*, *optional*, *default = DATA*

    Specify column to flag

  **fields**

    *str*, *optional*, *default = auto*

    comma separated list of (zero-indexed) field ids to process

  **calibrator_fields**

    *str*, *optional*, *default = auto*

    comma separated list of (zero-indexed) field ids to process

  **bands**

    *str*, *optional*, *default = auto*

    comma separated list of (zero-indexed) band ids to process



.. _flagging_rfinder:

--------------------------------------------------
**rfinder**
--------------------------------------------------

  A tool to investigate the presence of RFI

  **enable**

    *bool*, *optional*, *default = False*

    Enable invsetigation of rfi with rfinder

  **telescope**

    *str*, *optional*, *default = MeerKAT*

    Name of telescope

  **field**

    *str*, *optional*, *default = target*

    Field to get flag stats. Given as a key (key in [gcal, bpcal, target]).

  **polarization**

    *{"xx", "XX", "yy", "YY", "xy", "XY", "yx", "YX", "q", "Q"}*, *optional*, *default = q*

    Select polarisation e.g. xx, yy, xy, yx, q (also in CAPS)

  **spw_enable**

    *bool*, *optional*, *default = True*

    Enable spw for rebinning

  **spw_width**

    *int*, *optional*, *default = 10*

    Channel width of rebinned output table (MHz)

  **time_enable**

    *bool*, *optional*, *default = True*

    Enable time chunking

  **time_step**

    *int*, *optional*, *default = 5*

    Time chunks in minutes

  **movies_in_report**

    *bool*, *optional*, *default = True*

    Generate movies in a repo



.. _flagging_flagging_summary:

--------------------------------------------------
**flagging_summary**
--------------------------------------------------

  Write flagging summary at the end of the pre-calibration flagging. Uses CASA FLAGDATA in "summary" mode.

  **enable**

    *bool*

    Enables the writing of flagging summary.

