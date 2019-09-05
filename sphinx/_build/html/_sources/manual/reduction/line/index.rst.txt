.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Spectral line imaging
=========================
 
.. toctree::
   :maxdepth: 1

**[relevant workers:** :ref:`image_HI`\ **]**

Spectral line imaging runs on a combination of custom software, CASA, WSclean, SunBlocker and SoFiA in order to subtract the continuum,
Doppler correct, flag solar RFI, create cleaned spectral line cubes and their moment images.
It can run on the input .MS
files or on .MS files created by MeerKATHI at various stages of the pipeline (e.g., by the :ref:`split_target` worker).
In the latter case the name of the .MS files to be flagged is based on that of the input .MS files, with a label
added before the extension. Users can set the label with the :ref:`image_HI: label <image_HI_label>` parameter in this worker.

The input .MS files may contain several targets. In this case, MeerKATHI makes one HI cube per target, using all
available visibilities for that target from all input .MS files. This worker does not mosaic single-target cubes together.

---------------------
Continuum subtraction
---------------------
 
Continuum subtraction might be necessary before imaging the spectral line of interest.
MeerKATHI can do this using two standard methods, which can be run sequentially within a single MeerKATHI run: i)
subtraction of the FT-ed continuum model components from the visibilities (:ref:`image_HI: subtractmodelcol <image_HI_subtractmodelcol>`);
and ii) fitting and subtracting polynomials from the individual real and imaginary visibility spectra (parameter *uvlin* in
:ref:`image_HI: mstransform <image_HI_mstransform>`).
A third standard method currently NOT implemented in MeerKATHI consists of fitting and subtracting polynomials from
individual image spectra in the data cube. This may be implemented in the future.

In practice, the first method consists of subtracting the MODEL_DATA column from the CORRECTED_DATA column
of the .MS files. MeerKATHI writes the resulting visibilities in the CORRECTED_DATA column itself.

**Users should therefore be aware that the CORRECTED_DATA column gets overwritten.**

The MODEL_DATA column contains the continuum model to be subtract. Within
MeerKATHI, the MODEL_DATA column should have been filled in with the continuum model resulting from the
continuum imaging and self-calibration done by the :ref:`self_cal` worker.

When running the second continuum subtraction method, which uses the CASA task MSTRANSFORM, users can select the order of the fit,
the channels that should be included in the fit, and the column that should be considered. This method writes a new file with an 'mst'
suffix appended to the file name. Subsequent steps of this worker can be instructed to run on the latter file.

------------------
Doppler correction
------------------

Doppler correction is performed with the CASA task MSTRANSFORM (parameter *doppler* in :ref:`image_HI: mstransform <image_HI_mstransform>`)
in the same run of this task used to perform continuum subtraction (see above). Users can select the telescope (choosing from a list
of available names, see parameter *telescope* in :ref:`image_HI: mstransform <image_HI_mstransform>`), as well the regridding mode (channel, frequency
or velocity), velocity type and output frame. Users can also set the frequency (or velocity, ...) grid they want to Doppler correct to, but
they can also let MeerKATHI fin the optimal one given the input files. In the latter case visibilities will be regridded to the largest
Doppler-corrected spectral interval common to all input .MS files, at the worse Doppler-corrected spectral resolution of them all.

------------------
Solar RFI flagging
------------------

MeerKATHI flags solar RFI using SunBlocker (:ref:`image_HI: sunblocker <image_HI_sunblocker>`).
The main idea of SunBlocker is that, because solar RFI is broadband, averaging visibilities in
frequency should enhance its detectability. However, the phase of solar RFI changes rapidly with frequency, leading to vectorial averages
with very low amplitude. In order to enhance the detectability of the Sun SunBlocker performs a scalar average instead. It does so in uv cells of the
visibility plane (i.e., on gridded visibilities). Once that is done, UV cells with anomalously high (scalar) average ampliude are flagged.
This method has been shown to work well on continuum-subtracted data. Users have control over some of the SunBlocker settings,
such as flagging threshold and gridding.

-------
Imaging
-------

Imaging is done with WSCLEAN.
