## Requirements
**Provide a summary
* which hardware is recommended/required
* which operating systems are supported
**

## Add
**
* how to update MeerKATHI, see e.g. update from upstream part in https://github.com/ska-sa/meerkathi/wiki/Developing-MeerKATHI
* Troubleshooting
**

## Download & Install

### On Linux

0. Clone this repository
Use https and your github credentials, then go to the pipeline folder 'meerkathi'.
```
git clone https://github.com/ska-sa/meerkathi.git
cd meerkathi
```
1. Check out submodules
```
git submodule update --init --recursive 
```
2. Start and activate virtual environment outside the meerkathi directory
```
$ cd ..
$ virtualenv meerkathi-venv
$ source meerkathi-venv/bin/activate
$ pip install pip wheel setuptools -U
```
3. If working from master branch it may be necessary to install bleeding edge fixes from upstream dependencies. Please install the requirements.txt requirements:
```
$ pip install -U -r <absolute path to meerkathi folder>/requirements.txt
```
4. Install meerKATHI
```
$ pip install <absolute path to meerkathi folder>
$ export PYTHONPATH='' # Ensure that you use venv Python
```
5. Build Stimela
```
$ stimela build
```

### On Mac

0. create a python environment

`conda create env --name meer_venv`

1. activate environment

`source activate meer_venv`

2. clone `meerkathi`
```
git clone https://github.com/ska-sa/meerkathi.git
cd meerkathi
git submodule update --init --recursive 
```
3. Start and activate virtual environment
```
$ virtualenv meerkathi-venv
$ source meerkathi-venv/bin/activate
$ pip install pip wheel setuptools -U
```
4. If working from master branch it may be necessary to install bleeding edge fixes from upstream dependencies. Please install the requirements.txt requirements:
```
$ pip install -U -r <absolute path to meerkathi folder>/requirements.txt
```
5. Install meerKATHI
```
$ pip install <absolute path to meerkathi folder>
$ export PYTHONPATH='' # Ensure that you use venv Python
```

6. Build stimela

`stimela build`

7. run meerkathi

`meerkathi -c path_to_configuration_file`

WARNING: if `/etc/shadow` is not found:
```
pip install --upgrade git+https://github.com/SpheMakh/Stimela.git@issue-241
stimela clean -ac
stimela clean -aC
stimela build --no-cache
```

