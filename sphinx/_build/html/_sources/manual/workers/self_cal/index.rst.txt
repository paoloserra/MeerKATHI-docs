.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _self_cal:
 
==========================================
self_cal
==========================================
 
.. toctree::
   :maxdepth: 1
 
Perform Self calibration on the data



.. _self_cal_enable:

-------------------------------------
**enable**
-------------------------------------

  *bool*, *optional*

  Execute this segment



.. _self_cal_label:

-------------------------------------
**label**
-------------------------------------

  *str*, *optional*

  Label to tag the output files



.. _self_cal_order:

-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Workers are executed in ascedning order based on this value



.. _self_cal_undo_subtractmodelcol:

-------------------------------------
**undo_subtractmodelcol**
-------------------------------------

  *bool*, *optional*

  replace the corrected column with the sum of corrected and model columns to undo continuum subtraction that may have been done by the image HI worker. Default is false



.. _self_cal_primary_beam:

-------------------------------------
**primary_beam**
-------------------------------------

  *bool*, *optional*

  Use primary beam



.. _self_cal_calibrate_with:

-------------------------------------
**calibrate_with**
-------------------------------------

  *{"meqtrees", "cubical"}*, *optional*

  Tool to use for calibration



.. _self_cal_spwid:

-------------------------------------
**spwid**
-------------------------------------

  *int*, *optional*

  Provide spectral window id



.. _self_cal_ncpu:

-------------------------------------
**ncpu**
-------------------------------------

  *int*, *optional*

  number of cpu's to use



.. _self_cal_img_npix:

-------------------------------------
**img_npix**
-------------------------------------

  *int*, *optional*

  Number of pixels in output image



.. _self_cal_img_padding:

-------------------------------------
**img_padding**
-------------------------------------

  *float*, *optional*

  Padding



.. _self_cal_img_mgain:

-------------------------------------
**img_mgain**
-------------------------------------

  *float*, *optional*

  Image CLEANing gain



.. _self_cal_img_cell:

-------------------------------------
**img_cell**
-------------------------------------

  *float*, *optional*

  Image pixel size (arcsec)



.. _self_cal_img_weight:

-------------------------------------
**img_weight**
-------------------------------------

  *{"briggs", "uniform", "natural"}*, *optional*

  Image weighting type



.. _self_cal_img_robust:

-------------------------------------
**img_robust**
-------------------------------------

  *float*, *optional*

  Briggs robust value



.. _self_cal_img_uvtaper:

-------------------------------------
**img_uvtaper**
-------------------------------------

  *str*, *optional*

  Taper for imaging



.. _self_cal_img_niter:

-------------------------------------
**img_niter**
-------------------------------------

  *int*, *optional*

  Number of cleaning iterations



.. _self_cal_img_cleanborder:

-------------------------------------
**img_cleanborder**
-------------------------------------

  *float*, *optional*

  Clean border



.. _self_cal_img_facets:

-------------------------------------
**img_facets**
-------------------------------------

  *int*, *optional*

  Number facet to image



.. _self_cal_img_nchans:

-------------------------------------
**img_nchans**
-------------------------------------

  *int*, *optional*

  Number of channesls in output image



.. _self_cal_img_joinchannels:

-------------------------------------
**img_joinchannels**
-------------------------------------

  *bool*, *optional*

  Join channels to create MFS image



.. _self_cal_img_fit_spectral_pol:

-------------------------------------
**img_fit_spectral_pol**
-------------------------------------

  *int*, *optional*

  Fit a polynomial over frequency to each clean component



.. _self_cal_img_pol:

-------------------------------------
**img_pol**
-------------------------------------

  *str*, *optional*

  Stokes image to create



.. _self_cal_cal_gain_amplitude_clip_low:

-------------------------------------
**cal_gain_amplitude_clip_low**
-------------------------------------

  *float*, *optional*

  Lower gain amplitude clipping



.. _self_cal_cal_gain_amplitude_clip_high:

-------------------------------------
**cal_gain_amplitude_clip_high**
-------------------------------------

  *float*, *optional*

  Higher gain amplitude clipping



.. _self_cal_cal_niter:

-------------------------------------
**cal_niter**
-------------------------------------

  *int*, *optional*

  Number of self-calibration iterations to perform



.. _self_cal_start_at_iter:

-------------------------------------
**start_at_iter**
-------------------------------------

  *int*, *optional*

  Start self-cal iteration loop at this start value



.. _self_cal_aimfast:

-------------------------------------
**aimfast**
-------------------------------------

  Quality assessment parameter

  **enable**

    *bool*, *optional*

    Execute this segment

  **tolerance**

    *float*, *optional*

    Relative change in weighted mean of several indicators from aimfast.

  **convergence_criteria**

    *list* *of str*, *optional*

    The residual statistic to check convergence against. Every criterium listed will be combined into a weighted mean. Options ["DR","SKEW","KURT","STDDev","MEAN"]. Note that when calibrate model_mode = 'vis_only' DR is not an option.

  **area_factor**

    *float*, *optional*

    Peak flux source area multiplying factor i.e tot_area = psf-size\*af

  **normality_model**

    *{"normaltest", "shapiro"}*, *optional*

    normality test model to use. Note that normaltest is the D'Agostino

  **plot**

    *bool*, *optional*

    Generate html plots for comparing catalogs and residuals



.. _self_cal_image:

-------------------------------------
**image**
-------------------------------------

  Imaging parameter

  **enable**

    *bool*, *optional*

    Execute this segment

  **auto_mask**

    *list* *of int*, *optional*

    Auto masking threshold

  **auto_threshold**

    *list* *of float*, *optional*

    Auto clean threshold

  **column**

    *list* *of str*, *optional*

    Column to image

  **mask_from_sky**

    *bool*, *optional*

    switch on cleaning within mask from fits file

  **fits_mask**

    *list* *of str*, *optional*

    filename of fits mask (in output/masking folder)

  **multi_scale**

    *bool*, *optional*

    switch on multiscale cleaning

  **multi_scale_scales**

    *list* *of int*, *optional*

    scales of multiscale [0,10,20,etc, etc]

  **no_update_model**

    *bool*, *optional*

    do not update column MODEL_DATA after wsclean

  **minuvw_m**

    *int*, *optional*

    exclude short baselines [m]

  **local_rms**

    *bool*, *optional*

    switch on local rms measurement for cleaning



.. _self_cal_sofia_mask:

-------------------------------------
**sofia_mask**
-------------------------------------

  Run SoFiA source finder to produce a source mask and a Moment-0 map

  **enable**

    *bool*, *optional*

    Execute segment sofia (yes/no)? Default is yes.

  **threshold**

    *float*, *optional*

    SoFiA source finding threshold. Default is 4.0.

  **flag**

    *bool*, *optional*

    Use flag regions (yes/no)? Default is no.

  **flagregion**

    *list* *of int*, *optional*

    Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...]. Default is [].

  **inputmask**

    *str*, *optional*

    input mask over which add Sofia's

  **kernels**

    *list* *of int*, *optional*

    Kernels for mask

  **fornax_special**

    *bool*, *optional*

    Activates masking of Fornax A using Sofia

  **fornax_thresh**

    *list* *of float*, *optional*

    SoFiA source finding threshold. Default is 4.0.

  **use_sofia**

    *bool*, *optional*

    use sofia for mask of Fornax A instead of Fomalont mask

  **scale_noise_window**

    *float*, *optional*

    window size where to measure local rms in pixels

  **positivity**

    *bool*, *optional*

    merges only positive pixesl of sources in mask



.. _self_cal_extract_sources:

-------------------------------------
**extract_sources**
-------------------------------------

  Source finding parameters

  **enable**

    *bool*, *optional*

    Execute this segment

  **sourcefinder**

    *str*, *optional*

    choose your favorite sourcefinder pybdsm, (pybdsf), sofia

  **local_rms**

    *bool*, *optional*

    Execute this segment

  **spi**

    *bool*, *optional*

    Extract source spectral index

  **thresh_pix**

    *list* *of int*, *optional*

    Source finder pixel threshold

  **thresh_isl**

    *list* *of int*, *optional*

    Source finder island threshold



.. _self_cal_calibrate:

-------------------------------------
**calibrate**
-------------------------------------

  Calibration parameters

  **enable**

    *bool*, *optional*

    Execute this segment

  **model**

    *list* *of str*, *optional*

    Model number to use [or combination e.g. '1+2' to use first and second models]

  **output_data**

    *list* *of str*, *optional*

    Data to output after calibration

  **gain_matrix_type**

    *list* *of str*, *optional*

    Gain matrix type

  **model_mode**

    *str*, *optional*

    pybdsm_vis, pybdsm_only,  vis_only are the possible options

  **shared_memory**

    *str*, *optional*

    Set the amount of shared memory for cubical. Default '100Gb'

  **two_step**

    *bool*, *optional*

    Trigger a two step calibration process where the phase only calibration is applied before continuing with amplitude + phase cal. When cubical is used this happens simultaneous and gain parameters can be used with DDsols parameters. Set DDsol_time to -1 one to avoid amplitude calibration in an itereation. The parameter DDjones should be set to false.

  **add_vis_model**

    *bool*, *optional*

    Add/Use clean components from latest imaging step to/as sky model for calibation

  **Gsols_time**

    *list* *of float*, *optional*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **Gsols_channel**

    *list* *of float*, *optional*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **Bjones**

    *bool*, *optional*

    Enable Bjones

  **Bsols_time**

    *list* *of float*, *optional*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **Bsols_channel**

    *list* *of float*, *optional*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **DDjones**

    *bool*, *optional*

    Enable direction dependent calibration, currently experimental.

  **DDsols_time**

    *list* *of float*, *optional*

    Calibration solution intervals

  **DDsols_channel**

    *list* *of float*, *optional*

    Calibration solution intervals



.. _self_cal_restore_model:

-------------------------------------
**restore_model**
-------------------------------------

  Restore modelled to final calibrated residual image

  **enable**

    *bool*, *optional*

    Execute this segment

  **model**

    *str*, *optional*

    Model number to use [or combination e.g. '1+2' to use first and second models]

  **clean_model**

    *str*, *optional*

    Clean model number to use [or combination e.g. '1+2' to use first and second models]



.. _self_cal_flagging_summary:

-------------------------------------
**flagging_summary**
-------------------------------------

  Output the flagging summary

  **enable**

    *bool*, *optional*

    Execute this segment



.. _self_cal_gain_interpolation:

-------------------------------------
**gain_interpolation**
-------------------------------------

  Interpolate gains over the high frequency resolution data

  **enable**

    *bool*, *optional*

    Execute this segment

  **hires_label**

    *str*, *optional*

    label for high resolution data products in selfcal



.. _self_cal_highfreqres_contim:

-------------------------------------
**highfreqres_contim**
-------------------------------------

  Make final continuum image and model at higher freq res, ideally using a clean mask based on the last round of continuum imging

  **enable**

    *bool*, *optional*

    Execute this segment

  **chans**

    *int*, *optional*

    output continuum channels

  **deconv_chans**

    *int*, *optional*

    nr of channels used for deconvolution grouping together output continuum channels

  **fit_spectral_pol**

    *int*, *optional*

    How many terms for the spectral polynomial fit of each clean component

  **fits_mask**

    *str*, *optional*

    filename of fits mask (including folder if not input), default None

  **auto_mask**

    *float*, *optional*

    Auto masking threshold, default None

  **auto_threshold**

    *float*, *optional*

    Auto clean threshold, default 10

  **column**

    *str*, *optional*

    Column to image

  **multi_scale**

    *bool*, *optional*

    switch on multiscale cleaning

  **multi_scale_scales**

    *list* *of int*, *optional*

    scales of multiscale [0,10,20,etc, etc]

  **local_rms**

    *bool*, *optional*

    switch on local rms measurement for cleaning

