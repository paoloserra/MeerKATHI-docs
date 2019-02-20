.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
==========================================
masking
==========================================
 
.. toctree::
   :maxdepth: 1
 
Create mask from catalog / merge with mask of extended source



-------------------------------------
**enable**
-------------------------------------

  *bool*, *optional*

  Execute this segment



-------------------------------------
**order**
-------------------------------------

  *int*, *optional*

  Workers are executed in ascending order based on this value



-------------------------------------
**centre_coord**
-------------------------------------

  *optional*

  Coordinates of the centre of the field of view ["00:00:00","00:00:00"]



-------------------------------------
**mask_size**
-------------------------------------

  *int*, *optional*

  Number of pixels in the mask (must be the same as img_npix in selfcal)



-------------------------------------
**cell_size**
-------------------------------------

  *float*, *optional*

  Size fo pixel in the mask (arcsecm, must be the same as img_cell in selfcal)



-------------------------------------
**name_mask**
-------------------------------------

  *str*, *optional*

  Name of the output mask from SUMSS catalog



-------------------------------------
**extended_source_input**
-------------------------------------

  *str*, *optional*

  Name of the output mask of Fornax A



-------------------------------------
**final_mask**
-------------------------------------

  *str*, *optional*

  Name of the output final mask



-------------------------------------
**query_catalog**
-------------------------------------

  Query catalog to select field/sources from which extract the mask

    **enable**
      *bool*, *optional*

      Execute this worker

    **catalog**
      *str*, *optional*

      Name of catalog to query, either NVSS or SUMSS

    **width_image**
      *str*, *optional*

      Width of the region of sky we want to mask (keep larger than dirty image)



-------------------------------------
**pb_correction**
-------------------------------------

  Correct image for primary beam before exctracting mask

    **enable**
      *bool*, *optional*

      Execute this worker

    **frequency**
      *float*, *optional*

      Primary beam size changes with frequency, provide central frequency of dataset



-------------------------------------
**make_mask**
-------------------------------------

  Build mask from existing images

    **enable**
      *bool*

      Execute this worker

    **mask_with**
      *str*, *optional*

      Tool to use for masking

    **input_image**
      *str*, *optional*

      Input image where to create mask

    **thresh_lev**
      *float*, *optional*

      Cutoff to select sources in the SUMSS map, corrected for the primary beam (Jy)

    **scale_noise_window**
      *float*, *optional*

      window size where to measure local rms in pixels



-------------------------------------
**merge_with_extended**
-------------------------------------

  Merge with extedned map

    **enable**
      *bool*

      Execute this worker

    **extended_source_input**
      *str*, *optional*

      name of image of extended source

    **mask_with**
      *str*, *optional*

      Tool to use for masking

    **thresh_lev**
      *float*, *optional*

      Cutoff to select sources in the SUMSS map, corrected for the primary beam (Jy)

