.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Spectral line imaging
=========================
 
.. toctree::
   :maxdepth: 1

**[relevant workers:** :ref:`image_HI`\ **]**

---------------------
Continuum subtraction
---------------------
 
A run of MeerKATHI must always start by setting up a number of directory and file
names. This is done through the :ref:`general` and :ref:`get_data` workers.

In the :ref:`general` worker users give:

* if necessary, the *data_path* directory where to find the files that should be converted to .MS
  format (:ref:`general: data_path <general_data_path>`);
* the *msdir* directory where to find/write .MS files (:ref:`general: msdir <general_msdir>`);
* the *output* directory where to write all output data products (:ref:`general: output <general_output>`);
* the *input* directory where to find various input files, such as AOflagger strategies etc.
  (:ref:`general: input <general_input>`);
* the prefix for the output data products (:ref:`general: prefix <general_prefix>`).

If they do not exist yet, the above directories can be created by setting
:ref:`general: init_pipeline <general_init_pipeline>` to *true*. This also copies
files from the meerkathi/data/meerkat_files directory to the *input* directory set above.

In the :ref:`get_data` worker users give the name of the .MS files to be processed
(:ref:`get_data: dataid <get_data_dataid>`). Furthermore, the following optional steps are available:

* convert from HDF5/MVF format to .MS (:ref:`get_data: mvftoms <get_data_mvftoms>`);
  this step includes the following additional conversion options:

  + create a .MS.TAR file,
  + convert only visibilities in a selected channel range,
  + discard cross-polarisation products;

* untar an existing .MS.TAR file (:ref:`get_data: untar <get_data_untar>`);
* virtually concatenate all .MS input files (:ref:`get_data: combine <get_data_combine>`);
  optionally users can delete an existing concatenate file and tar/untar the concatenated file.

-------
Imaging
-------

Finally, before starting the actual data processing users need to provide some
info about the content of the input .MS files through the :ref:`observation_config` worker
(e.g., target and calibrators name, channelisation, etc.). In principle, this can be done
by editing the relevant parameters of this worker:
