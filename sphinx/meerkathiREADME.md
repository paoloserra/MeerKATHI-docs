## Download & Install
### Usage and publication policy
When using MeerKATHI/CARACal please be aware of and adhere to the [MeerKATHI publication policy](https://docs.google.com/document/d/12LjHM_e1G4kWRfCLcz0GgM8rlXOny23vVdcriiA8ayU).

### On Linux

0. Clone this repository
Use https and your github credentials, then go to the pipeline folder 'meerkathi'.
```
$ git clone https://github.com/ska-sa/meerkathi.git
$ cd meerkathi
```
1. Start and activate virtual environment outside the meerkathi directory
```
$ cd ..
$ virtualenv meerkathi-venv
$ source meerkathi-venv/bin/activate
$ pip install pip wheel setuptools -U
```
2. If working from master branch it may be necessary to install bleeding edge fixes from upstream dependencies. Please install the requirements.txt requirements:
```
$ pip install -U -r <absolute path to meerkathi folder>/requirements.txt
```
3. Install meerKATHI
```
$ pip install <absolute path to meerkathi folder>"[extra_diagnostics]"
$ export PYTHONPATH='' # Ensure that you use venv Python
```
If the requirements cannot be installed on your system you may omit [extra_diagnostics]. This will disable report rendering.

4. Pull and/or build stimela images

  - **Podman**[Recommended]
    ```
    $ stimela pull -p
    ```
    
  - **Singularity**[Recommended]
    ```
    $ stimela pull --singularity --pull-folder <folder to store stimela singularity images>
    ```

  - **uDocker**[Recommended]<note: no python3 support>
    ```
    $ stimela pull
    ```
    
  - **Docker**
    ```
    $ stimela pull -d
    $ stimela build
    ```

5. run meerkathi

  - **Podman**[Recommended]
    ``` $ meerkathi -c path_to_configuration_file --container-tech podman```

  - **Singularity**[Recommended]
    ```$ meerkathi -c path_to_configuration_file --container-tech singularity -sid <folder where singularity images are stored>```

  - **uDocker**[no python3 support]
    ``` $ meerkathi -c path_to_configuration_file --container-tech udocker```

  - **Docker**
    ```$ meerkathi -c< path to configuration file>```

### Troubleshooting

- **Stimela cache file**
When re-building/pullng/updating stimela (any stimela call above), sometimes problems will arise with the cache file of stimela, whose standard location is
```
~/.stimela
```
If you run into unexplicable errors when installing a stimela version, including a failed update (possibly resulting in a repeating error when running CARACal), do:
```
> rm ~/.stimela/*
> stimela ...
```

before re-building. If that does not work, re-building the dependencies might help.
```
> pip install --upgrade --force-reinstall -r <absolute path to meerkathi folder>/requirements.txt
> rm ~/.stimela/*
> stimela ...
```
### On Mac

0. create a python environment

`$ conda create env --name meer_venv`

1. activate environment

`$ source activate meer_venv`

2. clone `meerkathi`
```
$ git clone https://github.com/ska-sa/meerkathi.git
$ cd meerkathi
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

6. Pull and/or build stimela images
  - **uDocker**[Recommended]
    ```
    $ stimela pull
    ```
    
  - **Singularity**[Recommended]
    ```
    $ stimela pull --singularity --pull-folder <folder to store stimela singularity images>
    ```

  - **Docker**
    ```
    $ stimela pull
    $ stimela build
    ```

7. run meerkathi
  - **uDocker**[Recommended]
    ```$ meerkathi -c path_to_configuration_file --container-tech udocker```

  - **Singularity**[Recommended]
    ```$ meerkathi -c path_to_configuration_file --container-tech singularity -sid <folder where singularity images are stored>```
      
  - **Docker**
    ```$ meerkathi -c< path to configuration file>```
    
    
