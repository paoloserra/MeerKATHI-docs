## Download & Install

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
$ pip install <absolute path to meerkathi folder>[extra_diagnostics]
$ export PYTHONPATH='' # Ensure that you use venv Python
```
If the requirements cannot be installed on your system you may omit [extra_diagnostics]. This will disable report rendering.

4. Pull and/or build stimela images
  - **uDocker**[Recomended]
    ```
    $ stimela pull
    ```

  - **Singularity**[Recomeded]
    ```
    $ stimela pull --singularity --pull-folder <folder to store stimela singularity images>
    ```

  - **Docker**
    ```
    $ stimela pull
    $ stimela build
    ```

5. run meerkathi
  - **uDocker**[Recomended]
    ``` $ meerkathi -c path_to_configuration_file --container-tech udocker```

  - **Singularity**[Recomended]
    ```$ meerkathi -c path_to_configuration_file --container-tech singularity -sid <folder where singularity images are stored>```

  - **Docker**
    ```$ meerkathi -c< path to configuration file>```


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

  - **Singularity**[Recommeded]
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
    
    
