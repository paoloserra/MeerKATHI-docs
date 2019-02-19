.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
self_cal
==========================================
 
.. toctree::
   :maxdepth: 1
 
Perform Self calibration on the data



-------------------------------------
**enable**
-------------------------------------
  *bool*, *optional*

  Execute this segment



-------------------------------------
**label**
-------------------------------------
  *str*, *optional*

  Label to tag the output files



-------------------------------------
**order**
-------------------------------------
  *int*, *optional*

  Workers are executed in ascedning order based on this value



-------------------------------------
**undo_subtractmodelcol**
-------------------------------------
  *bool*, *optional*

  replace the corrected column with the sum of corrected and model columns to undo continuum subtraction that may have been done by the image HI worker. Default is false



-------------------------------------
**primary_beam**
-------------------------------------
  *bool*, *optional*

  Use primary beam



-------------------------------------
**calibrate_with**
-------------------------------------
  *str*, *optional*

  Tool to use for calibration



-------------------------------------
**spwid**
-------------------------------------
  *int*, *optional*

  Provide spectral window id



-------------------------------------
**img_npix**
-------------------------------------
  *int*, *optional*

  Number of pixels in output image



-------------------------------------
**img_padding**
-------------------------------------
  *float*, *optional*

  Padding



-------------------------------------
**img_mgain**
-------------------------------------
  *float*, *optional*

  Image CLEANing gain



-------------------------------------
**img_cell**
-------------------------------------
  *float*, *optional*

  Image pixel size (arcsec)



-------------------------------------
**img_weight**
-------------------------------------
  *str*, *optional*

  Image weighting type



-------------------------------------
**img_robust**
-------------------------------------
  *float*, *optional*

  Briggs robust value



-------------------------------------
**img_niter**
-------------------------------------
  *int*, *optional*

  Number of cleaning iterations



-------------------------------------
**img_cleanborder**
-------------------------------------
  *float*, *optional*

  Clean border



-------------------------------------
**img_facets**
-------------------------------------
  *int*, *optional*

  Number facet to image



-------------------------------------
**img_nchans**
-------------------------------------
  *int*, *optional*

  Number of channesls in output image



-------------------------------------
**img_joinchannels**
-------------------------------------
  *bool*, *optional*

  Join channels to create MFS image



-------------------------------------
**img_fit_spectral_pol**
-------------------------------------
  *int*, *optional*

  Fit a polynomial over frequency to each clean component



-------------------------------------
**img_pol**
-------------------------------------
  *str*, *optional*

  Stokes image to create



-------------------------------------
**bjones**
-------------------------------------
  *bool*, *optional*

  Enable Bjones.



-------------------------------------
**ddjones**
-------------------------------------
  *bool*, *optional*

  Enable direction dependent calibration, currently experimental.



-------------------------------------
**cal_DDsols**
-------------------------------------
  *optional*
  Calibration solution intervals



-------------------------------------
**cal_gain_amplitude_clip_low**
-------------------------------------
  *float*, *optional*

  Lower gain amplitude clipping



-------------------------------------
**cal_gain_amplitude_clip_high**
-------------------------------------
  *float*, *optional*

  Higher gain amplitude clipping



-------------------------------------
**cal_niter**
-------------------------------------
  *int*, *optional*

  Number of self-calibration iterations to perform



-------------------------------------
**start_at_iter**
-------------------------------------
  *int*, *optional*

  Start self-cal iteration loop at this start value



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
      *optional*

      The residual statistic to check convergence against. Every criterium listed will be combined into a weighted mean. Options ["DR","SKEW","KURT","STDDev","MEAN"]. Note that when calibrate model_mode = 'vis_only' DR is not an option.

    **area_factor**
      *float*, *optional*

      Peak flux source area multiplying factor i.e tot_area = psf-size*af

    **normality_model**
      *str*, *optional*

      normality test model to use. Note that normaltest is the D'Agostino



-------------------------------------
**image**
-------------------------------------
  Imaging parameter

    **enable**
      *bool*, *optional*

      Execute this segment

    **auto_mask**
      *optional*

      Auto masking threshold

    **auto_threshold**
      *optional*

      Auto clean threshold

    **column**
      *optional*

      Column to image

    **mask_from_sky**
      *bool*, *optional*

      switch on cleaning within mask from fits file

    **fits_mask**
      *optional*

      filename of fits mask (in output/masking folder)

    **multi_scale**
      *bool*, *optional*

      switch on multiscale cleaning

    **multi_scale_scales**
      *optional*

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
      *optional*

      Pixel/channel range(s) to be flagged prior to source finding. Format is [[x1, x2, y1, y2, z1, z2], ...]. Default is [].

    **inputmask**
      *str*, *optional*

      input mask over which add Sofia's

    **kernels**
      *optional*

      Kernels for mask

    **fornax_special**
      *bool*, *optional*

      Activates masking of Fornax A using Sofia

    **fornax_thresh**
      *optional*

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



-------------------------------------
**extract_sources**
-------------------------------------
  Source finding parameters

    **enable**
      *bool*, *optional*

      Execute this segment

    **spi**
      *bool*, *optional*

      Extract source spectral index

    **thresh_pix**
      *optional*

      Source finder pixel threshold

    **thresh_isl**
      *optional*

      Source finder island threshold



-------------------------------------
**calibrate**
-------------------------------------
  Calibration parameters

    **enable**
      *bool*, *optional*

      Execute this segment

    **model**
      *optional*

      Model number to use [or combination e.g. '1+2' to use first and second models]

    **output_data**
      *optional*

      Data to output after calibration

    **gain_matrix_type**
      *optional*

      Gain matrix type

    **model_mode**
      *str*, *optional*

      pybdsm_vis, pybdsm_only,  vis_only are the possible options

    **add_vis_model**
      *bool*, *optional*

      Add/Use clean components from latest imaging step to/as sky model for calibation

    **Gsols_time**
      *optional*

      Gsols for individual calibration steps, if not given will default to cal_Gsols

    **Gsols_channel**
      *optional*

      Gsols for individual calibration steps, if not given will default to cal_Gsols



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



-------------------------------------
**flagging_summary**
-------------------------------------
  Output the flagging summary

    **enable**
      *bool*, *optional*

      Execute this segment



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
      *optional*

      scales of multiscale [0,10,20,etc, etc]

    **local_rms**
      *bool*, *optional*

      switch on local rms measurement for cleaning

