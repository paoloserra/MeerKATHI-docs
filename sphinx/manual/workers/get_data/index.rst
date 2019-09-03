.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
.. _get_data:
 
==========================================
get_data
==========================================
 
.. toctree::
   :maxdepth: 1
 
Download and/or convert/unarchive data so that its in the MS format for further processing



.. _get_data_dataid:

--------------------------------------------------
**dataid**
--------------------------------------------------

  *list* *of str*

  Basename of MS. For MeerKAT data to be downloaded by MeerKATHI, this should be the data ID of the observation



.. _get_data_mvftoms:

--------------------------------------------------
**mvftoms**
--------------------------------------------------

  Convert HDF5/MVF files in data_path to MS files; the latter are written to msdir; also creates a MS.TAR file. (This only works for MeerKAT HDF5 files)

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **tar**

    *bool*, *optional*, *default = False*

    Create a tarbal of the converted MS.

  **channel_range**

    *str*, *optional*, *default = all*

    Only exctract channels in this range (0-based, inclusive; comma seperated string)

  **full_poll**

    *bool*, *optional*, *default = False*

    Extract all four correlations instead of only the XX,YY



.. _get_data_untar:

--------------------------------------------------
**untar**
--------------------------------------------------

  Unarchive from MS from a archive file.

  **enable**

    *bool*, *optional*, *default = False*

    Execute this segment

  **tar_options**

    *str*, *optional*, *default = -xvf*

    Options to parse to 'tar' command



.. _get_data_combine:

--------------------------------------------------
**combine**
--------------------------------------------------

  Virtually concatenate MSs and proceed with the combined MS

  **enable**

    *bool*, *optional*, *default = False*

    Execute this section

  **reset**

    *bool*, *optional*, *default = False*

    Delete concatenated MS if it exists. Else, proceed with existing MS

  **tar**

    Create a tarbal of the converted MS

    **enable**

      *bool*, *optional*, *default = False*

      Execute this section

    **tar_options**

      *str*, *optional*, *default = -cvf*

      Options to parse to the tar command

  **untar**

    Unarchive from MS from a archive file.

    **enable**

      *bool*, *optional*, *default = False*

      Execute this section

    **tar_options**

      *str*, *optional*, *default = -xvf*

      Options to parse to the tar command

