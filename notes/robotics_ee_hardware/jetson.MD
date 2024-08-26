# j3tsonDream : Jetson Edge AI Accelerators

Here are some of the most useful Jetson commands for managing and working with the NVIDIA Jetson Orin:

### 1. System Information
Check system information:

```python
$ tegrastats
```
Continuously monitors system resource usage like CPU, GPU, RAM, and more.

Check JetPack version:

```python
$ dpkg-query --show nvidia-l4t-core
```
Displays the installed version of JetPack.

### 2. Power Management
Check available power modes:

```python
$ sudo nvpmodel -q --available
```
Lists available power modes.

Set power mode:

```python
$ sudo nvpmodel -m <mode>
```
Sets the power mode (replace <mode> with the appropriate mode number).

Check current power mode:

```python
$ sudo nvpmodel -q
```
###  GPU and Deep Learning
Run a specific model on the GPU:

```python
$ sudo nvidia-smi
```
Monitor GPU usage and manage GPU tasks.


[ [NVIDIA Jetson Guide](https://docs.nvidia.com/jetson/archives/r34.1/DeveloperGuide/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/quick_start.html) ] [[Jetson Developer Kit](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#intro)] [[Getting Started With NVIDIA Jetson Nano Developer Kit](https://gilberttanner.com/blog/jetson-nano-getting-started/)]


```python
//after every reboot
$ sudo jtop //check that the UI comes up, then hit q to quit
$ sudo nvpmodel -m <pmid> //0 is for MAXN check that this executes without a warning, if not reboot
$ sudo jetson_clocks --fan //disable DVFS and set fan speed to max
$ sudo mount /dev/nvme0n1p1 /media/ssd
 
//before starting the workload
$ sudo python3 dataload_resnet.py
 
//change power mode
$ sudo nvpmodel -m <pmid> //0 is for MAXN check that this executes without a warning, if not reboot
$ sudo jetson_clocks --fan //disable DVFS and set fan speed to max
```


```python
$ sudo jetson_clocks --show
```

