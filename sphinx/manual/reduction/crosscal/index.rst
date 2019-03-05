.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Cross-calibration
=========================
 
.. toctree::
   :maxdepth: 1
 
**[relevant workers:** :ref:`cross_cal`, :ref:`inspect_data`\ **]**

Cross-calibration runs largely on CASA tasks. MeerKATHI allows users to solve for
delays, bandpass, gains and flux scale in several different ways.

-----------------
Preliminary steps
-----------------

Before starting users can take the following optional steps.

* Set up a label which will be appended to all
  cross-calibration products (i.e., tables and plots; :ref:`cross_cal: label <cross_cal_label>`)
* Clear any existing calibration and initialise the .MS for
  calibration (:ref:`cross_cal: clear_cal <cross_cal_clear_cal>`).
* Select the UV range that should be used to calibrate the data
  (:ref:`cross_cal: uvrange <cross_cal_uvrange>`). This can be useful, for example,
  to exclude short baselines from the calibration.
* Fill the MODEL_DATA column based on a calibrator model
  (:ref:`cross_cal: set_model <cross_cal_set_model>`). Additional
  options allow users to use a model of the PKS 1934-638 field which includes confusing
  sources and their spectral shape as seen through a frequency-dependent MeerKAT primary beam.

-----------------
Delay calibration
-----------------

Delay calibration is performed with the CASA task GAINCAL and results in the creation of a
delay calibration table. Subsequent calibration steps (e.g., bandpass, gain and flux calibration)
can apply the delay calibration table on the fly. This is achieved by setting
:ref:`cross_cal: otfdelay <cross_cal_otfdelay>` to *true*.

In GAINCAL, the delay calibration is performed using only baselines with the reference antenna.
The choice of reference antennas is therefore very important. For examples, reference antennas
involved in short baselines should probably be avoided.

The delay calibration options are set at :ref:`cross_cal: delay_cal <cross_cal_delay_cal>`.
Users can set the following parameters:

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI ("fcal", "bpcal", "gcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the delay calibration.
* Solution interval (*solint*). Set this to 'inf' for time-independent delays. Note that for fully
  time-independent delays you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty strings then data are not combined
  and at least one delay solution is calculated per observation, field, scan, spw (even for
  *solint="inf"*).
* Minimum S/N ratio (*minsnr*). No delay is calculated for solution intervals with a S/N ratio
  below this value.

Once a delay calibration has been obtaiend users can flag the data based on the delay solutions (*flag*).
This is done with the CASA task FLAGDATA.
For *mode="clip"* all visibilities with a delay outside the *clipminmax* range are flagged.
Other delay flagging modes are also available.

Finally, the solutions can be plotted (*plot*). Normally all plotting options should be left to their
default values.

--------------------
Bandpass calibration
--------------------

Bandpass calibration is performed with the CASA tasks BANDPASS and, optionally, GAINCAL.
Its options are set at :ref:`cross_cal: bp_cal <cross_cal_bp_cal>`.
The following bandpass calibration options are similar to those for the delay calibration (see above):

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI (typically "bpcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the bandpass calibration.
* Solution interval (*solint*). Set this to 'inf' for a time-independent bandpass. Note that for a fully
  time-independent bandpass you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty strings then data are not combined
  and at least one bandpass solution is calculated per observation, field, scan (even for
  *solint="inf"*).
* Minimum S/N ratio (*minsnr*). No bandpass is calculated for solution intervals with a S/N ratio
  below this value.

Bandpass calibration has the following additional options:

* Minimum number of baselines (*minnrbl*). No bandpass is calculated for solution intervals
  with less antennas than this minimum number.
* Whether to set the reference antenna to the value given in the :ref:`observation_config` worker
  (*set_refant*). If *false* then CASA BANDPASS will decide which reference antenna to use.
* Whether to normalise the bandpass to have average amplitude and phase of 1 and 0, repsectively (*solnorm*).

MeerKATHI can calibrate the bandpass with the above options in a single run of the CASA task BANDPASS.
However, a single run of BANDPASS may not be ideal when calculating a time-independent bandpass from
calibrator scans spread over a long time interval.
This is because the vector time-average of the calibrator's raw visibilities, which is calculated
before solving for the time-independent bandpass, may be corrupted by the variation of
the antenna gains with time. In this case it is better to correct for such gain variations *before* 
time-averaging the calibrator's visibilities and calculating the time-independent bandpass.
MeerKATHI allows users to do this through the parameter *remove_ph_time_var*.
Setting this parameter to *true* results in the following thress steps (instead of a single run of BANDPASS):

* A first run of BANDPASS with the solution interval set by *solint* and with *combine=""* (regardless of
  what users set *combine* to be). This results in a preliminary
  bandpass solution per observation, field, scan even for *solint="inf"*.
* A run of the the CASA task GAINCAL applying the above bandpass on the fly and solving for
  time-dependent antenna gains. The use of the preliminary bandpass ensures a good quality of the
  time-dependent gain calibration.
* A second run of BANDPASS with the solution interval set by *solint* and combining the data as
  requested by the user with *combine*. The above gain calibration is applied on the fly, resulting in
  a more accurate time-independent bandpass.

Finally, the solutions can be plotted (*plot*). Normally all plotting options should be left to their
default values.

----------------------
Flux scale calibration
----------------------

TBD

----------------
Gain calibration
----------------

TBD

------------------------
Flux scale bootstrapping
------------------------

TBD

--------------
Closure errors
--------------

TBD
