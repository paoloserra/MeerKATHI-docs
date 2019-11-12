.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _image_line:
 
==========================================
image_line
==========================================
 
.. toctree::
   :maxdepth: 1
 
Create HI data cube and detect sources therein



.. _image_line_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute segment image_line.



.. _image_line_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of names of MS data sets to be used. MS data set names will always start with the data set id, followed by a hyphen, followed by desc.



.. _image_line_line_name:

--------------------------------------------------
**line_name**
--------------------------------------------------

  *str*, *optional*, *default = HI*

  Line name string to be used for output file names.



.. _image_line_restfreq:

--------------------------------------------------
**restfreq**
--------------------------------------------------

  *str*, *optional*, *default = 1.420405752GHz*

  Rest frequency default value for this worker.



.. _image_line_subtractmodelcol:

--------------------------------------------------
**subtractmodelcol**
--------------------------------------------------

  Replace the column CORRECTED_DATA with the difference CORRECTED_DATA - MODEL_DATA. This is useful for continuum subtraction as it enables the subtraction of the most recent continuum clean model.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment subtractmodelcol.



.. _image_line_mstransform:

--------------------------------------------------
**mstransform**
--------------------------------------------------

  Perform UVLIN continuum subtraction and/or doppler tracking corrections

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment doppler correction.

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



.. _image_line_sunblocker:

--------------------------------------------------
**sunblocker**
--------------------------------------------------

  Use sunblocker to remove solar RFI. See description of sunblocker on github repository gigjozsa/sunblocker in method phazer of module sunblocker.py.

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment sunblocker.

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Execute sunblocker on continuum-subtracted data (otherwise use non-continuum-subtracted data).

  **imsize**

    *int*, *optional*, *default = 900*

    Image size (use the same as in wsclean_image or casa_image).

  **cell**

    *float*, *optional*, *default = 2.*

    Cell size in arcsec (use the same as in wsclean_image or casa_image).

  **threshold**

    *float*, *optional*, *default = 4.*

    Distance from average beyond which data are flagged in units of sigma.

  **vampirisms**

    *bool*, *optional*, *default = False*

    Apply only to data taken during day time.

  **uvmax**

    *float*, *optional*, *default = 2000*

    Maximum uvdistance in wavelength to be analysed.

  **uvmin**

    *float*, *optional*, *default = 0.*

    Minimum uvdistance in wavelength to be analysed.



.. _image_line_make_image:

--------------------------------------------------
**make_image**
--------------------------------------------------

  Image either with WSclean + SoFiA (for clean masks) or with Casa.

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment make_image.

  **image_with**

    *str*, *optional*, *default = wsclean*

    Choose whether to image with WSclean + SoFiA ("wsclean") or with Casa ("casa").

  **use_mstransform**

    *bool*, *optional*, *default = True*

    Image the .MS file(s) made by CASA MSTRANSFORM (continuum-subtracted and/or Doppler corrected).

  **pol**

    *str*, *optional*, *default = I*

    Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations).

  **spwid**

    *int*, *optional*, *default = 0*

    Spectral window to use.

  **nchans**

    *int*, *optional*, *default = 0*

    Number of channels of HI cube, 0 means all channels.

  **firstchan**

    *int*, *optional*, *default = 0*

    First channel of HI cube.

  **binchans**

    *int*, *optional*, *default = 1*

    Integer binning of channels.

  **npix**

    *seq*, *optional*, *default = 900 , 900*

    Image size in pixels. List of integers (width and height) or a single integer for square images.

  **cell**

    *float*, *optional*, *default = 2*

    Scale of a pixel. Default unit is arcsec, but can be specificied, e.g. 'scale 20asec'.

  **padding**

    *float*, *optional*, *default = 1.2*

    Images have initial size padding\*npix, and are later trimmed to npix.

  **weight**

    *str*, *optional*, *default = briggs*

    Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition.

  **robust**

    *float*, *optional*, *default = 0*

    Robust parameter in case of Briggs weighting.

  **taper**

    *float*, *optional*, *default = 0*

    Gaussian taper FWHM in arcsec. Zero means no tapering.

  **niter**

    *int*, *optional*, *default = 1000000*

    Maximum number of clean iterations to perform.

  **wscl_mgain**

    *float*, *optional*, *default = 1.0*

    WSclean gain for major iterations, Ratio of peak that will be subtracted in each major iteration.

  **wscl_sofia_niter**

    *int*, *optional*, *default = 2*

    Maximum number of WSclean + SoFiA iterations. The initial cleaning is done with WSclean automasking or with a user clean mask. Subsequent iterations use a SoFiA clean mask. A value of 1 means that WSclean is only executed once and SoFiA is not used.

  **wscl_sofia_converge**

    *float*, *optional*, *default = 1.1*

    Stop the WSclean + SoFiA iterations if the cube RMS has dropped by a factor < wscl_sofia_converge when comparing the last two iterations. If set to 0 then the maximum number of iterations is performed regardless of the noise change.

  **wscl_keep_final_products_only**

    *bool*, *optional*, *default = False*

    If set to true it deletes WSclean + Sofia intermediate cubes from the output directory, if set to false it keeps all the cubes of the WSclean + SoFiA iterations.

  **wscl_user_clean_mask**

    *str*, *optional*, *default = ' '*

    WSclean user clean mask for first WSclean + SoFiA iteration (give filename, to be located in the output/masking folder).

  **wscl_auto_mask**

    *float*, *optional*, *default = 10*

    WSclean option. Construct a mask from found components and when a threshold of sigma is reached, continue cleaning with the mask down to the normal threshold.

  **wscl_auto_threshold**

    *float*, *optional*, *default = 0.5*

    WSclean option. Auto clean threshold.

  **wscl_make_cube**

    *bool*, *optional*, *default = True*

    If set to true the output of WSclean is a data cube, if set to false the output is one fits file per spectral channel.

  **wscl_no_update_mod**

    *bool*, *optional*, *default = True*

    If set to true, WSclean will not store the line clean model in MODEL_DATA.

  **wscl_multi_scale**

    *bool*, *optional*, *default = False*

    Switch on WSclean multiscale cleaning.

  **wscl_multi_scale_scales**

    *list* *of int*, *optional*, *default = 0, 10, 20, 30*

    Scales of WSclean multiscale [0,10,20,etc, etc].

  **casa_threshold**

    *str*, *optional*, *default = 10mJy*

    Flux level to stop CASA cleaning, must include units, e.g. '1.0mJy'.

  **casa_port2fits**

    *bool*, *optional*, *default = False*

    Port CASA output to fits files.



.. _image_line_remove_stokes_axis:

--------------------------------------------------
**remove_stokes_axis**
--------------------------------------------------

  Remove Stokes axis from HI cube

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment.



.. _image_line_pb_cube:

--------------------------------------------------
**pb_cube**
--------------------------------------------------

  Make primary beam cube

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment.

  **apply_pb**

    *bool*, *optional*, *default = False*

    Whether to apply the primary beam correction to the image cube.



.. _image_line_freq_to_vel:

--------------------------------------------------
**freq_to_vel**
--------------------------------------------------

  Convert the spectral axis' header keys of the HI cube from frequency to velocity in the radio definition, v=c(1-obsfreq/restfreq). No change of spectra reference frame is performed.

  **enable**

    *bool*, *optional*, *default = False*

    Execute conversion.

  **reverse**

    *bool*, *optional*, *default = False*

    Perform the inverse transformation and change the cube 3rd axis from radio velocity to frequency.



.. _image_line_sofia:

--------------------------------------------------
**sofia**
--------------------------------------------------

  Run SoFiA source finder to produce a source mask and a Moment-0 map

  **enable**

    *bool*, *optional*, *default = True*

    Execute segment sofia?

  **rmsMode**

    *str*, *optional*, *default = mad*

    Method to determine rms ('mad' for using median absolute deviation, 'std' for using standard deviation, 'negative' for using Gaussian fit to negative voxels).

  **threshold**

    *float*, *optional*, *default = 4.0*

    SoFiA source finding threshold.

  **flag**

    *bool*, *optional*, *default = False*

    Use flag regions?

  **flagregion**

    *list* *of int*, *optional*, *default = 10, 10*

    Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...].

  **merge**

    *bool*, *optional*, *default = False*

    Use method to de-select and merge emission islands detected by any of SoFiA source finding algorithms. If turned on, pixels with a separation of less than mergeX pixels in x direction and less than mergeY pixels in y-direction and less than z pixels in z-direction will be merged and identified as a single object in the mask. Detections whose extent in x-direction is smaller than minSizeX, in y direction is smaller than minSizeY, and in z-direction is smaller than minSizeZ will be removed from the mask. Parameter merge determines if the merging should be applied.

  **mergeX**

    *int*, *optional*, *default = 2*

    Merge-'radius' in x-direction.

  **mergeY**

    *int*, *optional*, *default = 2*

    Merge-'radius' in y-direction.

  **mergeZ**

    *int*, *optional*, *default = 3*

    Merge-'radius' in z-direction (velocity direction).

  **minSizeX**

    *int*, *optional*, *default = 3*

    Minimum size in x-direction.

  **minSizeY**

    *int*, *optional*, *default = 3*

    Minimum size in y-direction.

  **minSizeZ**

    *int*, *optional*, *default = 3*

    Minimum size in y-direction.

  **do_cubelets**

    *bool*, *optional*, *default = True*

    Create cubelets of HI sources.

  **do_mom0**

    *bool*, *optional*, *default = True*

    Create moment 0 map.

  **do_mom1**

    *bool*, *optional*, *default = True*

    Create moment 1 map.



.. _image_line_sharpener:

--------------------------------------------------
**sharpener**
--------------------------------------------------

  Run sharpener to extract spectrum of all continuum sources against the lines of sight. The spectra are then plotted.

  **enable**

    *bool*, *optional*, *default = False*

    Execute sharpener?

  **catalog**

    *{"NVSS", "PYBDSF"}*, *optional*, *default = PYBDSF*

    Type of catalog to use (PYBDSF/NVSS).

  **channels_per_plot**

    *int*, *optional*, *default = 50*

    Number of channels to plot per detail plot.

  **thresh**

    *float*, *optional*, *default = 20*

    Threshold to select sources in online catalogs (mJy).

  **width**

    *str*, *optional*, *default = 1.0d*

    Field of view of output catalog (degrees).

  **label**

    *str*, *optional*, *default = ' '*

    Prefix label of plot names and titles.

