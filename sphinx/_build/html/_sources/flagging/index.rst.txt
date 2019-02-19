.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
flagging
==========================================
 
.. toctree::
   :maxdepth: 1
 
Flagging of the data.



-------------------------------------
**enable**
-------------------------------------
  *bool*, *optional*

  Execute flagging of the data.



-------------------------------------
**order**
-------------------------------------
  *int*, *optional*

  Order in queue of workers. Generally a non-negative integer.



-------------------------------------
**label**
-------------------------------------
  *str*, *optional*

  The label is added to the input .MS file name to define the name of the .MS file that should be flagged, <input>-<label>.ms. Default is an empty string, i.e., the original .MS is flagged.



-------------------------------------
**hires_label**
-------------------------------------
  *str*, *optional*

  Label for high frequency resolution data.



-------------------------------------
**hires_flag**
-------------------------------------
  *bool*, *optional*

  Enables AOFlagger run on high frequency resolution data.



-------------------------------------
**autoflag_autocorr_powerspectra**
-------------------------------------
  Flags antennas based on drifts in the scan average of the auto correlation spectra per field. This doesn't strictly require any calibration. It is also not field structure dependent, since it is just based on the DC of the field. Compares scan to median power of scans per field per channel. Also compares antenna to median of the array per scan per field per channel. This should catch any antenna with severe temperature problems.

    **enable**
      *bool*, *optional*

      Enables flagging of antennas based on drifts in the scan average of the auto correlation spectra per field.

    **scan_to_scan_threshold**
      *int*, *optional*

      Threshold for flagging in sigma above the rest of the scans per field per channel.

    **antenna_to_group_threshold**
      *int*, *optional*

      Threshold for flagging in sigma above array median power spectra per scan per field per channel.

    **column**
      *str*, *optional*

      Data column to flag.

    **fields**
      *str*, *optional*

      Fields to flag. Given as 'auto' or comma-seperated keys (keys in gcal, bpcal, target).

    **calibrator_fields**
      *str*, *optional*

      Calibrator fields. Given as 'auto' or comma-seperated keys (keys in gcal, bpcal).

    **threads**
      *int*, *optional*

      Number of threads to use.



-------------------------------------
**flag_autocorr**
-------------------------------------
  Flag autocorrelations. Through CASA flagdata task.

    **enable**
      *bool*, *optional*

      Enables flagging of autocorrelations.



-------------------------------------
**quack_flagging**
-------------------------------------
  Do quack flagging, i.e. flag the begining and/or end chunks of each scan. Again, through FLAGDATA.

    **enable**
      *bool*, *optional*

      Enable quack flagging.

    **quackinterval**
      *float*, *optional*

      Time interval (in seconds) to flag.

    **quackmode**
      *str*, *optional*

      Quack flagging mode. Either 'beg', which flags scan begining, 'endb', which flags end of the scan, 'end', which flags everything but the first specified seconds of the scan and 'tail' which flags all but the last specified seconds of the scan.



-------------------------------------
**flag_shadow**
-------------------------------------
  Flag shadowed antennas through the CASA task FLAGDATA.

    **enable**
      *bool*, *optional*

      Enables flagging of shadowed antennas.

    **tolerance**
      *float*, *optional*

      Amounts of shadow allowed (in metres). Default is 0. A positive number allows antennas to overlap in projection. A negative number forces antennas apart in projection.

    **include_full_mk64**
      *bool*, *optional*

      Consider all MeerKAT-64 antennas in the shadowing calculation even if only a subarray is used. Default is False.



-------------------------------------
**flag_spw**
-------------------------------------
  Flag spectral windows/channels. Of course, through FLAGDATA.

    **enable**
      *bool*, *optional*

      Enable flagging spectral windows/ channels.

    **channels**
      *str*, *optional*

      Channels to flag. Given as "spectral window index:start channel ~ end channel", e.g. "*:856~880MHz". End channel not inclusive.

    **ensure_valid_selection**
      *bool*, *optional*

      Check whether the channel selection returns any data. If it does not, FLAGDATA is not executed, preventing the pipeline from crashing. This check only works with the following spw formats (multiple, comma-separated selections allowed), "*:firstchan~lastchan"; "firstspw~lastspw:firstchan~lastchan"; "spw:firstchan~lastchan"; "firstchan~lastchan". Channels are assumed to be in frequency (Hz, kHz, MHz, GHz allowed; if no units are given it assumes Hz).



-------------------------------------
**flag_time**
-------------------------------------
  Flag timerange in the data using CASA FLAGDATA task.

    **enable**
      *bool*, *optional*

      Enabla flagging timeranges.

    **timerange**
      *str*, *optional*

      Timerange to flag. Given in format 'YYYY/MM/DD/HH:MM:SS-YYYY/MM/DD/HH:MM:SS'.



-------------------------------------
**flag_antennas**
-------------------------------------
  Flag bad antennas. Or just the ones you have sworn a vendetta against.

    **enable**
      *bool*, *optional*

      Enables flagging of bad antennas.

    **antennas**
      *str*, *optional*

      Antennas to flag. Follows the CASA Flagdata syntax.

    **timerange**
      *str*, *optional*

      Timerange to flag. Given in format 'YYYY/MM/DD/HH:MM:SS-YYYY/MM/DD/HH:MM:SS'.



-------------------------------------
**flag_scan**
-------------------------------------
  Flag bad scans. Uses CASA Flagdata task.

    **enable**
      *bool*, *optional*

      Enables flagging of bad scans.

    **scans**
      *str*, *optional*

      Scans to flag. CASA flagdata syntax.



-------------------------------------
**static_mask**
-------------------------------------
  Apply static mask to flag out known RFI, Meerkat specific.

    **enable**
      *bool*, *optional*

      Enables the application of static mask on the data.

    **mask**
      *str*, *optional*

      The mask to apply.

    **uvrange**
      *str*, *optional*

      UV range to select (CASA style range, e.g. lower~upper) for flagging. Leave blank for entire array.



-------------------------------------
**autoflag_rfi**
-------------------------------------
  Flag RFI using AOFlagger software.

    **enable**
      *bool*, *optional*

      Enable RFI flagging with AOFlagger.

    **strategy**
      *str*, *optional*

      The AOFlagger strategy file to use.

    **column**
      *str*, *optional*

      Specify column to flag

    **fields**
      *str*, *optional*

      comma separated list of (zero-indexed) field ids to process

    **bands**
      *str*, *optional*

      comma separated list of (zero-indexed) band ids to process



-------------------------------------
**flagging_summary**
-------------------------------------
  Write flagging summary at the end of the pre-calibration flagging. Uses CASA FLAGDATA in "summary" mode.

    **enable**
      *bool*, *optional*

      Enables the writing of flagging summary.

