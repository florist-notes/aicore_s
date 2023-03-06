### To manage env with Anaconda : [[download](https://www.anaconda.com/products/distribution)] instead of virtualenv.

```bash
    $ sudo sh Anaconda3-2019.10-Linux-x86_64.sh
    $ cat >> ~/.bashrc << 'EOF'

    export PATH=$HOME/anaconda3/bin:${PATH}
    EOF

    $ source .bashrc
    $ conda upgrade -y --all
    $ conda create --name py37
    $ conda activate py37

    $ sudo apt install python3-pip

    $ conda install -c rapidsai -c nvidia -c conda-forge -c defaults rapids=0.11 python=3.7 cudatoolkit=10.1

    $ pip install torchvision

    $ conda create --name tf (new environment)
    $ conda activate tf
    $ pip install --upgrade tensorflow

```


### $ conda command pallette: [commands](https://docs.conda.io/projects/conda/en/latest/commands.html) sheet:

```bash
    $ conda info (verify if conda installed)
    $ conda install --help or $ COMMANDNAME --help
    $ conda install $PACKAGE_NAME (Install a package)
    $ conda install --name bio-env toolz (Install a new package (toolz) in a different environment
(bio-env))
    $ conda update --name $ENVIRONMENT_NAME $PACKAGE_NAME (Update a package)
    $ conda update conda (Update package manager)
    $ conda remove --name $ENVIRONMENT_NAME $PACKAGE_NAME (Uninstall a package)
    $ conda remove --name bio-env toolz boltons ( Remove one or more packages (toolz, boltons) from a specific environment (bio-env) )
    $ conda create --name $ENVIRONMENT_NAME python (Create an environment)
    $ conda env create --file bio-env.txt (Create environment from a text file)
    $ conda create --name py35 python=3.5  (Create a new environment named py35, install Python 3.5)
    $ conda create --name bio-env biopython (create a new environment, name
it bio-env and install the biopython package)
    $ source activate py35
    $ conda activate $ENVIRONMENT_NAME (Activate an environment)
    $ conda deactivate or $ source deactivate (Deactivate an environment)
    $ conda create --clone py35 --name py35-2 (Make exact copy of an environment)
    $ conda search $SEARCH_TERM (Search available packages)
    $ conda install --channel $URL $PACKAGE_NAME (Install package from specific source)
    $ list (List all packages and versions installed in active environment)
    $ conda list --name $ENVIRONMENT_NAME (List installed packages)
    $ conda list --export (Create requirements file)
    $ conda list --revisions (List the history of each change to the current environment)
    $ conda info --envs (List all environments)
    $ conda install pip (Install other package manager)
    $ conda install python=x.x (Install Python)
    $ conda update python (Update Python)
    $ conda list --explicit > bio-env.txt (Save environment to a text file)
```

Example flow with conda :

```bash
    $ curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o Miniconda3-latest-Linux-x86_64.sh
    $ bash Miniconda3-latest-Linux-x86_64.sh
    $ conda create --name tf python=3.9
    $ conda install -c conda-forge cudatoolkit=11.2.2 cudnn=8.1.0
    $ conda deactivate
    $ conda activate tf
    $ nvidia-smi
    $ conda install -c conda-forge cudatoolkit=11.2.2 cudnn=8.1.0
    $ mkdir -p $CONDA_PREFIX/etc/conda/activate.d
    $ echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/' > $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
    $ pip install --upgrade pip
    $ pip install tensorflow==2.11.*
    $ python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
    $ python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

```
