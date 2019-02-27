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



-------------------------------------
**enable**
-------------------------------------

  *bool*, *optional*

  Execute segment image_HI (yes/no). Default is yes.



-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Order in queue of workers. Default is 11.



-------------------------------------
**label**
-------------------------------------

  *str*, *optional*

  Label of names of MS data sets to be used. MS data set names will always start with the data set id, followed by a hyphen, followed by desc. Default is corr.



-------------------------------------
**hires_label**
-------------------------------------

  *str*

  Label of names of High frequency resolution MS data sets to be used. MS data set names will always start with the data set id, followed by a hyphen, followed by desc. Default is hires.



-------------------------------------
**use_hires_data**
-------------------------------------

  *bool*, *optional*

  Make use of high resolution data for HI imaging



-------------------------------------
**restfreq**
-------------------------------------

  *str*, *optional*

  Rest frequency default value for this worker. Default is '1.420405752GHz'.



-------------------------------------
**npix**
-------------------------------------

  *optional*

  Default number of pixels (wherever npix is requested) in this worker. List of integers (width and height) or a single integer for square images. Default is 1024.



-------------------------------------
**cell**
-------------------------------------

  *float*, *optional*

  Default scale of a pixel in arcsec. Default is 7.



-------------------------------------
**weight**
-------------------------------------

  *str*, *optional*

  Default weight for the worker. Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition. Default is natural.



-------------------------------------
**robust**
-------------------------------------

  *float*, *optional*

  Default robust parameter in case of Briggs weighting. Default is 2.



-------------------------------------
**subtractmodelcol**
-------------------------------------

  Replace the column CORRECTED_DATA with the difference CORRECTED_DATA - MODEL_DATA. This is useful for continuum subtraction as it enables the subtraction of the most recent continuum clean model.

    **enable**
      *bool*, *optional*

      Execute segment subtractmodelcol. Default is False.



-------------------------------------
**mstransform**
-------------------------------------

  Perform UVLIN continuum subtraction and/or doppler tracking corrections

    **enable**
      *bool*, *optional*

      Execute segment doppler correction (yes/no). Default is yes.

    **telescope**
      *str*, *optional*

      The name of the telescope from which observations were made. Default is the 'meerkat' telescope. Current options are gmrt, vla, wsrt, atca

    **doppler**
      *bool*, *optional*

      Transform channel labels and visibilities to a different spectral reference frame. default is True

    **mode**
      *str*, *optional*

      Regridding mode (channel/velocity/frequency/channel_b). Default is 'frequency'

    **outframe**
      *str*, *optional*

      Output reference frame, options 'LSRK', 'LSRD', 'BARY', 'GALACTO', 'LGROUP', 'CMB', 'GEO', 'TOPO'. Defaut is 'BARY'

    **veltype**
      *str*, *optional*

      Definition of velocity (as used in mode), radio or optical.  Default is 'radio'

    **outchangrid**
      *str*, *optional*

      Output channel grid for Doppler correction. Default is 'auto', and the pipeline will calculate the appropriate channel grid. If not 'auto' it must be in the format 'nchan,chan0,chanw' where nchan is an integer, and chan0 and chanw must include units appropriate for the chosen mode (see parameter 'mode' above)

    **uvlin**
      *bool*, *optional*

      Perform continuum subtraction as in task uvcontsub whilst regridding within mstransform. Default is false

    **fitspw**
      *str*, *optional*

      Spectral window channel selection for fitting the continuumSelection of line-free channels using CASA syntax (e.g. '0:0~100;150:300'). If set to null, a fit to all unflagges visibilities will be performed. (Defaults to null)

    **fitorder**
      *int*, *optional*

      Polynomial order for the continuum fits

    **column**
      *str*, *optional*

      Data column to use.

    **obsinfo**
      *bool*, *optional*

      Create obsinfo.txt and obsinfo.json of MS file created by mstransform. Default true



-------------------------------------
**sunblocker**
-------------------------------------

  Use sunblocker to remove solar RFI. See description of sunblocker on github repository gigjozsa/sunblocker in method phazer of module sunblocker.py.

    **enable**
      *bool*, *optional*

      Execute segment sunblocker (yes/no). Default is yes.

    **use_mstransform**
      *bool*, *optional*

      Execute sunblocker on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

    **imsize**
      *int*, *optional*

      Image size (use the same as in wsclean_image or casa_image). Default is worker npix

    **cell**
      *float*, *optional*

      Cell size in arcsec (use the same as in wsclean_image or casa_image). Default is worker cell

    **threshold**
      *float*, *optional*

      Distance from average beyond which data are flagged in units of sigma. Default is 4.



-------------------------------------
**wsclean_image**
-------------------------------------

  Use WSClean to create line data cube. See WSclean wiki on sourceforge.

    **enable**
      *bool*, *optional*

      Execute segment wsclean_image (yes/no). Default is yes.

    **wscl_niter**
      *int*, *optional*

      Maximum number of rewsclean iterations to perform. Default is 2

    **rm_intcubes**
      *bool*, *optional*

      If set to true it deletes intermediate cubes from the output directory, if set to false it keeps all the cubes from the wsclean loops

    **use_mstransform**
      *bool*, *optional*

      Execute wsclean_image on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

    **pol**
      *str*, *optional*

      Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations). Default is I.

    **spwid**
      *int*, *optional*

      Spectral window to use. Default is 0.

    **nchans**
      *text*, *optional*

      Number of channels of HI cube, 'all' or an integer number. Default is 'all'.

    **firstchan**
      *int*, *optional*

      First channel of HI cube. Default is 0.

    **binchans**
      *int*, *optional*

      Integer binning of channels. Default is 1 (no binning).

    **npix**
      *seq*, *optional*

      Image size in pixels. List of integers (width and height) or a single integer for square images. Default is Worker default for npix.

    **padding**
      *float*, *optional*

      Images have initial size padding\*npix, and are later trimmed to npix. Default is 1.2.

    **mgain**
      *float*, *optional*

      Cleaning gain for major iterations, Ratio of peak that will be subtracted in each major iteration. Default is 0.9.

    **cell**
      *text*, *optional*

      Scale of a pixel. Default unit is arcsec, but can be specificied, e.g. 'scale 20asec'. Default is Worker default for cell.

    **weight**
      *str*, *optional*

      Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition. Default is Worker default for weight.

    **robust**
      *float*, *optional*

      Robust parameter in case of Briggs weighting. Default is 2.

    **taper**
      *float*, *optional*

      Gaussian taper FWHM in arcsec. Default is 0, no tapering.

    **niter**
      *int*, *optional*

      Maximum number of clean iterations to perform. Default is 1000000.

    **ownfitsmask**
      *str*, *optional*

      Accepts a 3D-mask cleaning mask in fits format. Mask made by the user. Default is '' (an empty field)

    **automask**
      *float*, *optional*

      Construct a mask from found components and when a threshold of sigma is reached, continue cleaning with the mask down to the normal threshold.

    **autothreshold**
      *float*, *optional*

      Estimate noise level using a robust estimator and stop at sigma x stddev

    **cleanborder**
      *float*, *optional*

      Set the border size in which no cleaning is performed, in percentage of the width/height of a plane. With an plane size of 1000 pixels and clean border of 1%, each border is 10 pixels. Default is 0.

    **make_cube**
      *bool*, *optional*

      If set to true the output is a data cube, if set to false the output is one fits file per spectral channel. Default is yes.

    **no_update_mod**
      *bool*, *optional*

      If set to true, will not store the clean model in MODEL_DATA. Relevant for HI.



-------------------------------------
**casa_image**
-------------------------------------

  Use CASA to create line data cube.

    **enable**
      *bool*, *optional*

    **use_mstransform**
      *bool*, *optional*

      Execute wsclean_image on continuum-subtracted data (otherwise use non-continuum-subtracted data) (yes/no). Default is yes.

    **pol**
      *str*, *optional*

      Polarizations in output cube (I,Q,U,V,XX,YY,XY,YX,RR,LL,RL,LR and combinations). Default is I.

    **spwid**
      *int*, *optional*

      Spectral window to use. Default is 0.

    **nchans**
      *text*, *optional*

      Number of channels. If set to 'all', all channels are used. Otherwise provide the number of channels (starting with startchan, see below). Default is 'all'.

    **startchan**
      *int*, *optional*

      Starting channel of the cube. Used in combination with nchans. Default is 0.

    **npix**
      *seq*, *optional*

      Image size in pixels. List of integers (width and height) or a single integer for square images. Default is worker npix.

    **cell**
      *text*, *optional*

      Scale of a pixel. Default unit is arcsec, but can be specificied, e.g. 'scale 20asec'. Default is worker cell.

    **weight**
      *str*, *optional*

      Weightmode can be natural, uniform, briggs. When using Briggs weighting, the Robustness parameter robust has to be specified in addition. Default is worker weight.

    **robust**
      *float*, *optional*

      Robust parameter in case of Briggs weighting. Default is worker robust.

    **niter**
      *int*, *optional*

      Maximum number of clean iterations to perform. Default is 1000000.

    **threshold**
      *str*, *optional*

      Flux level to stop cleaning, must include units, e.g. '1.0mJy'. Default is '10mJy'.

    **port2fits**
      *bool*, *optional*

      Port output to fits files if yes. Default is yes.



-------------------------------------
**remove_stokes_axis**
-------------------------------------

  Remove Stokes axis from HI cube

    **enable**
      *bool*, *optional*

      Execute this segment. Default is true



-------------------------------------
**pb_cube**
-------------------------------------

  Make primary beam cube

    **enable**
      *bool*, *optional*

      Execute this segment. Default is false



-------------------------------------
**freq_to_vel**
-------------------------------------

  Convert the spectral axis' header keys of the HI cube from frequency to velocity in the radio definition, v=c(1-obsfreq/restfreq). No change of spectra reference frame is performed.

    **enable**
      *bool*, *optional*

      Execute conversion. Default is true



-------------------------------------
**sofia**
-------------------------------------

  Run SoFiA source finder to produce a source mask and a Moment-0 map

    **enable**
      *bool*, *optional*

      Execute segment sofia (yes/no)? Default is yes.

    **rmsMode**
      *str*, *optional*

      Method to determine rms ('mad' for using median absolute deviation, 'std' for using standard deviation, 'negative' for using Gaussian fit to negative voxels). Default is 'mad'

    **threshold**
      *float*, *optional*

      SoFiA source finding threshold. Default is 4.0.

    **flag**
      *bool*, *optional*

      Use flag regions (yes/no)? Default is no.

    **flagregion**
      *optional*

      Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...]. Default is [].

    **merge**
      *bool*, *optional*

      Use method to de-select and merge emission islands detected by any of SoFiA source finding algorithms. If turned on, pixels with a separation of less than mergeX pixels in x direction and less than mergeY pixels in y-direction and less than z pixels in z-direction will be merged and identified as a single object in the mask. Detections whose extent in x-direction is smaller than minSizeX, in y direction is smaller than minSizeY, and in z-direction is smaller than minSizeZ will be removed from the mask. Parameter merge determines if the merging should be applied (yes/no). Default is yes.

    **mergeX**
      *int*, *optional*

      Merge-'radius' in x-direction. Default is 2

    **mergeY**
      *int*, *optional*

      Merge-'radius' in y-direction. Default is 2

    **mergeZ**
      *int*, *optional*

      Merge-'radius' in z-direction (velocity direction). Default is 3

    **minSizeX**
      *int*, *optional*

      Minimum size in x-direction. Default is 3.

    **minSizeY**
      *int*, *optional*

      Minimum size in y-direction. Default is 3.

    **minSizeZ**
      *int*, *optional*

      Minimum size in y-direction. Default is 5.



-------------------------------------
**flagging_summary**
-------------------------------------

  Print out flagging summary.

    **enable**
      *bool*, *optional*

      Execute printing flagging summary.

