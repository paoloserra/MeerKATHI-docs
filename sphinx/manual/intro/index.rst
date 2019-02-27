.. meerkathi-docs documentation master file, created by
   sphinx-quickstart on Mon Feb 18 15:04:26 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.
 
============
Introduction
============
 
.. toctree::
   :maxdepth: 1
 
What is MeerKATHI?
------------------

MeerKATHI is a pipeline to reduce radio interferometry continuum and spectral line data in
full polarisation. It works on data from any radio interferometer as long as they are in
“measurement set” format.

In the simplest terms, MeerKATHI is a collection of Stimela scripts.
`Stimela <https://github.com/SpheMakh/Stimela>`_ is a platform-independent radio
interferometry scripting framework based on Python and Docker/Singularity.
Stimela allows users to
execute tasks from many different data reduction packages in Python without having to
install those packages individually (e.g., CASA, MeqTrees, AOflagger, SoFiA, etc.).
Using Stimela, the different software packages are available through a unified scheme.
MeerKATHI consists of a sequence of Stimela**-Python** scripts, which it links and runs sequentially **or in loops with certain stopping conditions (e.g. stop iterating on an image if the image quality is good enough)**.

Within MeerKATHI – and throughout this documentation – the individual Stimela**-Python** scripts are called
"workers". Each MeerKATHI worker corresponds to a specific section of the data reduction
process (e.g., flagging, cross-calibration, spectral line imaging, etc.). Each worker
executes several tasks from the interferometry packages included in Stimela (e.g., the
cross-calibration worker can calibrate delays, bandpass, gains and flux scale)**either sequentially or in a loop with certain exit conditions**.

~~In practice, u~~ **U**sers tell MeerKATHI what to do – and how to do it – via **specifying parameters in**a configuration file.
The configuration file has one section for each run of a worker. By editing the configuration
file users control the workers' options, deciding which tasks to run and with what settings.
A detailed explanation of the configuration file syntax is given in the :ref:`configfile`
section of this manual.

Normally, users won’t have to touch anything but the configuration file **and, in an ideal world, barely even that**. They can check
what~~’s~~**has** happened through a variety of data products, diagnostic plots and log files.
A list of all MeerKATHI data products is available at the :ref:`products` section of this manual.

~~In the rest of this Introduction~~**Below** we give a brief description of each worker. A more comprehensive
description is available in the :ref:`reduction` section of this manual. ~~, which follows
the flow of a typical data reduction process.~~ The full list of parameters available for
the individual workers through the configuration file can be found at the :ref:`workers`
section of this manual or following the links below. **REMARK: we should also have a topical list and an alphabetical list of parameters with links to their description. Don't know if makehtedocs generates this automatically.**

Brief description of workers
----------------------------

The following workers are available in MeerKATHI. Typically, they are executed in the
same order in which they are given below. Only the first three workers (general, get_data
and  observation_config) should always be executed **at least once**. All other workers are optional.

:ref:`general`
^^^^^^^^^^^^^^

~~This worker~~ **_general_** is used to set up the name of various input/output directories
and the prefix for the output data products (e.g., diagnostic plots, images, etc.).

:ref:`get_data`
^^^^^^^^^^^^^^^

~~This worker~~ **_get_data_** ~~is used to set~~**sets** up the name of the files to be processed and whether any
conversion to .MS format is necessary. It can also virtually concatenate several .MS files
together.

:ref:`observation_config`
^^^^^^^^^^^^^^^^^^^^^^^^^

~~This worker~~ **observation_config** ~~is used to set up~~ **collects** basic information on the content of the .MS files to be
processed (e.g., target and calibrators' name, channelisation, etc.). The worker can also
extract this information automatically from the .MS metadata. Finally, it can create a
primary beam image cube on a user-defined pixel- and frequency grid.


:ref:`prepare_data`
^^^^^^^^^^^^^^^^^^^

~~This worker~~**prepare_data** ~~is used to prepare~~**prepares** the data for calibration and imaging. For example, it can
recalculate UVW coordinates, add a BITFLAG column to the input .MS files, or add spectral
weights based on Tsys measurements.

:ref:`flagging`
^^^^^^^^^^^^^^^

~~This worker is used to flag~~**_flagging_** flags the data and ~~return~~**returns** statistics on the flags. As all other
workers, it can be run multiple times within a single MeerKATHI run (though this feature
is not necessarily useful for many other workers). It can flag data based on, e.g.,
channel-, antenna- and time selection, or using automated algorithms that run on
autocorrelations (to catch antennas with clear problems) or crosscorrelations.

:ref:`cross_cal`
^^^^^^^^^^^^^^^^

~~This worker~~**_cross_cal_** is used to cross-calibrate the data. Users can calibrate delays, bandpass,
gains and flux scale. The calibration can be applied to the calibrators' visibilities for
future inspection. Numerous parameters are available for users to decide how to calibrate.
Flagging based on closure errors is available in this worker.

:ref:`inspect_data`
^^^^^^^^^^^^^^^^^^^

~~This worker~~**_inspect_data_** produces diagnostic plots based on the calibrated calibrators' visibilities.

:ref:`split_target`
^^^^^^^^^^^^^^^^^^^

~~This worker is used to create~~**_split_target_ creates** new .MS files which contain the target's calibrated
visibilities only. Time and frequency averaging is available, as well as phase rotation to
a new phase centre.

:ref:`masking`
^^^^^^^^^^^^^^

~~This worker is used to create~~**_masking_ creates an a-priori clean mask based on NVSS or SUMSS catalogues, 
to be used during the continuum imaging/self-calibration loop. It can also merge the
resulting mask with a mask based on an existing image.

:ref:`self_cal`
^^^^^^^^^^^^^^^

~~This worker~~**_self_cal_** performs continuum imaging and standard (i.e., direction-independent)
self-calibration. Automated convergence of the calibration procedure is optionally
available. This worker can also transfer the resulting sky model and apply the calibration
to another .MS (e.g., if calibration and model are obtained from a coarse-channels .MS
file they can then be transfered to a fine-channels .MS file).

:ref:`image_HI`
^^^^^^^^^^^^^^^

~~This worker~~ **_image_HI_** is used to create spectra-line cubes. It can subtract the continuum via both
model and UVLIN-like subtraction, Doppler correct, flag solar RFI, perform
automated iterative cleaning with 3D clean masks, and, finally, run a spectral-line source
finder.
