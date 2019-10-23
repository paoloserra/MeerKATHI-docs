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

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*

  Execute this segment



.. _self_cal_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*, *default = corr*

  Label of the .MS files to process



.. _self_cal_undo_subtractmodelcol:

--------------------------------------------------
**undo_subtractmodelcol**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  replace the corrected column with the sum of corrected and model columns to undo continuum subtraction that may have been done by the image HI worker.



.. _self_cal_primary_beam:

--------------------------------------------------
**primary_beam**
--------------------------------------------------

  *bool*, *optional*, *default = False*

  Use primary beam



.. _self_cal_calibrate_with:

--------------------------------------------------
**calibrate_with**
--------------------------------------------------

  *{"meqtrees", "cubical"}*, *optional*, *default = cubical*

  Tool to use for calibration



.. _self_cal_spwid:

--------------------------------------------------
**spwid**
--------------------------------------------------

  *int*, *optional*, *default = 0*

  Provide spectral window id



.. _self_cal_ncpu:

--------------------------------------------------
**ncpu**
--------------------------------------------------

  *int*, *optional*, *default = 5*

  number of cpu's to use



.. _self_cal_img_npix:

--------------------------------------------------
**img_npix**
--------------------------------------------------

  *int*, *optional*, *default = 1800*

  Number of pixels in output image



.. _self_cal_img_padding:

--------------------------------------------------
**img_padding**
--------------------------------------------------

  *float*, *optional*, *default = 1.3*

  Padding in WSclean



.. _self_cal_img_mgain:

--------------------------------------------------
**img_mgain**
--------------------------------------------------

  *float*, *optional*, *default = 0.99*

  Image CLEANing gain



.. _self_cal_img_cell:

--------------------------------------------------
**img_cell**
--------------------------------------------------

  *float*, *optional*, *default = 2.*

  Image pixel size (arcsec)



.. _self_cal_img_weight:

--------------------------------------------------
**img_weight**
--------------------------------------------------

  *{"briggs", "uniform", "natural"}*, *optional*, *default = briggs*

  Image weighting type. If Briggs, set the img robust parameter



.. _self_cal_img_robust:

--------------------------------------------------
**img_robust**
--------------------------------------------------

  *float*, *optional*, *default = 0.*

  Briggs robust value



.. _self_cal_img_uvtaper:

--------------------------------------------------
**img_uvtaper**
--------------------------------------------------

  *str*, *optional*, *default = 0*

  Taper for imaging (arcsec)



.. _self_cal_img_niter:

--------------------------------------------------
**img_niter**
--------------------------------------------------

  *int*, *optional*, *default = 1000000*

  Number of cleaning iterations



.. _self_cal_img_cleanborder:

--------------------------------------------------
**img_cleanborder**
--------------------------------------------------

  *float*, *optional*, *default = 1.3*

  Clean border



.. _self_cal_img_nchans:

--------------------------------------------------
**img_nchans**
--------------------------------------------------

  *int*, *optional*, *default = 3*

  Number of channesls in output image



.. _self_cal_img_joinchannels:

--------------------------------------------------
**img_joinchannels**
--------------------------------------------------

  *bool*, *optional*, *default = True*

  Join channels to create MFS image



.. _self_cal_img_fit_spectral_pol:

--------------------------------------------------
**img_fit_spectral_pol**
--------------------------------------------------

  *int*, *optional*, *default = 2*

  Number of spectral polynomial terms to fit to each clean component. This is equal to the order of the polynomial plus 1.



.. _self_cal_img_pol:

--------------------------------------------------
**img_pol**
--------------------------------------------------

  *str*, *optional*, *default = I*

  Stokes image to create



.. _self_cal_cal_gain_amplitude_clip_low:

--------------------------------------------------
**cal_gain_amplitude_clip_low**
--------------------------------------------------

  *float*, *optional*, *default = 0.5*

  Lower gain amplitude clipping



.. _self_cal_cal_gain_amplitude_clip_high:

--------------------------------------------------
**cal_gain_amplitude_clip_high**
--------------------------------------------------

  *float*, *optional*, *default = 2.*

  Higher gain amplitude clipping



.. _self_cal_cal_niter:

--------------------------------------------------
**cal_niter**
--------------------------------------------------

  *int*, *optional*, *default = 2*

  Number of self-calibration iterations to perform



.. _self_cal_start_at_iter:

--------------------------------------------------
**start_at_iter**
--------------------------------------------------

  *int*, *optional*, *default = 1*

  Start self-cal iteration loop at this start value, 1-based.



.. _self_cal_cal_time_chunk:

--------------------------------------------------
**cal_time_chunk**
--------------------------------------------------

  *int*, *optional*, *default = 128*

  Chunk data up by this number of timeslots. This limits the amount of data processed at once. Smaller chunks allow for a smaller RAM footprint and greater parallelism but sets an upper limit on the time solution intervals that may be employed. 0 means use full time axis but does not cross scan boundaries.



.. _self_cal_cal_freq_chunk:

--------------------------------------------------
**cal_freq_chunk**
--------------------------------------------------

  *int*, *optional*, *default = 1024*

  Chunk data up by this number of channels. This limits the amount of data processed at once. Smaller chunks allow for a smaller RAM footprint and greater parallelism but sets an upper limit on the frequency solution intervals that may be employed. 0 means use full frequency axis but does not cross SPW boundaries.



.. _self_cal_aimfast:

--------------------------------------------------
**aimfast**
--------------------------------------------------

  Quality assessment parameter

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **tolerance**

    *float*, *optional*, *default = 0.02*

    Relative change in weighted mean of several indicators from aimfast.

  **convergence_criteria**

    *list* *of str*, *optional*, *default = DR*

    The residual statistic to check convergence against. Every criterium listed will be combined into a weighted mean. Options ["DR","SKEW","KURT","STDDev","MEAN"]. Note that when calibrate model_mode = 'vis_only' DR is not an option.

  **area_factor**

    *int*, *optional*, *default = 6*

    Peak flux source area multiplying factor i.e tot_area = psf-size\*af

  **normality_model**

    *{"normaltest", "shapiro"}*, *optional*, *default = normaltest*

    normality test model to use. Note that normaltest is the D'Agostino

  **plot**

    *bool*, *optional*, *default = True*

    Generate html plots for comparing catalogs and residuals



.. _self_cal_image:

--------------------------------------------------
**image**
--------------------------------------------------

  Imaging parameter

  **enable**

    *bool*, *optional*, *default = True*

    Execute this segment

  **auto_mask**

    *list* *of float*, *optional*, *default = 30, 10, 7*

    Auto masking threshold

  **auto_threshold**

    *list* *of float*, *optional*, *default = 0.5*

    Auto clean threshold

  **column**

    *list* *of str*, *optional*, *default = DATA, CORRECTED_DATA*

    Column to image

  **mask_from_sky**

    *bool*, *optional*, *default = False*

    switch on cleaning within mask from fits file

  **fits_mask**

    *list* *of str*, *optional*, *default = catalog_mask.fits*

    filename of fits mask (in output/masking folder)

  **multi_scale**

    *bool*, *optional*, *default = False*

    switch on multiscale cleaning

  **multi_scale_scales**

    *list* *of int*, *optional*, *default = 10, 20, 30*

    scales of multiscale [0,10,20,etc, etc] in pixels

  **minuvw_m**

    *int*, *optional*, *default = 0*

    exclude short baselines [m]

  **local_rms**

    *bool*, *optional*, *default = False*

    switch on local rms measurement for cleaning



.. _self_cal_sofia_mask:

--------------------------------------------------
**sofia_mask**
--------------------------------------------------

  Run SoFiA source finder to produce a source mask and a Moment-0 map

  **enable**

    *bool*, *optional*, *default = False*

    Execute segment sofia (yes/no)?

  **threshold**

    *float*, *optional*, *default = 4.0*

    SoFiA source finding threshold.

  **flag**

    *bool*, *optional*, *default = False*

    Use flag regions (yes/no)?

  **flagregion**

    *list* *of str*, *optional*, *default = ' '*

    Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...].

  **inputmask**

    *str*, *optional*, *default = ' '*

    input mask over which add Sofia's

  **fornax_special**

    *bool*, *optional*, *default = False*

    Activates masking of Fornax A using Sofia

  **fornax_thresh**

    *list* *of float*, *optional*, *default = 4.0*

    SoFiA source finding threshold. Default is 4.0.

  **use_sofia**

    *bool*, *optional*, *default = False*

    use sofia for mask of Fornax A instead of Fomalont mask

  **scale_noise_window**

    *int*, *optional*, *default = 31*

    window size where to measure local rms in pixels

  **positivity**

    *bool*, *optional*, *default = False*

    merges only positive pixesl of sources in mask



.. _self_cal_extract_sources:

--------------------------------------------------
**extract_sources**
--------------------------------------------------

  Source finding parameters

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **sourcefinder**

    *str*, *optional*, *default = pybdsm*

    choose your favorite sourcefinder pybdsm, (pybdsf), sofia

  **local_rms**

    *bool*, *optional*, *default = False*

    Execute this segment

  **spi**

    *bool*, *optional*, *default = False*

    Extract source spectral index

  **thresh_pix**

    *list* *of int*, *optional*, *default = 5*

    Source finder pixel threshold

  **thresh_isl**

    *list* *of int*, *optional*, *default = 3*

    Source finder island threshold



.. _self_cal_calibrate:

--------------------------------------------------
**calibrate**
--------------------------------------------------

  Calibration parameters

  **enable**

    *bool*, *optional*, *default = True*

    Execute this segment

  **model**

    *list* *of str*, *optional*, *default = 1,2*

    Model number to use [or combination e.g. '1+2' to use first and second models]

  **output_data**

    *list* *of str*, *optional*, *default = CORR_DATA*

    Data to output after calibration

  **gain_matrix_type**

    *list* *of str*, *optional*, *default = GainDiagPhase*

    Gain matrix type

  **model_mode**

    *str*, *optional*, *default = vis_only*

    pybdsm_vis, pybdsm_only,  vis_only are the possible options

  **shared_memory**

    *str*, *optional*, *default = 100Gb*

    Set the amount of shared memory for cubical. Default '100Gb'

  **two_step**

    *bool*, *optional*, *default = False*

    Trigger a two step calibration process where the phase only calibration is applied before continuing with amplitude + phase cal. When cubical is used this happens simultaneous and gain parameters can be used with DDsols parameters. Set DDsol_time to -1 one to avoid amplitude calibration in an itereation. The parameter DDjones should be set to false.

  **add_vis_model**

    *bool*, *optional*, *default = True*

    Add/Use clean components from latest imaging step to/as sky model for calibation

  **Gsols_time**

    *list* *of float*, *optional*, *default = 16*

    G-Jones time solution interval. The parameter cal_time_chunk above should a multiple of Gsols_time. 0 means a single solution for the full time chunk.

  **Gsols_channel**

    *list* *of float*, *optional*, *default = 0*

    G-Jones frequency solution interval. The parameter cal_frq_chunk above should a multiple of Gsols_channel. 0 means a single solution for the full frequency chunk.

  **Bjones**

    *bool*, *optional*, *default = False*

    Enable Bjones

  **Bsols_time**

    *list* *of int*, *optional*, *default = 0*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **Bsols_channel**

    *list* *of float*, *optional*, *default = 2*

    Gsols for individual calibration steps, if not given will default to cal_Gsols

  **DDjones**

    *bool*, *optional*, *default = False*

    Enable direction dependent calibration, currently experimental.

  **DDsols_time**

    *list* *of float*, *optional*, *default = 0*

    Calibration solution intervals

  **DDsols_channel**

    *list* *of float*, *optional*, *default = 0*

    Calibration solution intervals

  **weight_column**

    *str*, *optional*, *default = WEIGHT*

    Column with weights

  **madmax_flagging**

    *bool*, *optional*, *default = True*

    Flags based on maximum of mad

  **madmax_flag_thresh**

    *list* *of int*, *optional*, *default = 0, 10*

    Threshold for madmax flagging

  **sol_term_iters**

    *str*, *optional*, *default = auto*

    Number of iterations per Jones term. If set to 'auto', uses hardcoded iteration numbers depending on the jones chain.

  **ragavi_plot**

    Plotting dignostics plots for delay correction calibration.

    **enable**

      *bool*, *optional*, *default = False*

      Enables plotting dignostics

    **gaintype**

      *list* *of str*, *optional*, *default = G*

      List of gain solution types

    **field**

      *list* *of int*, *optional*, *default = 0*

      Fields to plot. Specify by field id, index.

    **corr**

      *str*, *optional*, *default = X*

      Correlation to plot. E.g. X/Y or H/V



.. _self_cal_restore_model:

--------------------------------------------------
**restore_model**
--------------------------------------------------

  Restore modelled to final calibrated residual image

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **model**

    *str*, *optional*, *default = 1+2*

    Model number to use [or combination e.g. '1+2' to use first and second models]

  **clean_model**

    *str*, *optional*, *default = 3*

    Clean model number to use [or combination e.g. '1+2' to use first and second models]



.. _self_cal_flagging_summary:

--------------------------------------------------
**flagging_summary**
--------------------------------------------------

  Output the flagging summary

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment



.. _self_cal_transfer_apply_gains:

--------------------------------------------------
**transfer_apply_gains**
--------------------------------------------------

  Interpolate gains over the high frequency resolution data

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **transfer_to_label**

    *str*, *optional*, *default = corr*

    label of cross-calibrated .ms file to which to transfer and apply the selfcal gains



.. _self_cal_transfer_model:

--------------------------------------------------
**transfer_model**
--------------------------------------------------

  Transfer model from last WSclean imaging run to the MODEL_DATA column of another .MS

  **enable**

    *bool*, *optional*, *default = True*

    Execute this segment (default False)

  **transfer_to_label**

    *str*, *optional*, *default = corr*

    label of .ms file to which to transfer the model

  **model**

    *str*, *optional*, *default = auto*

    Name of the sky model file (currently the only supported format is that of WSclean component lists). When 'auto', the pipeline builds the file name from the input parameters of the selfcal loop. The file is assumed to be in the 'output' directory.

  **spectra**

    *bool*, *optional*, *default = True*

    Model sources as non-flat spectra. The spectral coefficients and reference frequency must be present in the sky model.

  **row_chunks**

    *int*, *optional*, *default = 0*

    Number of rows of input .MS that are processed in a single chunk.

  **model_chunks**

    *int*, *optional*, *default = 0*

    Number of sky model components that are processed in a single chunk.

  **invert_uvw**

    *bool*, *optional*, *default = True*

    Invert UVW coordinates. Useful if we want compare our visibilities against MeqTrees.

  **within**

    *str*, *optional*, *default = ' '*

    Give JS9 region file. Only sources within those regions will be included.

  **points_only**

    *bool*, *optional*, *default = False*

    Select only point-only sources. Default is False.

  **num_sources**

    *int*, *optional*, *default = 0*

    Select only N brightest sources. Default is 0

  **num_workers**

    *int*, *optional*, *default = 0*

    Explicitly set the number of worker threads. Default is 0, meaning it uses all threads.

  **memory_fraction**

    *float*, *optional*, *default = 0.5*

    Fraction of system RAM that can be used. Used when setting automatically the chunk size.



.. _self_cal_highfreqres_contim:

--------------------------------------------------
**highfreqres_contim**
--------------------------------------------------

  Make final continuum image and model at higher frequency resolution, ideally using a clean mask based on the last round of continuum imaging

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **chans**

    *int*, *optional*, *default = 10*

    output continuum channels

  **deconv_chans**

    *int*, *optional*, *default = 2*

    nr of channels used for deconvolution grouping together output continuum channels

  **fit_spectral_pol**

    *int*, *optional*, *default = 2*

    How many terms for the spectral polynomial fit of each clean component

  **fits_mask**

    *str*, *optional*, *default = ' '*

    filename of fits mask (including folder if not input), default None

  **auto_mask**

    *float*, *optional*, *default = 10*

    Auto masking threshold, default None

  **auto_threshold**

    *float*, *optional*, *default = 0.5*

    Auto clean threshold, default 10

  **column**

    *str*, *optional*, *default = CORR_DATA*

    Column to image

  **multi_scale**

    *bool*, *optional*, *default = False*

    switch on multiscale cleaning

  **multi_scale_scales**

    *list* *of int*, *optional*, *default = 10, 20, 30, 40*

    scales of multiscale [0,10,20,etc, etc] in pixel

  **local_rms**

    *bool*, *optional*, *default = False*

    switch on local rms measurement for cleaning

