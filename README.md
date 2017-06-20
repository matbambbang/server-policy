server-policy
=========================================================================
Server policy for Data Mining &amp; Information Lab

# Basic setup

```bash
$ sudo apt-get install vim
$ sudo apt-get install perl
$ sudo apt-get install build-essential gcc g++ make binutils linux-headers-`uname -r`

$ vi ~/.bashrc

# add this to bashrc
export LC_ALL=C

$ source ~/.bashrc
```

## Install CUDA

The nvidia-driver will automatically be set up during the configuration.

```bash
$ sudo <[:download_dir]>/cuda_8.0.44_linux.run
```
```bash
$ vi ~/.bashrc

export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=/usr/local/cuda/lib64
export CUDA_HOME=/usr/local/cuda

$ source ~/.bashrc
```
After successfully executing the above, you should see

```bash
$ nvidia-smi

* (Result)
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 375.20                 Driver Version: 375.20                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  TITAN X (Pascal)    Off  | 0000:4B:00.0     Off |                  N/A |
| 67%   86C    P2   249W / 250W |   5026MiB / 12221MiB |     82%      Default |
+-------------------------------+----------------------+----------------------+
|   1  TITAN X (Pascal)    Off  | 0000:4C:00.0      On |                  N/A |
| 88%   90C    P2   225W / 250W |   3842MiB / 12213MiB |     78%      Default |
+-------------------------------+----------------------+----------------------+
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```
```bash
$ nvcc --version

* (Result)
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Sun_Sep__4_22:14:01_CDT_2016
Cuda compilation tools, release 8.0, V8.0.44
```

## Install cuDNN

```bash
$ cd <DOWNLOAD DIR>
$ tar -zxvf ./cudnn-8.0-linux-x64-v5.1.tgz
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/
$ sudo chmod a+r /usr/local/cuda/include/cudnn.h
$ sudo chmod a+r /usr/local/cuda/lib64/libcudnn*
```

## Github
```bash
$ sudo apt-get install git
$ git config --global alias.lg "log -10 --oneline --graph"
```
