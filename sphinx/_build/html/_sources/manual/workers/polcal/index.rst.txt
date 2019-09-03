.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _polcal:
 
==========================================
polcal
==========================================
 
.. toctree::
   :maxdepth: 1
 
Carry out crosshand calibration of the data (X and D) on boresight, after parallel hand calibration has been performed



.. _polcal_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute this segment.



.. _polcal_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = pol*

  Label for this worker and its associated datasets



.. _polcal_solve_uvdist:

--------------------------------------------------
**solve_uvdist**
--------------------------------------------------

  *str*, *optional*, *default = 100~100000000m*

  UV cutoff for solver. This should be large enough to wash out RFI



.. _polcal_preaverage_time:

--------------------------------------------------
**preaverage_time**
--------------------------------------------------

  *str*, *optional*, *default = 30s*

  Preaveraging time interval (like 30s) used in solving for X, D and plots



.. _polcal_preaverage_freq:

--------------------------------------------------
**preaverage_freq**
--------------------------------------------------

  *int*, *optional*, *default = 4*

  Preaveraging channel interval (like 4) used in solving for X, D and plots



.. _polcal_timesol_solfreqsel:

--------------------------------------------------
**timesol_solfreqsel**
--------------------------------------------------

  *str*, *optional*, *default = ' '*

  Subband selection to be used whenever solving for the DC component of either X or D. This could be picked to avoid RFI



.. _polcal_timesol_soltime:

--------------------------------------------------
**timesol_soltime**
--------------------------------------------------

  *str*, *optional*, *default = inf*

  Time solution interval to be used whenever solving for the DC component of either X or D



.. _polcal_freqsol_soltime:

--------------------------------------------------
**freqsol_soltime**
--------------------------------------------------

  *str*, *optional*, *default = inf*

  Time solution interval to be used when solving for per channel solutions for either X or D. This ought to be as long as possible



.. _polcal_feed_angle_rotation:

--------------------------------------------------
**feed_angle_rotation**
--------------------------------------------------

  *float*, *optional*, *default = -90.*

  Apply feed angle rotation matrix to all stations. MeerKAT X and Y feeds are flipped, so apply a -90 offset here



.. _polcal_do_dump_precalibration_leakage_reports:

--------------------------------------------------
**do_dump_precalibration_leakage_reports**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Write out report estimating residual quadrature leakages prior to crosshand calibration



.. _polcal_set_model:

--------------------------------------------------
**set_model**
--------------------------------------------------

  Predict model for calibrators into preaveraged dataset

  **enable**

    *bool*, *optional*, *default = True*

    Execute this segment.

  **meerkathi_model**

    *bool*, *optional*, *default = True*

    Use model, if available full-sky model, built into southern calibrators database, instead of any NRAO model

  **threads**

    *int*, *optional*, *default = 8*

    When predicting full sky model (lsm) use these many threads in MeqServer



.. _polcal_do_phaseup_crosshand_calibrator:

--------------------------------------------------
**do_phaseup_crosshand_calibrator**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Phaseup diagonal of calibrator that is used to calibrate crosshand phase prior to solving for slope and offset in crosshand phase



.. _polcal_do_solve_crosshand_slope:

--------------------------------------------------
**do_solve_crosshand_slope**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Solve for a frequency slope (X-Y digitizer delay) on the crosshand. This requires SNR on the crosshands.



.. _polcal_do_solve_crosshand_phase:

--------------------------------------------------
**do_solve_crosshand_phase**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Solve for an absolute phase on the crosshand, necessary for polarization angle measurements and to derotate U from V. This requires SNR on the crosshands.



.. _polcal_do_solve_leakages:

--------------------------------------------------
**do_solve_leakages**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Solve for leakages from I into U and V. If your calibrator polarization model for your flux scale reference is accurate this shouldalways be enabled.



.. _polcal_do_apply_XD:

--------------------------------------------------
**do_apply_XD**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Apply off-diagonal corrections



.. _polcal_do_dump_postcalibration_leakage_reports:

--------------------------------------------------
**do_dump_postcalibration_leakage_reports**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Write out report estimating residual quadrature leakages post crosshand calibration



.. _polcal_flagging_summary_crosshand_cal:

--------------------------------------------------
**flagging_summary_crosshand_cal**
--------------------------------------------------

  Summarize data flagged at the end of crosshand calibration

  **enable**

    *bool*, *optional*, *default = True*

    Execute this segment.

