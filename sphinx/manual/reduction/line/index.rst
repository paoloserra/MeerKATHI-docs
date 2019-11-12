.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Spectral line imaging
=========================
 
.. toctree::
   :maxdepth: 1

**[relevant workers:** :ref:`image_line`\ **]**

Spectral line imaging runs on a combination of custom software, CASA, WSclean, SunBlocker and SoFiA in order to subtract the continuum,
Doppler correct, flag solar RFI, create cleaned spectral line cubes and moment images.
It can run on the input .MS files or on .MS files created by MeerKATHI at various stages of the pipeline
(e.g., by the :ref:`split_target` worker). In the latter case the name of the .MS files to be imaged is based on that of the input .MS files,
with a label added before the extension. Users can set the label with the :ref:`image_line: label <image_line_label>` parameter in this worker.

The input .MS files may contain several targets. In this case, MeerKATHI makes one HI cube per target, using all
available visibilities for that target from all input .MS files. This worker does not mosaic line cubes made for different targets.

---------------------
Continuum subtraction
---------------------
 
Continuum subtraction might be necessary before imaging the spectral line of interest.
MeerKATHI can do this using two standard methods, which can be run sequentially within a single MeerKATHI run: i)
subtraction of the continuum model visibilities from the field visibilities (:ref:`image_line: subtractmodelcol <image_line_subtractmodelcol>`);
and ii) fitting and subtracting polynomials from the individual real and imaginary visibility spectra (parameter *uvlin* in
:ref:`image_line: mstransform <image_line_mstransform>`).
A third standard method currently NOT implemented in MeerKATHI consists of fitting and subtracting polynomials from
individual image spectra in the data cube. This may be implemented in the future.

In practice, the first method consists of subtracting the MODEL_DATA column from the CORRECTED_DATA column
of the .MS files. MeerKATHI writes the resulting visibilities in the CORRECTED_DATA column itself.

**Users should therefore be aware that the CORRECTED_DATA column gets overwritten.**

The MODEL_DATA column contains the continuum model to be subtracted. Within
MeerKATHI, the MODEL_DATA column should have been filled in with the continuum model resulting from the
continuum imaging and self-calibration done by the :ref:`self_cal` worker.

When running the second continuum subtraction method, which uses the CASA task MSTRANSFORM, users can select the order of the fit,
the channels that should be included in the fit, and the column that should be considered. This method writes a new file with an 'mst'
suffix appended to the file name. Subsequent steps of this worker can be instructed to run on the file written by MSTANSFORM.

------------------
Doppler correction
------------------

Doppler correction is performed with the CASA task MSTRANSFORM (parameter *doppler* in :ref:`image_line: mstransform <image_line_mstransform>`)
in the same run of this task used to perform continuum subtraction (see above). Users can select the telescope (choosing from a list
of available names, see parameter *telescope* in :ref:`image_line: mstransform <image_line_mstransform>`), as well the regridding mode (channel, frequency
or velocity), velocity type and output frame. Users can also set the frequency (or velocity, ...) grid they want to Doppler correct to, but
they can also let MeerKATHI fin the optimal one given the input files. In the latter case, visibilities will be regridded to the widest
Doppler-corrected spectral interval common to all input .MS files, at the worse Doppler-corrected spectral resolution of them all.

------------------
Solar RFI flagging
------------------

MeerKATHI flags solar RFI using SunBlocker (:ref:`image_line: sunblocker <image_line_sunblocker>`).
The main idea of SunBlocker is that, because solar RFI is broadband, averaging visibilities in
frequency should enhance its detectability. However, the phase of solar RFI changes rapidly with frequency, leading to vectorial averages
with very low amplitude. In order to enhance the detectability of the solar RFI SunBlocker performs a scalar average. It does so in uv cells of the
visibility plane (i.e., on gridded visibilities). Once that is done, UV cells with anomalously high (scalar) average ampliude are flagged.
This method has been shown to work well on continuum-subtracted data. Users have control over some of the SunBlocker settings,
such as flagging threshold and gridding. It is also possible to run this task on day-time data only.

-------
Imaging
-------

Spectral line imaging is done with WSCLEAN. This software produces a set of individual .FITS images per channel (i.e.,
dirty image, psf, clean model, restored image), and when that is done MeerKATHI stacks them all together in .FITS image cubes.
Cleaning is done iteratively by making a first cube using WSClean algorithms for a blind clean, then making a clean mask with SoFiA and
running WSClean again with that clean mask, and so on. Users can let MeerKATHI continue iterating until the noise in the residual cube
converges (up to a maximum number of iterations) or perform a fixed number of iterations ignoring noise convergence. Users also have full
control of all WSCLEAN imaging parameters.

Imaging can also been done in CASA, but this has not received as much attention as WSCLEAN imaging and may be obsolete.

Several additional steps are availabel and can be run once the .FITS image cubes are ready. This includes removing the trivial Stokes axis
from the cubes, convert the frequency axis from frequency to velocity, and create a primary beam cube on the same WCS grid of the image cube.
At the moment the primary beam cube is calculated assuming a Gaussian primary beam with FWHM = 1.02 * lightspeed / frequency / dishdiameter.

As a final step, MeerKATHI can run SoFiA in order to make a line detection mask and the corresponding moment images. Users have control
over several (but not all) SoFiA settings.

-----------
Diagnostics
-----------

As a useful diagnostic, MeerKATHI can run SHARPENER, which extracts 1D spectra at the position of bright continuum sources in the field.
This is helpful to assess the quality of the continuum subtraction. It can also create one last flagging summary.
