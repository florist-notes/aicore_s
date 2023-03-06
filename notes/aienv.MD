# AI Environment with CUDA, cudnn and python on linux

```
            ******** PLAN  ******** :


        System : https://github.com/florist-notes/aicore_s/blob/main/notes/ai_workstation/final_aistation.md

        OS : AlmaLinux 8.6 (RHEL 8) / ubuntu 20.04 LTS (Debian)
        GPU: 2 x NVIDIA® RTX™ A5500 with NVLink 24 GB GDDR6
        Processor : AMD Ryzen™ Threadripper™ PRO 5995WX Prozessor (2,70 GHz bis zu 4,50 GHz)

        env management : Anaconda (Miniconda)

        Target libraries:
        > CUDA Toolkit version: 11.4
        > cuDNN version: 8.2.4
        > Python version : 3.9
        > TensorRT version :  8.4.0
        > PyTorch version : 1.8.1
        > TensorFlow version : 2.4
        > OpenCV version: 4.5

```
My grpahics card (2x RTX A5500) supports until CUDA 11.6 ([.pdf](https://www.nvidia.com/content/dam/en-zz/Solutions/gtcs22/rtx-a5500/nvidia-rtx-a5500-datasheet.pdf)). Check what CUDA toolkit is supported by your graphics card, my selection: cuDNN : [8.2.4](https://developer.nvidia.com/compute/machine-learning/cudnn/secure/8.2.4/11.4_20210831/cudnn-11.4-linux-x64-v8.2.4.15.tgz) from [cudnn-archive](https://developer.nvidia.com/rdp/cudnn-archive) and [CUDA 11.4](https://developer.nvidia.com/cuda-11-4-0-download-archive), To download CUDA for RHEL 8:

```bash
        $ wget https://developer.download.nvidia.com/compute/cuda/11.6.0/local_installers/cuda-repo-rhel8-11-6-local-11.6.0_510.39.01-1.x86_64.rpm
        $ sudo rpm -i cuda-repo-rhel8-11-6-local-11.6.0_510.39.01-1.x86_64.rpm
        $ sudo dnf clean all
        $ sudo dnf -y module install nvidia-driver:latest-dkms
        $ sudo dnf -y install cuda
```
To extract cuDNN tar file:

```bash
        $ tar xvf cudnn-11.4-linux-x64-v8.2.4.15.tgz
        $ sudo cp -P cuda/lib64/* /usr/local/cuda/lib64/
        $ sudo cp cuda/include/* /usr/local/cuda/include/
```
Next, update the paths for CUDA library and executables:

```bash
        $ echo 'export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"' >> ~/.bashrc
        $ echo 'export CUDA_HOME=/usr/local/cuda' >> ~/.bashrc 
        $ echo 'export PATH="/usr/local/cuda/bin:$PATH"' >> ~/.bashrc 
        $ source ~/.bashrc
```

<img src="../img/resultnvidia.png" width=100%>

Once installed check CUDA : `$ cat /usr/local/cuda/version.json` and cuDNN : ` $ cat /usr/local/cuda/include/cudnn.h`. To check nvidia drivers : `$ nvidia-smi` and to check CUDA Compute toolkit : `$ nvcc --version`. To remove CUDA from system : 

```bash
            $ sudo apt-get --purge remove "*cublas*" "cuda*" "nsight*" (if downloaded from apt-get) 
            $ sudo apt-get --purge remove "*nvidia*" (remove nvidia-drivers)
            $ sudo rm -rf /usr/local/cuda* (if installed via source file)

```
The CUDA config file `$ cat /usr/local/cuda/version.json` returns a json with CUDA version information:

```bash
            {
            "cuda" : {
                "name" : "CUDA SDK",
                "version" : "12.1.0"
            },
            "cuda_cccl" : {
                "name" : "CUDA C++ Core Compute Libraries",
                "version" : "12.1.55"
            },
            "cuda_cudart" : {
                "name" : "CUDA Runtime (cudart)",
                "version" : "12.1.55"
            },
            "cuda_cuobjdump" : {
                "name" : "cuobjdump",
                "version" : "12.1.55"
            }
            .
            .
            .
```

## Step-by-step Guide :

The Advanced Packaging Tool (APT) is a high-level package management tool in Ubuntu and other Debian Linux distribution derivatives. Let's revise our apt commands here:

```
        $ ls  /etc/apt/apt.conf.d
        $ sudo apt update
        $ apt list --upgradable
        $ sudo apt upgrade -y

        To see progress bar in apt, configure: in /etc/apt/apt.conf.d in the 99progressbar file
        $ nano 99progressbar
        Dpkg::Progress-Fancy"1";
        $ sudo apt upgrade package_name
        $ sudo apt full-upgrade
        $ sudo apt install package_name
        $ sudo apt install package1 package2
        $ sudo apt install /full/path/file.deb
        $ sudo apt remove package_name
        $ sudo apt remove package1 package2
        $ sudo apt purge package_name
        $ sudo apt autoremove (remove unused packages)

```
The apt-get suite is also an APT command-line tool for handling packages in Linux systems. The software-properties-common package gives you better control over your package manager by letting you add PPA (Personal Package Archive) repositories. Deadsnakes is a PPA with newer releases than the default Ubuntu repositories. Install the supporting software with the command:

```bash
    $ sudo apt-get update
    $ sudo apt-get upgrade -y
```
### To install python 3 and basic libraries:

```bash
    $ sudo apt-get update
    $ sudo apt-get --assume-yes upgrade
    $ sudo apt-get --assume-yes install tmux build-essential curl vim  gcc-9 g++-9 python-is-python3 python3-virtualenv make binutils
    $ sudo apt-get --assume-yes install software-properties-common
    $ sudo apt-get install -y cmake gfortran git pkg-config
    $ sudo apt-get install -y python-dev software-properties-common wget 
    $ sudo apt-get autoremove
    $ sudo apt install python3.8

    OR  from source file
    
    $ wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz
    $ tar -xf Python-3.8.3.tgz
    $ cd python-3.8.3
    $ ./configure --enable-optimizations
    $ python3 --version
```




This is a guide to understand and build your AI environment with CUDA, cudnn and python. I have a [dnf guide for RHEL](./packagednf.MD) and an AI hardware guide [here](https://github.com/s-ai-kia/aicore_s) for extended learning.