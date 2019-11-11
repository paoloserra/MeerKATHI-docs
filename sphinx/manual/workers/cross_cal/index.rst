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



.. _cross_cal_clear_cal:

--------------------------------------------------
**clear_cal**
--------------------------------------------------

  Initializes dataset for calibration using CASA

  **enable**

    *bool*, *optional*, *default = True*

    Execute intialization step

  **field**

    *list* *of str*, *optional*, *default = fcal, bpcal, gcal, xcal, target*

    fields to initialize

  **addmodel**

    *bool*, *optional*, *default = True*

    Intializes scratch MODEL_DATA column



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



.. _cross_cal_delay_cal:

--------------------------------------------------
**delay_cal**
--------------------------------------------------

  Carry out delay correction calibration (using gaincal task from CASA).

  **enable**

    *bool*, *optional*, *default = True*

    Execute delay correction calibration.

  **combine**

    *{"", "obs", "scan", "spw", "field", "obs,scan", "scan,obs"}*, *optional*, *default = scan*

    Parameter to combine different data axis for solving.

  **solint**

    *str*, *optional*, *default = inf*

    Solution interval for delay-correction calibration.

  **minsnr**

    *int*, *optional*, *default = 3*

    Minimum required SNR for solutions.

  **field**

    *list* *of str*, *optional*, *default = bpcal*

    Set the field to estimate the delay correction from. Specify either the field number, name or even as 'fcal' corresponding to field specification in observation config.

  **plot**

    Plotting dignostics plots for delay correction calibration.

    **enable**

      *bool*, *optional*, *default = True*

      Enables plotting dignostics

    **gaintype**

      *str*, *optional*, *default = K*

      Type of gain solution table

    **field**

      *list* *of str*, *optional*, *default = bpcal*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V

    **htmlname**

      *str*, *optional*, *default = ' '*

      Output HTML file name

  **flag**

    Flagging based on delay correction solutions.

    **enable**

      *bool*, *optional*, *default = True*

      Enable flagging based on delay correction solutions via CASA FLAGDATA task.

    **mode**

      *{"list", "manual", "clip", "quack", "shadow", "elevation", "tfcrop", "antint", "extend", "unflag", "summary"}*, *optional*, *default = clip*

      Mode to set for flagging based on delay correction gains. Default used is "clip". If you want to use other modes, specify the relevant keywords from Flagdata.

    **clipminmax**

      *list* *of float*, *optional*, *default = -60.0, 60.0*

      Specifies the minimum and maximum delay to keep, e.g. [-60, 60]. Execute order 66 on the rest.



.. _cross_cal_bp_cal:

--------------------------------------------------
**bp_cal**
--------------------------------------------------

  Carry out bandpass calibration (using bandpass task from CASA)

  **enable**

    *bool*, *optional*, *default = True*

    Executes bandpass calibration.

  **combine**

    *{"", "obs", "scan", "spw", "field", "obs,scan", "scan,obs"}*, *optional*, *default = scan*

    Parameter to combine different data axis for solving.

  **field**

    *list* *of str*, *optional*, *default = bpcal*

    Set the field to estimate the bandpass from. Specify either the field number, name or even as 'bpcal' corresponding to field specification in observation config.

  **minnrbl**

    *int*, *optional*, *default = 4*

    Minimum number of baselines required (per antenna) for solving.

  **minsnr**

    *int*, *optional*, *default = 5*

    Minimum required SNR for solutions.

  **solnorm**

    *bool*, *optional*, *default = True*

    Normalize average solution amplitudes to unity.

  **solint**

    *str*, *optional*, *default = inf*

    Solution interval for bandpass calibration.

  **solint_PREB0**

    *str*, *optional*, *default = 60s*

    Solution interval for delay-correction calibration.

  **set_refant**

    *bool*, *optional*, *default = False*

    Should a reference antenna be used for this calibration

  **remove_ph_time_var**

    Remove large temporal phase variations from the bandpass calibrator before solving for the bandpass.

    **enable**

      *bool*, *optional*, *default = False*

      Enable removal of gain phase variations with time prior to solving for final bandpass.

    **bp_solint**

      *str*, *optional*, *default = inf*

      Solution interval for bandpass calibration before determining the variation of the gain phase with time.

    **bp_combine**

      *{"", "obs", "scan", "spw", "field", "obs,scan", "scan,obs"}*, *optional*, *default = ' '*

      Parameter to combine different data axis for solving.

    **g_solint**

      *str*, *optional*, *default = inf*

      Solution interval for gain phase calibration to be applied when solving for the final bandpass.

    **g_combine**

      *{"", "obs", "scan", "spw", "field", "obs,scan", "scan,obs"}*, *optional*, *default = ' '*

      Parameter to combine different data axis for solving.

  **flag**

    Flagging based on bandpass amplitude solutions.

    **enable**

      *bool*, *optional*, *default = False*

      Enable flagging based on Bandpass correction solutions via CASA FLAGDATA task.

    **mode**

      *{"list", "manual", "clip", "quack", "shadow", "elevation", "tfcrop", "antint", "extend", "unflag", "summary"}*, *optional*, *default = clip*

      Mode to set for flagging based on delay correction gains. Default is "clip". If you want to use other modes, specify the relevant keywords from Flagdata.

    **clipminmax**

      *list* *of float*, *optional*, *default = 0.1,10.0*

      Specifies the minimum and maximum gain to keep, e.g. [0.1, 10].

  **plot**

    Plotting dignostics plots for bandpass correction calibration.

    **enable**

      *bool*, *optional*, *default = True*

      Enables plotting dignostics

    **gaintype**

      *str*, *optional*, *default = B*

      Type of gain solution table

    **field**

      *list* *of str*, *optional*, *default = bpcal*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V

    **htmlname**

      *str*, *optional*, *default = ' '*

      Output HTML file name



.. _cross_cal_gain_cal_flux:

--------------------------------------------------
**gain_cal_flux**
--------------------------------------------------

  Carry out gain calibration on the flux calibrator field.

  **enable**

    *bool*, *optional*, *default = True*

    Execute gain calibration on the flux calibrator field.

  **combine**

    *{"", "obs", "scan", "spw", "field"}*, *optional*, *default = ' '*

    Parameter to combine different data axis for solving.

  **field**

    *list* *of str*, *optional*, *default = fcal*

    Set the field to estimate the gain from. Specify either the field number, name or even as 'fcal' corresponding to field specification in observation config.

  **minnrbl**

    *int*, *optional*, *default = 4*

    Minimum number of baselines required (per antenna) for solving.

  **minsnr**

    *int*, *optional*, *default = 5*

    Minimum required SNR for solutions.

  **solint**

    *str*, *optional*, *default = inf*

    Time solution interval

  **set_refant**

    *bool*, *optional*, *default = False*

    Should a reference antenna be used for this calibration

  **flag**

    Flagging based on flux-scale amplitude solutions.

    **enable**

      *bool*, *optional*, *default = False*

      Enable flagging based on delay correction solutions via CASA FLAGDATA task. Default is False.

    **mode**

      *{"list", "manual", "clip", "quack", "shadow", "elevation", "tfcrop", "antint", "extend", "unflag", "summary"}*, *optional*, *default = clip*

      Mode to set for flagging based on delay correction gains. Default is "clip". If you want to use other modes, specify the relevant keywords from Flagdata.

    **clipminmax**

      *list* *of float*, *optional*, *default = 0.1, 10.0*

      Specifies the minimum and maximum delay to keep, e.g. [0.1, 10].

  **plot**

    Plotting dignostics plots for flux calibrator corrections.

    **enable**

      *bool*, *optional*, *default = True*

      Enables plotting dignostics

    **gaintype**

      *str*, *optional*, *default = G*

      Type of gain solution table

    **field**

      *list* *of str*, *optional*, *default = fcal*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V

    **htmlname**

      *str*, *optional*, *default = ' '*

      Output HTML file name



.. _cross_cal_gain_cal_gain:

--------------------------------------------------
**gain_cal_gain**
--------------------------------------------------

  Carry out gain calibration on the gain calibrator field.

  **enable**

    *bool*, *optional*, *default = True*

    Execute gain calibration on the gain calibrator field.

  **combine**

    *{"", "obs", "scan", "spw", "field"}*, *optional*, *default = ' '*

    Parameter to combine different data axis for solving.

  **field**

    *list* *of str*, *optional*, *default = gcal*

    Set the field to estimate the gain from. Specify either the field number, name or even as 'gcal' corresponding to field specification in observation config.

  **minnrbl**

    *int*, *optional*, *default = 4*

    Minimum number of baselines required (per antenna) for solving.

  **minsnr**

    *int*, *optional*, *default = 3*

    Minimum required SNR for solutions.

  **solint**

    *str*, *optional*, *default = inf*

    Time solution interval

  **set_refant**

    *bool*, *optional*, *default = False*

    Should a reference antenna be used for this calibration

  **flag**

    Flagging based on gain amplitudes.

    **enable**

      *bool*, *optional*, *default = False*

      Enable flagging based on delay correction solutions via CASA FLAGDATA task. Default is False.

    **mode**

      *{"list", "manual", "clip", "quack", "shadow", "elevation", "tfcrop", "antint", "extend", "unflag", "summary"}*, *optional*, *default = clip*

      Mode to set for flagging based on delay correction gains. Default is "clip". If you want to use other modes, specify the relevant keywords from Flagdata.

    **clipminmax**

      *list* *of float*, *optional*, *default = 0.1, 10.0*

      Specifies the minimum and maximum delay to keep, e.g. [0.1, 10].

  **plot**

    Plotting dignostics plots for gain calibrator corrections.

    **enable**

      *bool*, *optional*, *default = True*

      Enables plotting dignostics

    **gaintype**

      *str*, *optional*, *default = G*

      Type of gain solution table

    **field**

      *list* *of str*, *optional*, *default = gcal*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V

    **htmlname**

      *str*, *optional*, *default = ' '*

      Output HTML file name



.. _cross_cal_transfer_fluxscale:

--------------------------------------------------
**transfer_fluxscale**
--------------------------------------------------

  Transfers fluxscale from the flux calibrator field to the gain calibrator.

  **enable**

    *bool*, *optional*, *default = True*

    Executes transferring flux scale.

  **reference**

    *list* *of str*, *optional*, *default = fcal*

    Field to transfer flux sale from. Specify either the field number, name or even as 'fcal' corresponding to field specification in observation config.

  **transfer**

    *list* *of str*, *optional*, *default = gcal*

    Field to transfer flux scale to. Specify either the field number, name or even as 'gcal' corresponding to field specification in observation config.

  **plot**

    Enables plotting gain amplitudes for Flux and Gain calibrator field.

    **enable**

      *bool*, *optional*, *default = True*

      Enables plotting dignostics

    **gaintype**

      *str*, *optional*, *default = G*

      Type of gain solution table

    **field**

      *list* *of str*, *optional*, *default = gcal*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V

    **htmlname**

      *str*, *optional*, *default = ' '*

      Output HTML file name



.. _cross_cal_apply_delay_cal:

--------------------------------------------------
**apply_delay_cal**
--------------------------------------------------

  Apply the delay correction calibration table to specified fields via the CASA applycal task.

  **enable**

    *bool*, *optional*, *default = True*

    Executes application of delay correction calibration table.

  **field**

    *list* *of str*, *optional*, *default = bpcal*

    Field to select in the delay correction calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

  **applyto**

    *list* *of str*, *optional*, *default = bpcal, gcal, xcal, target*

    Field(s) to apply the delay correction calibration table to. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal, gcal, target'.

  **applymode**

    *{"=", "calflag", "calflagstrict", "trial", "flagonly", "flagonlystrict"}*, *optional*, *default = calflag*

    Calibration mode, the default being "calflag" - calibrates and applies flags from solutions. See CASA documentation for info on other modes.



.. _cross_cal_apply_bp_cal:

--------------------------------------------------
**apply_bp_cal**
--------------------------------------------------

  Apply the bandpass table to specified fields via the CASA applycal task.

  **enable**

    *bool*, *optional*, *default = True*

    Executes application of bandpass table.

  **field**

    *list* *of str*, *optional*, *default = bpcal*

    Field to select in the bandpass table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal'.

  **applyto**

    *list* *of str*, *optional*, *default = bpcal, gcal, xcal, target*

    Field(s) to apply the bandpass table to. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal, gcal, target'.

  **applymode**

    *{"=", "calflag", "calflagstrict", "trial", "flagonly", "flagonlystrict"}*, *optional*, *default = calflag*

    Calibration mode, the default being "calflag" - calibrates and applies flags from solutions. See CASA documentation for info on other modes.



.. _cross_cal_apply_gain_cal_gain:

--------------------------------------------------
**apply_gain_cal_gain**
--------------------------------------------------

  Apply the gain calibration table to specified fields via the CASA applycal task.

  **enable**

    *bool*, *optional*, *default = False*

    Executes application of gain calibration table.

  **field**

    *list* *of str*, *optional*, *default = gcal*

    Field to select in the gain calibration table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.

  **applyto**

    *list* *of str*, *optional*, *default = bpcal, gcal, xcal, target*

    Field(s) to apply the gain calibration table to. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal, gcal, target'.

  **applymode**

    *{"=", "calflag", "calflagstrict", "trial", "flagonly", "flagonlystrict"}*, *optional*, *default = calflag*

    Calibration mode, the default being "calflag" - calibrates and applies flags from solutions. See CASA documentation for info on other modes.



.. _cross_cal_apply_transfer_fluxscale:

--------------------------------------------------
**apply_transfer_fluxscale**
--------------------------------------------------

  Apply the fluxscale table to specified fields via the CASA applycal task.

  **enable**

    *bool*, *optional*, *default = True*

    Executes application of fluxscale table.

  **field**

    *list* *of str*, *optional*, *default = gcal*

    Field to select in the fluxscale table. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'gcal'.

  **applyto**

    *list* *of str*, *optional*, *default = bpcal, gcal, xcal, target*

    Field(s) to apply the fluxscale table to. Specify either the field number, name or as corrsponding to field spec in observation config, e.g. 'bpcal, gcal, target'.

  **applymode**

    *{"=", "calflag", "calflagstrict", "trial", "flagonly", "flagonlystrict"}*, *optional*, *default = calflag*

    Calibration mode, the default being "calflag" - calibrates and applies flags from solutions. See CASA documentation for info on other modes.



.. _cross_cal_autoflag_closure_error:

--------------------------------------------------
**autoflag_closure_error**
--------------------------------------------------

  Flag closure errors and systematic issues based on calibrated calibrator phase.

  **enable**

    *bool*, *optional*, *default = False*

    Execute flagging closure errors etc.

  **scan_to_scan_threshold**

    *int*, *optional*, *default = 3*

    Sigma spread above the rest of the scans per field per channel.

  **baseline_to_group_threshold**

    *int*, *optional*, *default = 3*

    Sigma above array median phase spread per scan per field per channel.

  **column**

    *str*, *optional*, *default = CORRECTED_DATA*

    MS column to use.

  **fields**

    *str*, *optional*, *default = auto*

    Fields to flag. Either set 'auto' or specify as 'gcal, bpcal, target'

  **calibrator_fields**

    *str*, *optional*, *default = auto*

    Calibrator fields to estimate the closure errors etc. from.

  **threads**

    *int*, *optional*, *default = 1*

    Number of cores to use to carry out this process.



.. _cross_cal_flagging_summary:

--------------------------------------------------
**flagging_summary**
--------------------------------------------------

  Prints out the buther's bill, i.e. data flagging summary at the end of cross calibration process.

  **enable**

    *bool*, *optional*, *default = True*

    Execute printing flagging summary.

