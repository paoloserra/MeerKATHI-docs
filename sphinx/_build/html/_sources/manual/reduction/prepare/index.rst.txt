.. meerkathi documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
=========================
Prepare pipeline and data
=========================
 
.. toctree::
   :maxdepth: 1

**[relevant workers:** :ref:`general`, :ref:`get_data`, :ref:`observation_config`\ **]**
 
A run of MeerKATHI must always start by setting up a number of directory and file
names. This is done through the :ref:`general` and :ref:`get_data` workers.

In the :ref:`general` worker users give:

* if necessary, the directory where to find the files that should be converted to .MS
  format (*general:data_path*);
* the directory where to find/write the .MS files (*general:msdir*);
* the directory where to write all output data products (*general:output*);
* the directory where to find various input files, such as AOflagger strategies etc.
  (*general:input*);
* the prefix for the output data products (*general:prefix*).

If they do not exist yet, the above directories can be created by setting
*general:init_pipeline* to *true*.

In the :ref:`get_data` worker users give the name of the .MS files to be processed
(*get_data:dataid*). Furthermore, the following optional steps are available:

* if conversion from HDF5/MVF format to .MS is necessary it can be enabled through the
  *get_data:mvftoms* parameter; further conversion options allow users to:

  + create a .MS.TAR file,
  + convert only visibilities in a channel range,
  + discard cross-polarisation products;

* if an .MS.TAR file already exists and should be untar-ed, this can be achieved with the
  *get_data:untar* parameter;
* if multiple .MS files are given as input, they can be virtually concatenated with
  *get_data:combine parameter*.
  
Finally, before starting the actual data processing users need to provide some necessary
info about the content of the input .MS files through the :ref:`observation_config` worker
(e.g., target and calibrators name, channelisation, etc.). In principle, this can be done
by editing the relevant parameters of this worker. In fact, MeerKATHI can automatically extract
most of these info from the .MS files themselves. To do so users should enable the
*observation_config:obsinfo* parameter. This writes a .JSON and a .TXT file to disc. Once
the .JSON file is on disc, parameters set to *auto* in the :ref:`observation_config`
worker will be automatically read from that file.

Note that the reference antenna information is often missing from the metadata. In those
cases, users should carefully select a good reference antenna for calibration and set it
with the *observation_config:reference_antenna* parameter.

**[missing from this page: vampirisms, primary beam]**
