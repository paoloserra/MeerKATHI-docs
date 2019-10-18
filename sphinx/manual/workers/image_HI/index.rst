.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _image_HI:
 
==========================================
image_HI
==========================================
 
.. toctree::
   :maxdepth: 1
 
Create HI data cube and detect sources therein



.. _image_HI_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute segment image_HI (yes/no).



.. _image_HI_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of names of MS data sets to be used. MS data set names will always start with the data set id, followed by a hyphen, followed by desc.



.. _image_HI_restfreq:

--------------------------------------------------
**restfreq**
--------------------------------------------------

  *str*, *optional*, *default = 1.420405752GHz*

  Rest frequency default value for this worker.



.. _image_HI_npix:

--------------------------------------------------
**npix**
--------------------------------------------------

  *list* *of int*, *optional*, *default = 900*

  Default number of pixels (wherever npix is requested) in this worker. List of integers (width and height) or a single integer for square images.



.. _image_HI_cell:

--------------------------------------------------
**cell**
--------------------------------------------------

  *float*, *optional*, *default = 2*

  Default scale of a pixel in arcsec.



.. _image_HI_weight:

--------------------------------------------------
**weight**
--------------------------------------------------

  *str*, *optional*, *default = briggs*

  Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition.



.. _image_HI_robust:

--------------------------------------------------
**robust**
--------------------------------------------------

  *float*, *optional*, *default = 0*

  Default robust parameter in case of Briggs weighting.



.. _image_HI_subtractmodelcol:

--------------------------------------------------
**subtractmodelcol**
--------------------------------------------------

  Replace the column CORRECTED_DATA with the difference CORRECTED_DATA - MODEL_DATA. This is useful for continuum subtraction as it enables the subtraction of the most recent continuum clean model.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment subtractmodelcol.



.. _image_HI_mstransform:

--------------------------------------------------
**mstransform**
--------------------------------------------------

  Perform UVLIN continuum subtraction and/or doppler tracking corrections

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment doppler correction (yes/no).

  **telescope**

    *{"meerkat", "vla", "gmrt", "wsrt", "atca", "askap"}*, *optional*, *default = meerkat*

    The name of the telescope from which observations were made. Default is the 'meerkat' telescope. Current options are gmrt, vla, wsrt, atca.

  **doppler**

    *bool*, *optional*, *default = True*

    Transform channel labels and visibilities to a different spectral reference frame.

  **mode**

    *str*, *optional*, *default = frequency*

    Regridding mode (channel/velocity/frequency/channel_b).

  **outframe**

    *{"", "topo", "geo", "lsrk", "lsrd", "bary", "galacto", "lgroup", "cmb", "source"}*, *optional*, *default = bary*

    Output reference frame, options '', 'topo', 'geo', 'lsrk', 'lsrd', 'bary', 'galacto', 'lgroup', 'cmb', 'source'

  **veltype**

    *str*, *optional*, *default = radio*

    Definition of velocity (as used in mode), radio or optical.

  **outchangrid**

    *str*, *optional*, *default = auto*

    Output channel grid for Doppler correction. Default is 'auto', and the pipeline will calculate the appropriate channel grid. If not 'auto' it must be in the format 'nchan,chan0,chanw' where nchan is an integer, and chan0 and chanw must include units appropriate for the chosen mode (see parameter 'mode' above)

  **uvlin**

    *bool*, *optional*, *default = True*

    Perform continuum subtraction as in task uvcontsub whilst regridding within mstransform.

  **fitspw**

    *str*, *optional*, *default = ' '*

    Spectral window channel selection for fitting the continuumSelection of line-free channels using CASA syntax (e.g. '0:0~100;150:300'). If set to null, a fit to all unflagges visibilities will be performed.

  **fitorder**

    *int*, *optional*, *default = 1*

    Polynomial order for the continuum fits

  **column**

    *str*, *optional*, *default = corrected*

    Data column to use.

  **obsinfo**

    *bool*, *optional*, *default = True*

    Create obsinfo.txt and obsinfo.json of MS file created by mstransform.



.. _image_HI_sunblocker:

--------------------------------------------------
**sunblocker**
--------------------------------------------------

  Use sunblocker to remove solar RFI. See description of sunblocker on github repository gigjozsa/sunblocker in method phazer of module sunblocker.py.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment sunblocker (yes/no). Default is yes.

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Execute sunblocker on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

  **imsize**

    *int*, *optional*, *default = 900*

    Image size (use the same as in wsclean_image or casa_image). Default is worker npix

  **cell**

    *float*, *optional*, *default = 2.*

    Cell size in arcsec (use the same as in wsclean_image or casa_image). Default is worker cell

  **threshold**

    *float*, *optional*, *default = 4.*

    Distance from average beyond which data are flagged in units of sigma. Default is 4.

  **vampirisms**

    *bool*, *optional*, *default = False*

    Apply only to data taken during day time (defaults to true)

  **uvmax**

    *float*, *optional*, *default = 2000*

    Maximum uvdistance in wavelength to be analysed (defaults to 2000)

  **uvmin**

    *float*, *optional*, *default = 0.*

    Minimum uvdistance in wavelength to be analysed (defaults to 0)



.. _image_HI_wsclean_image:

--------------------------------------------------
**wsclean_image**
--------------------------------------------------

  Use WSClean to create line data cube. See WSclean wiki on sourceforge.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment wsclean_image (yes/no). Default is yes.

  **wscl_niter**

    *int*, *optional*, *default = 2*

    Maximum number of rewsclean iterations to perform. Default is 2

  **tol**

    *float*, *optional*, *default = 3.*

    Relative change in the noise.

  **rm_intcubes**

    *bool*, *optional*, *default = False*

    If set to true it deletes intermediate cubes from the output directory, if set to false it keeps all the cubes from the wsclean loops

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Execute wsclean_image on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

  **pol**

    *str*, *optional*, *default = I*

    Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations). Default is I.

  **spwid**

    *int*, *optional*, *default = 0*

    Spectral window to use. Default is 0.

  **nchans**

    *int*, *optional*, *default = 0*

    Number of channels of HI cube, 0 means all channels.

  **firstchan**

    *int*, *optional*, *default = 0*

    First channel of HI cube. Default is 0.

  **binchans**

    *int*, *optional*, *default = 1*

    Integer binning of channels. Default is 1 (no binning).

  **npix**

    *seq*, *optional*, *default = 900 , 900*

    Image size in pixels. List of integers (width and height) or a single integer for square images. Default is Worker default for npix.

  **padding**

    *float*, *optional*, *default = 1.2*

    Images have initial size padding\*npix, and are later trimmed to npix. Default is 1.2.

  **mgain**

    *float*, *optional*, *default = 1.0*

    Cleaning gain for major iterations, Ratio of peak that will be subtracted in each major iteration. Default is 0.9.

  **cell**

    *float*, *optional*, *default = 2*

    Scale of a pixel. Default unit is arcsec, but can be specificied, e.g. 'scale 20asec'. Default is Worker default for cell.

  **weight**

    *str*, *optional*, *default = briggs*

    Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition. Default is Worker default for weight.

  **robust**

    *float*, *optional*, *default = 0*

    Robust parameter in case of Briggs weighting. Default is 2.

  **taper**

    *float*, *optional*, *default = 0*

    Gaussian taper FWHM in arcsec. Default is 0, no tapering.

  **niter**

    *int*, *optional*, *default = 1000000*

    Maximum number of clean iterations to perform. Default is 1000000.

  **ownfitsmask**

    *str*, *optional*, *default = ' '*

    filename of fits mask (in output/masking folder)

  **auto_mask**

    *float*, *optional*, *default = 10*

    Construct a mask from found components and when a threshold of sigma is reached, continue cleaning with the mask down to the normal threshold.

  **auto_threshold**

    *float*, *optional*, *default = 0.5*

    Auto clean threshold

  **cleanborder**

    *float*, *optional*, *default = 0*

    Set the border size in which no cleaning is performed, in percentage of the width/height of a plane. With an plane size of 1000 pixels and clean border of 1%, each border is 10 pixels. Default is 0.

  **make_cube**

    *bool*, *optional*, *default = True*

    If set to true the output is a data cube, if set to false the output is one fits file per spectral channel. Default is yes.

  **no_update_mod**

    *bool*, *optional*, *default = True*

    If set to true, will not store the clean model in MODEL_DATA. Relevant for HI.

  **multi_scale**

    *bool*, *optional*, *default = False*

    switch on multiscale cleaning

  **multi_scale_scales**

    *list* *of int*, *optional*, *default = 0, 10, 20, 30*

    scales of multiscale [0,10,20,etc, etc]



.. _image_HI_casa_image:

--------------------------------------------------
**casa_image**
--------------------------------------------------

  Use CASA to create line data cube.

  **enable**

    *bool*, *optional*, *default = False*

  **use_mstransform**

    *bool*, *optional*, *default = False*

    Execute wsclean_image on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

  **pol**

    *str*, *optional*, *default = I*

    Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations). Default is I.

  **taper**

    *str*, *optional*, *default = 0*

    uvtaper as in casa clean either in arcsec of klambda.

  **spwid**

    *int*, *optional*, *default = 0*

    Spectral window to use. Default is 0.

  **nchans**

    *int*, *optional*, *default = 0*

    Number of channels of HI cube, 0 means all channels.

  **firstchan**

    *int*, *optional*, *default = 0*

    First channel of HI cube. Default is 0.

  **binchans**

    *int*, *optional*, *default = 1*

    Integer binning of channels. Default is 1 (no binning).

  **npix**

    *seq*, *optional*, *default = 900, 900*

    Image size in pixels. List of integers (width and height) or a single integer for square images. Default is worker npix.

  **cell**

    *float*, *optional*, *default = 2*

    Scale of a pixel. Default unit is arcsec, but can be specificied, e.g. 'scale 20asec'. Default is worker cell.

  **weight**

    *str*, *optional*, *default = briggs*

    Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition. Default is worker weight.

  **robust**

    *float*, *optional*, *default = 0.0*

    Robust parameter in case of Briggs weighting. Default is worker robust.

  **niter**

    *int*, *optional*, *default = 1000000*

    Maximum number of clean iterations to perform. Default is 1000000.

  **threshold**

    *str*, *optional*, *default = 10mJy*

    Flux level to stop cleaning, must include units, e.g. '1.0mJy'. Default is '10mJy'.

  **port2fits**

    *bool*, *optional*, *default = False*

    Port output to fits files if yes. Default is yes.



.. _image_HI_remove_stokes_axis:

--------------------------------------------------
**remove_stokes_axis**
--------------------------------------------------

  Remove Stokes axis from HI cube

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment. Default is true



.. _image_HI_pb_cube:

--------------------------------------------------
**pb_cube**
--------------------------------------------------

  Make primary beam cube

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment. Default is false

  **apply_pb**

    *bool*, *optional*, *default = False*

    Whether to apply the primary beam correction to the image cube. Default is false



.. _image_HI_freq_to_vel:

--------------------------------------------------
**freq_to_vel**
--------------------------------------------------

  Convert the spectral axis' header keys of the HI cube from frequency to velocity in the radio definition, v=c(1-obsfreq/restfreq). No change of spectra reference frame is performed.

  **enable**

    *bool*, *optional*, *default = False*

    Execute conversion. Default is true

  **reverse**

    *bool*, *optional*, *default = False*

    Perform the inverse transformation and change the cube 3rd axis from velocity to frequency. Default is false.



.. _image_HI_sofia:

--------------------------------------------------
**sofia**
--------------------------------------------------

  Run SoFiA source finder to produce a source mask and a Moment-0 map

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment sofia (yes/no)? Default is yes.

  **rmsMode**

    *str*, *optional*, *default = mad*

    Method to determine rms ('mad' for using median absolute deviation, 'std' for using standard deviation, 'negative' for using Gaussian fit to negative voxels). Default is 'mad'

  **threshold**

    *float*, *optional*, *default = 4.0*

    SoFiA source finding threshold. Default is 4.0.

  **flag**

    *bool*, *optional*, *default = False*

    Use flag regions (yes/no)? Default is no.

  **flagregion**

    *list* *of int*, *optional*, *default = 10, 10*

    Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...]. Default is [].

  **merge**

    *bool*, *optional*, *default = False*

    Use method to de-select and merge emission islands detected by any of SoFiA source finding algorithms. If turned on, pixels with a separation of less than mergeX pixels in x direction and less than mergeY pixels in y-direction and less than z pixels in z-direction will be merged and identified as a single object in the mask. Detections whose extent in x-direction is smaller than minSizeX, in y direction is smaller than minSizeY, and in z-direction is smaller than minSizeZ will be removed from the mask. Parameter merge determines if the merging should be applied (yes/no). Default is yes.

  **mergeX**

    *int*, *optional*, *default = 2*

    Merge-'radius' in x-direction. Default is 2

  **mergeY**

    *int*, *optional*, *default = 2*

    Merge-'radius' in y-direction. Default is 2

  **mergeZ**

    *int*, *optional*, *default = 3*

    Merge-'radius' in z-direction (velocity direction). Default is 3

  **minSizeX**

    *int*, *optional*, *default = 3*

    Minimum size in x-direction. Default is 3.

  **minSizeY**

    *int*, *optional*, *default = 3*

    Minimum size in y-direction. Default is 3.

  **minSizeZ**

    *int*, *optional*, *default = 3*

    Minimum size in y-direction. Default is 5.

  **do_cubelets**

    *bool*, *optional*, *default = True*

    Create cubelets of HI sources.

  **do_mom0**

    *bool*, *optional*, *default = True*

    Create moment 0 map.

  **do_mom1**

    *bool*, *optional*, *default = True*

    Create moment 1 map.



.. _image_HI_sharpener:

--------------------------------------------------
**sharpener**
--------------------------------------------------

  Run sharpener to extract spectrum of all continuum sources against the lines of sight. The spectra are then plotted.

  **enable**

    *bool*, *optional*, *default = False*

    Execute sharpener (yes/no)? Default is yes

  **catalog**

    *{"NVSS", "PYBDSF"}*, *optional*, *default = PYBDSF*

    Type of catalog to use (PYBDSF/NVSS). Default is 'PYBDSF'

  **channels_per_plot**

    *int*, *optional*, *default = 50*

    Number of channels to plot per detail plot. Default is 50

  **thresh**

    *float*, *optional*, *default = 20*

    Threshold to select sources in online catalogs (mJy). Default is '20'

  **width**

    *str*, *optional*, *default = 1.0d*

    Field of view of output catalog (degrees). Default is '1.0d'

  **label**

    *str*, *optional*, *default = ' '*

    Prefix label of plot names and titles. Default is 'pipeline.prefix'



.. _image_HI_flagging_summary:

--------------------------------------------------
**flagging_summary**
--------------------------------------------------

  Print out flagging summary.

  **enable**

    *bool*, *optional*, *default = False*

    Execute printing flagging summary.

