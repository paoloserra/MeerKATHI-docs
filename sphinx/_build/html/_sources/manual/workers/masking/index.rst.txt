.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _masking:
 
==========================================
masking
==========================================
 
.. toctree::
   :maxdepth: 1
 
Create mask from catalog and/or merge with mask of extended source



.. _masking_enable:

--------------------------------------------------
**enable**
--------------------------------------------------

  *bool*, *optional*

  Execute this segment



.. _masking_centre_coord:

--------------------------------------------------
**centre_coord**
--------------------------------------------------

  *list* *of str*, *optional*

  Coordinates of the centre of the field of view read from reference_dir by default



.. _masking_label:

--------------------------------------------------
**label**
--------------------------------------------------

  *str*, *optional*

  Label of the .MS file where to find information about the target



.. _masking_mask_size:

--------------------------------------------------
**mask_size**
--------------------------------------------------

  *int*, *optional*

  Number of pixels in the mask (must be the same as img_npix in selfcal worker)



.. _masking_cell_size:

--------------------------------------------------
**cell_size**
--------------------------------------------------

  *float*, *optional*

  Size of pixel in the mask (arcsec, must be the same as img_cell in selfcal worker)



.. _masking_name_mask:

--------------------------------------------------
**name_mask**
--------------------------------------------------

  *str*, *optional*

  Name of the output mask generated from catalog



.. _masking_extended_source_input:

--------------------------------------------------
**extended_source_input**
--------------------------------------------------

  *str*, *optional*

  Name of the input mask for particularly extended sources in the field



.. _masking_final_mask:

--------------------------------------------------
**final_mask**
--------------------------------------------------

  *str*, *optional*

  Name of the output final mask



.. _masking_query_catalog:

--------------------------------------------------
**query_catalog**
--------------------------------------------------

  Query catalog to select field/sources from which extract the mask

  **enable**

    *bool*, *optional*

    Execute this worker

  **catalog**

    *{"NVSS", "SUMSS"}*, *optional*

    Name of catalog to query [NVSS/SUMSS]

  **width_image**

    *str*, *optional*

    Width of the region of sky we want to mask (keep larger than dirty image)

  **thresh_nvss**

    *float*, *optional*

    Cutoff to select sources in the SUMSS map, corrected for the primary beam (Jy) or cutoff in sigmas for sofia source finder



.. _masking_pb_correction:

--------------------------------------------------
**pb_correction**
--------------------------------------------------

  Correct input image for primary beam before exctracting mask

  **enable**

    *bool*, *optional*

    Execute this worker

  **frequency**

    *float*, *optional*

    Primary beam size changes with frequency, provide central frequency of considered dataset



.. _masking_make_mask:

--------------------------------------------------
**make_mask**
--------------------------------------------------

  Build mask from existing image using SoFiA and/or threshold cutoff

  **enable**

    *bool*, *optional*

    Execute this worker

  **mask_with**

    *{"thresh", "sofia"}*, *optional*

    Tool to use for masking

  **input_image**

    *{"pbcorr", "path_to_mask"}*, *optional*

    Input image where to create mask ???? what is this ???

  **thresh_lev**

    *int*, *optional*

    Cutoff to select sources in the SUMSS map, corrected for the primary beam (Jy) or cutoff in sigmas for sofia source finder

  **scale_noise_window**

    *int*, *optional*

    window size where SoFiA measures the local rms, units of pixels



.. _masking_merge_with_extended:

--------------------------------------------------
**merge_with_extended**
--------------------------------------------------

  Merge with mask of extended source

  **enable**

    *bool*, *optional*

    Execute this worker

  **extended_source_input**

    *str*, *optional*

    name of image of extended source to merge with current image

  **mask_with**

    *{"thresh", "sofia"}*, *optional*

    Tool to use for masking

  **thresh_lev**

    *float*, *optional*

    Cutoff to select sources in the SUMSS map, corrected for the primary beam (Jy) or cutoff in sigmas for sofia source finder

