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
## AI environment with miniconda (a different approach) : 

Install Miniconda from [docs.conda.io/en/latest/miniconda](https://docs.conda.io/en/latest/miniconda.html) and [NVIDIA CUDA toolkit](https://developer.nvidia.com/cuda-downloads)

We can install CUDA by running ` $ sudo apt install nvidia-cuda-toolkit` and after installing CUDA, run to verify the install: ` $ nvcc -V`. You'll see an output such as :

```
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2021 NVIDIA Corporation
Built on Sun_Jul_22_21:07:16_PDT_2019
Cuda compilation tools, release ‘version’
```

Now we’ll download NVIDIA cuDNN : [https://developer.nvidia.com/cudnn](https://developer.nvidia.com/cudnn) - [[download](https://developer.nvidia.com/rdp/cudnn-download)] and ` $ tar -xvzf cudnn-10.1-linux-x64-'version'.tgz` to extract the cudnn files.
Now, we’ll copy the extracted files to the CUDA installation path:

```bash
$ sudo cp cuda/include/cudnn.h /usr/lib/cuda/include/
$ sudo cp cuda/lib64/libcudnn* /usr/lib/cuda/lib64/
```
Setting up the file permissions of cuDNN:
```bash
$ sudo chmod a+r /usr/lib/cuda/include/cudnn.h /usr/lib/cuda/lib64/libcudnn*
```

Get the environment ready:

Export CUDA environment variables. To set them, run:

```bash
$ echo 'export LD_LIBRARY_PATH=/usr/lib/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
$ echo 'export LD_LIBRARY_PATH=/usr/lib/cuda/include:$LD_LIBRARY_PATH' >> ~/.bashrc
```

we can also set the environment with conda and jupyter notebook.

After installing Miniconda, open the command prompt : ` $ conda install -y jupyter`.

```bash
    
    $ conda create --name tensorflow python=3.8
    $ conda activate tensorflow
    $ conda install nb_conda
    $ conda install -c anaconda tensorflow

```

To add additional libraries, update or create the ymp file in your root location, use: ` $ conda env update --file tools.yml`

To check GPU with tensorflow :

```python

    import sys

    import tensorflow.keras
    import pandas as pd
    import sklearn as sk
    import tensorflow as tf


    tf.config.list_physical_devices("GPU")

    print(f"Tensor Flow Version: {tf.__version__}")
    print(f"Keras Version: {tensorflow.keras.__version__}")
    print()
    print(f"Python {sys.version}")
    print(f"Pandas {pd.__version__}")
    print(f"Scikit-Learn {sk.__version__}")
    gpu = len(tf.config.list_physical_devices('GPU'))>0
    print("GPU is", "available" if gpu else "NOT AVAILABLE")
```


## AI Environment In Ubuntu / Debian based systems:

A light and straightforward setup for ubuntu systems to follow:

```bash
    $ sudo apt update && sudo apt upgrade
    $ sudo add-apt-repository ppa:graphics-drivers/ppa
    $ sudo apt update
    $ sudo apt install nvidia-driver-470

    to install CUDA:
    $ wget https://developer.download.nvidia.com/compute/cuda/11.2.0/local_installers/cuda_11.2.0_460.27.04_linux.run
    $ sudo sh cuda_11.2.0_460.27.04_linux.run

    $ cd $HOME/NVIDIA_CUDA-11.2_Samples/5_Simulations/smokeParticles (to test CUDA)
    $ make all && make run

    Update the environment variables, and add the following lines to ~/.bashrc
   
    export PATH=/usr/local/cuda-11.2/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
    export CUDA_HOME=/usr/local/cuda
    export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
   
   
    $ source ~/.bashrc

    to install CUDNN:
    $ tar -zvxf cudnn-11.2-linux-x64-v8.1.0.77.tgz
    $ sudo cp -P cuda/include/cudnn.h /usr/local/cuda-11.2/include
    $ sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-11.2/lib64/
    $ sudo chmod a+r /usr/local/cuda-11.2/lib64/libcudnn*
    $ nvcc -V

    to install anaconda:
    $ wget https://repo.anaconda.com/archive/Anaconda3-2022.10-Linux-x86_64.sh
    $ bash Anaconda3-2022.10-Linux-x86_64.sh

    create a conda environment:
    $ conda create --name deep-learning55
    $ conda activate deep-learning55

    $ pip3 install tensorflow
    $ pip3 install keras
    $ pip install torch

    $ pip install jupyterlab --user (jupyter lab over jupyter notebook)
    $ jupyter lab
```