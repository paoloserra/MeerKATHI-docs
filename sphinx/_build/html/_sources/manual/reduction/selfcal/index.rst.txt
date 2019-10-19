.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
======================================
Continuum imaging and self-calibration
======================================
 
.. toctree::
   :maxdepth: 1
 
**[relevant workers:** :ref:`split_target`, :ref:`flagging`, :ref:`self_cal`\ **]**

-------------------------------------------
Split, average and flag target visibilities
-------------------------------------------

Following cross-calibration MeerKATHI creates a new .MS file which contains the
cross-calibrated target visibilities only. This is done by the :ref:`split_target`
worker. In case the cross-calibration tables have not been applied to the target
by the :ref:`cross_cal` worker, :ref:`split_target` can do so on the fly while
splitting using the CASA task MSTRANSFORM.

Optionally, the :ref:`split_target` worker can average in time and/or frequency
while splitting. Depending on the science goals, it might be useful to run this
worker more than once. E.g., the first time to create a frequency-averaged dataset
for continuum imaging and self-calibration, and the second time to create a
narrow-band dataset for spectral-line work. The possibility of running this
worker multiple times within a single MeerKATHI run allows users to design the
best strategy for their project.

Before self-calibrating it might also be good to flag the target's visibilities.
(Typically the target is not flagged before applying the cross-calibration.) This can
be done with the :ref:`flagging` worker (which was probably already run on the
calibrators' visibilities before cross-calibration) setting fields to target in
:ref:`flagging: autoflag_rfi <flagging_autoflag_rfi>`.

--------------------------------------
Image the continuum and self-calibrate
--------------------------------------

Having split, optionally averaged and flagged the target, it is now possible to
iteratively image the radio continuum emission and self-calibrate the visibilities.
The resulting gain tables and continuum model can also be transferred to another
.MS file (particularly useful for spectral line work). All this can be done with the
:ref:`self_cal` worker.

Several parameters allow users to set up both the imaging and self-calibration
according to their needs. Imaging is done with WSclean, and the parameters of this
imaging software are available in the :ref:`self_cal` worker. Calibration is done
with either Cubical or MeqTrees, and also in this case the :ref:`self_cal` worker
includes the parameters available in those packages.

Additional parameters allow users to decide how many calibration iterations to
perform through the parameter :ref:`self_cal: cal_niter  <self_cal_cal_niter>`.
For a value N, the code will create N+1 images following the sequence image1,
selfcal1, image2, selfcal2, ... imageN, selfcalN, imageN+1.

Optionally, users can enable :ref:`self_cal: aimfast  <self_cal_aimfast>`, which
at each new iteration compares the new continuum image with the previous one and
decides whether the image has improved significantly. In case it has not, no further
iterations are performed. In this case therefore :ref:`self_cal: cal_niter  <self_cal_cal_niter>`
is the maximum number of iterations.

**[missing a description of additional functionalities]**

-----------------------
Gain and model transfer
-----------------------
