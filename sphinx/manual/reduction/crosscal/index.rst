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

Cross-calibration runs largely on CASA tasks. Using these tasks, MeerKATHI allows users to
solve for delays, bandpass, gains and flux scale in several different ways.

Just as an example, it is possible to solve for:
1) time-independent antenna delays and normalised bandpass based on the observation of a
bandpass calibrator;
2) time-dependent antenna flux scale based on the observation of a flux calibrator;
3) time-dependent antenna gains based on the observation of a secondary calibrator;
4) time-dependent antenna flux scale at fine time resolution obtained by scaling the gains
from step 3 above to the gains from step 2 above.

Variations on the above scheme are possible by tuning the parameters of the various
steps. However, be aware that MeerKATHI does not check that the selected combination of
settings makes physical sense.

-----------------
Preliminary steps
-----------------

Before starting users can take the following optional steps.

* Set up a label which will be appended to all
  cross-calibration products (i.e., tables and plots; :ref:`cross_cal: label <cross_cal_label>`)
* Reinitialise the .MS for calibration with the CASA task CLEARCAL
  (:ref:`cross_cal: clear_cal <cross_cal_clear_cal>`). Given the users' field selection
  for this task (with the *field* parameter) MeerKATHI sets the MODEL_DATA column
  to unity in total intensity and zero in polarization, sets the
  CORRECTED_DATA column equal to the DATA column, and optionally adds a MODEL_DATA
  column if not already present. Selected fields can be specified with the field number or name
  as it appears in the metadata, or with the field code within MeerKATHI (typically "fcal", "bpcal";
  field codes are set by the :ref:`observation_config` worker).
  Multiple fields can be selected.
* Select the UV range that should be used to calibrate the data
  (:ref:`cross_cal: uvrange <cross_cal_uvrange>`). This can be useful, for example,
  to exclude short baselines from the calibration.
* Fill the MODEL_DATA column based on a calibrator model with the CASA task SETJY
  (:ref:`cross_cal: set_model <cross_cal_set_model>`). Various models are available
  and can be chosen using a number of additional parameters.
  For PKS 1934-638, users can choose a sky model which includes confusing
  sources and their spectral shape as seen through a frequency-dependent MeerKAT primary beam.
  This is recommended for MeerKAT observations. Alternatively, users can choose a point
  source model. When available, SARAO models are adopted. Alternatively, MeerKATHI uses the
  NRAO models.

-----------------
Delay calibration
-----------------

Antenna-based delay calibration is performed with the CASA task GAINCAL. It results in the creation of a
delay calibration table, which subsequent calibration steps can apply the on the fly (e.g., bandpass,
gain and flux calibration). In order to do this set :ref:`cross_cal: otfdelay <cross_cal_otfdelay>` to *true*.

In GAINCAL, the delay calibration is performed using only baselines with the reference antenna.
Therefore, the choice of reference antennas is very important. For example, reference antennas
involved in short baselines should probably be avoided. Also, care should be taken that the reference
antenna is not involved in heavily flagged baselines, as this could result in loss of a much larger
fraction of the array due to missing delay calibration.

The delay calibration options are set at :ref:`cross_cal: delay_cal <cross_cal_delay_cal>`.
Users can set the following parameters:

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI ("fcal", "bpcal", "gcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the delay calibration.
* Solution time interval (*solint*). Set this to 'inf' for time-independent delays. Note that for fully
  time-independent delays you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty string then data are not combined
  and at least one delay solution is calculated per observation, field, scan, spw (even for
  *solint="inf"*).
* Minimum S/N ratio (*minsnr*). No delay is calculated for solution intervals with a S/N ratio
  below this value.

Once a delay calibration has been obtaiend users can flag the data based on the delay solutions (*flag*).
This is done with the CASA task FLAGDATA.
For *mode="clip"* all visibilities with a delay outside the *clipminmax* range are flagged.
Other delay flagging modes are also available.

Finally, the solutions can be plotted (*plot*). Normally, all plotting options can be kept to their
default values.

--------------------
Bandpass calibration
--------------------

Antenna-based bandpass calibration is performed with the CASA tasks BANDPASS and, optionally, GAINCAL.
Its options are set at :ref:`cross_cal: bp_cal <cross_cal_bp_cal>`.
The following bandpass calibration options are similar to those for the delay calibration (see above):

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI (typically "bpcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the bandpass calibration.
* Solution time interval (*solint*). Set this to 'inf' for a time-independent bandpass. Note that for a fully
  time-independent bandpass you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty string then data are not combined
  and at least one bandpass solution is calculated per observation, field, scan (even for
  *solint="inf"*).
* Minimum S/N ratio (*minsnr*). No bandpass is calculated for solution intervals with a S/N ratio
  below this value.

Bandpass calibration has the following additional options:

* Minimum number of baselines (*minnrbl*). Given a solution interval, no bandpass is calculated for antennas
  with less baselines than this minimum number.
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
Setting this parameter to *true* results in the following three steps (instead of a single run of BANDPASS):

* A first run of BANDPASS with the solution interval set by *solint* and with *combine=""* (regardless of
  what users set *combine* to be). This results in a preliminary
  bandpass solution per observation, field, scan even for *solint="inf"*.
* A run of the the CASA task GAINCAL applying the above bandpass on the fly and solving for
  time-dependent antenna gains. The use of the preliminary bandpass ensures a good quality of the
  time-dependent gain calibration.
* A second run of BANDPASS with the solution interval set by *solint* and combining the data as
  requested by the user with *combine*. The above gain calibration is applied on the fly, resulting in
  a more accurate time-independent bandpass.

Finally, the solutions can be plotted (*plot*). Normally, all plotting options can be kept to their
default values.

----------------------
Flux scale calibration
----------------------

Antenna-based flux scale calibration is performed with the CASA task GAINCAL. Its options are set at
:ref:`cross_cal: gain_cal_flux <cross_cal_gain_cal_flux>`.

The flux scale calibration options are similar to those for the bandpass calibration (see above):

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI (typically "fcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the flux scale calibration.
* Solution time interval (*solint*). Set this to 'inf' for a time-independent calibration. Note that for a fully
  time-independent calibration you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty string then data are not combined
  and at least one flux scale solution is calculated per observation, field, scan, spw (even for
  *solint="inf"*).
* Minimum S/N ratio (*minsnr*). No flux scale calibration is calculated for solution intervals with a S/N ratio
  below this value.
* Minimum number of baselines (*minnrbl*). Given a solution interval, no flux scale calibration is calculated for
  antennas with less baselines than this minimum number.
* Whether to set the reference antenna to the value given in the :ref:`observation_config` worker
  (*set_refant*). If *false* then CASA GAINCAL will decide which reference antenna to use.

Finally, the solutions can be plotted (*plot*). Normally, all plotting options can be kept to their
default values.

----------------
Gain calibration
----------------

Antenna-based gain calibration is performed with the CASA task GAINCAL. Its options are set at
:ref:`cross_cal: gain_cal_gain <cross_cal_gain_cal_gain>`.

The gain scale calibration options are identical to those for the flux calibration (see above):

* Field to use (*field*). This can be the field number or name as it appears in the metadata, or the
  field code within MeerKATHI (typically "gcal"; field codes are set by the :ref:`observation_config`
  worker). Multiple fields can be used for the gain calibration.
* Solution time interval (*solint*). Set this to 'inf' for a time-independent calibration. Note that for a fully
  time-independent calibration you may need to set the *combine* option below to an appropriate value.
* Whether and how to combine the data (*combine*). If this is an empty string then data are not combined
  and at least one gain solution is calculated per observation, field, scan, spw (even for
  *solint="inf"*). This is probably the mode of interest in most cases.
* Minimum S/N ratio (*minsnr*). No gain calibration is calculated for solution intervals with a S/N ratio
  below this value.
* Minimum number of baselines (*minnrbl*). Given a solution interval, no gain calibration is calculated for
  antennas with less baselines than this minimum number.
* Whether to set the reference antenna to the value given in the :ref:`observation_config` worker
  (*set_refant*). If *false* then CASA GAINCAL will decide which reference antenna to use.

Finally, the gain solutions can be plotted (*plot*). Normally, all plotting options can be kept to their
default values.

------------------------
Flux scale bootstrapping
------------------------

Typically, the calibrator used for the flux scale calibration above is observed at low cadence. This
results in a coarse time resolution (if any) for the flux calibration. Higher resolution mapping
of the variation of the gain amplitude with time might be provided by the gain calibration step above,
which is based on the typically more frequent observation of a gain calibrator.
These gain amplitudes do not give a reliable, absolute flux scale, but can be scaled to the gain
amplitudes obtained from the flux calibrator. Within MeerKATHI, this step is performed with the CASA
task FLUXSCALE. Its options are set at :ref:`cross_cal: transfer_fluxscale <cross_cal_transfer_fluxscale>`.

The only availabel options are the field(s) from which the flux scale was derived (*reference*) and those
whose gains should be scaled (*transfer*). As for all other steps above, fields can be specified
with the field number or name as it appears in the metadata, or the field code within MeerKATHI. Typically
this will be *reference="fcal"* and *transfer="gcal"*.

The CASA FLUXSCALE algorithm works initially on each antenna and each polarisation product separately.
It calculates the ratio *R* ( *i* , *x* ) between the time-averaged gain amplitude derived from the flux calibrator
and the time-averaged gain amplitude derived from the gain calibrator for antenna *i* and polarisation product *x*.
This results in *N* (ant) x *N* (pol) values of the ratio *R* ( *i* , *x* ). The algorithm then takes the median of all such values,
*F* = MEDIAN[ *R* ( *i* , *x* )]. Finally, all values of the gain amplitude derived from the gain calibrator for all antennas
and polarisation products are multiplied by *F*. This means that the bootstrapping is done globally for the array
as a whole, and not individually for each antenna and each polarisation product.

The final flux scale solutions can be plotted (*plot*). Normally, all plotting options can be kept to their
default values.

---------------------------
Apply the cross-calibration
---------------------------

MeerKATHI can apply the cross calibration tables to all calibrators (useful for diagnostics) and to the science
target. In doing so it will use the following interpolation rules:

* Delay calibration: applied to the fields bpcal, gcal, target with nearest, linear, linear interpolation, respectively.
* Bandpass calibration: applied to the fields bpcal, gcal, target with nearest, linear, linear interpolation, respectively.
* Gain calibration before bootstrapping the flux scale: applied to the fields bpcal, gcal, target
  with linear, linear, linear interpolation, respectively.
* Gain calibration after bootstrapping the flux scale: applied to the fields bpcal, gcal, target
  with linear, nearest, linear interpolation, repsectively.

**[missing from this page: flag on closure errors and flag statistics]**
