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
:ref:`flagging: autoflag_rfi: <flagging_autoflag_rfi>`.
