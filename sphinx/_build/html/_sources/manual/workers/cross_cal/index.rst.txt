.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _cross_cal:
 
==========================================
cross_cal
==========================================
 
.. toctree::
   :maxdepth: 1
 
Carry out Cross calibration of the data (delay, bandpass and gain calibration)



.. _cross_cal_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute this segment.



.. _cross_cal_otfdelay:

--------------------------------------------------
**otfdelay**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Set whether to apply the delay calibration on the fly when solving for other calibration terms.



.. _cross_cal_uvrange:

--------------------------------------------------
**uvrange**
--------------------------------------------------

  *str*, *optional*, *default = >50*

  Set the U-V range for data selection, e.g. '>50'.



.. _cross_cal_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = 1gc1*

  Label for output files.



.. _cross_cal_casa_version:

--------------------------------------------------
**casa_version**
--------------------------------------------------

  *str*, *optional*, *default = 47*

  Casa version to carry out cross-calibration. '47' means use CASA 4.7, which is recommended, unless you enjoy your data extra flag-gy. Leave empty to use the latest CASA.



.. _cross_cal_set_model:

--------------------------------------------------
**set_model**
--------------------------------------------------

  Essentially setjy task from CASA.

  **enable**

    *bool*, *optional*, *default = True*

    Execute the setjy task.

  **meerkathi_model**

    *bool*, *optional*, *default = False*

    Force disable built-in models in MeerKATHI (NOT RECOMMENDED!)

  **no_verify**

    *bool*, *optional*, *default = False*

    Enables setting standard manually.

  **field**

    *str*, *optional*, *default = fcal*

    Set the field to carry out setjy on. Specify either the field number, name or even as 'fcal' corresponding to field specification in observation config.

  **threads**

    *int*, *optional*, *default = 8*

    Set the number of threads to use when predicting local sky model using MeqTrees.



.. _cross_cal_primary_cal:

--------------------------------------------------
**primary_cal**
--------------------------------------------------

  Calibrating on the bandpass calibrator field

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **reuse_existing_gains**

    *bool*, *optional*, *default = False*

    Reuse gain tables if they exist

  **order**

    *str*, *optional*, *default = KGB*

    Order in which to solve for gains for this field. E.g, if order is set to 'KGB', the we solve for delays, then the phase and amplitude, and finally the bandpass. The full options are: K-delay calibration; G-amplitude and phase calibration; B-bandpass calibration; A-automatic flagging (existing gains will be applied first).

  **solnorm**

    *bool*, *optional*, *default = False*

    Normalise average solution amplitude to 1.0

  **combine**

    *list* *of str*, *optional*, *default = '', '', scan*

    Parameter to combine different data axis for solving. Options are ['','obs', 'scan', 'spw', 'field', 'obs,scan', 'scan,ob']

  **solint**

    *list* *of str*, *optional*, *default = 120s, 120s, inf*

    Solution interval for delay-correction calibration.

  **calmode**

    *list* *of str*, *optional*, *default = a, ap, ap*

    Type of solution

  **B_fillgaps**

    *int*, *optional*, *default = 70*

    Fill flagged solution channels by interpolation

  **plotgains**

    *bool*, *optional*, *default = True*

    Plot gains

  **flag**

    Apply existing gains and flag corrected data

    **column**

      *{"corrected", "residual"}*, *optional*, *default = corrected*

      Data column to flag on

    **usewindowstats**

      *{"none", "sum", "std", "both"}*, *optional*, *default = std*

      Calculate additional flags using sliding window statistics

    **combinescans**

      *bool*, *optional*, *default = False*

      Accumulate data across scans depending on the value of ntime

    **flagdimension**

      *{"freq", "time", "freqtime", "timefreq"}*, *optional*, *default = freqtime*

      Dimensions along which to calculate fits (freq/time/freqtime/timefreq)

    **timecutoff**

      *float*, *optional*, *default = 4.0*

      Flagging thresholds in units of deviation from the fit

    **freqcutoff**

      *float*, *optional*, *default = 3.0*

      Flagging thresholds in units of deviation from the fit

    **correlation**

      *str*, *optional*, *default = ' '*

      Correlation



.. _cross_cal_secondary_cal:

--------------------------------------------------
**secondary_cal**
--------------------------------------------------

  Calibrating on the amplitude/phase calibrator field

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **reuse_existing_gains**

    *bool*, *optional*, *default = False*

    Reuse gain tables if they exist

  **order**

    *str*, *optional*, *default = KG*

    Order in which to solve for gains for this field. E.g, if order is set to 'KGB', the we solve for delays, then the phase and amplitude, and finally the bandpass. The full options are: K-delay calibration; G-amplitude and phase calibration; B-bandpass calibration; A-automatic flagging (existing gains will be applied first); I-Do a self-callibration

  **solnorm**

    *bool*, *optional*, *default = False*

    Normalise average solution amplitude to 1.0

  **combine**

    *list* *of str*, *optional*, *default = '', scan*

    Parameter to combine different data axis for solving. Options are ['','obs', 'scan', 'spw', 'field', 'obs,scan', 'scan,ob']

  **solint**

    *list* *of str*, *optional*, *default = 120s, 120s*

    Solution interval for delay-correction calibration.

  **calmode**

    *list* *of str*, *optional*, *default = a, ap, ap*

    Type of solution

  **apply**

    *str*, *optional*, *default = B*

    Gains to apply from calibration of bandpass field

  **plotgains**

    *bool*, *optional*, *default = True*

    Plot gains

  **flag**

    Apply existing gains and flag corrected data

    **column**

      *{"corrected", "residual"}*, *optional*, *default = corrected*

      Data column to flag on

    **usewindowstats**

      *{"none", "sum", "std", "both"}*, *optional*, *default = std*

      Calculate additional flags using sliding window statistics

    **combinescans**

      *bool*, *optional*, *default = False*

      Accumulate data across scans depending on the value of ntime

    **flagdimension**

      *{"freq", "time", "freqtime", "timefreq"}*, *optional*, *default = freqtime*

      Dimensions along which to calculate fits (freq/time/freqtime/timefreq)

    **timecutoff**

      *float*, *optional*, *default = 4.0*

      Flagging thresholds in units of deviation from the fit

    **freqcutoff**

      *float*, *optional*, *default = 3.0*

      Flagging thresholds in units of deviation from the fit

    **correlation**

      *str*, *optional*, *default = ' '*

      Correlation



.. _cross_cal_apply_cal:

--------------------------------------------------
**apply_cal**
--------------------------------------------------

  Apply calibration

  **enable**

    *bool*, *optional*, *default = True*

    Execute this section

  **applyto**

    *list* *of str*, *optional*, *default = bpcal, gcal, target*

    Fields to apply calibration to

  **calmode**

    *{"=", "calflag", "calflagstrict", "trial", "flagonly", "flagonlystrict"}*, *optional*, *default = calflag*

    Calibration mode, the default being "calflag" - calibrates and applies flags from solutions. See CASA documentation for info on other modes.



.. _cross_cal_flagging_summary:

--------------------------------------------------
**flagging_summary**
--------------------------------------------------

  Prints out the buther's bill, i.e. data flagging summary at the end of cross calibration process.

  **enable**

    *bool*, *optional*, *default = True*

    Execute printing flagging summary.

