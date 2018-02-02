DMIS SERVER POLICY
=========================================================================
Server policy for Data Mining &amp; Information Lab

## Server ip
|   server   |     ip            |      VGA    |    admin   |   user   |  user+   |
|:----------:|:-----------------:|:-----------:|:----------:|:--------:|:--------:|
|  gPower 0  | 163.152.163.108   | GTX Titan X |   jinhyuk  |  hyunjae |  miyoung |
|  gPower 2  | 163.152.163.112   | GTX Titan X |   yongqyu  |  buru    |  raehyun |
|  gPower 3  | 163.152.163.221   | GTX Titan X |   bumsoo   |  nayoung |  daehan  |
|  gPower 4  | 163.152.163.222   | GTX Titan X |   sunkyu   |  heewon  |          |
|  gPower 5  | 163.152.163.223   | GTX Titan X |  byounggun |  billal  |          |
|  gPower 6  | 163.152.163.210   | GTX 1080    |   wonjin   |          |          |

## Basic setup

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
or
$ sudo sh <[:download_dir]>/cuda_8.0.44_linux.run

*
Do you accept the previously read EULA?
accept/decline/quit: accept

Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 384.81?
(y)es/(n)o/(q)uit: y

Do you want to install the OpenGL libraries?
(y)es/(n)o/(q)uit [ default is yes ]: n

Do you want to run nvidia-xconfig?
This will update the system X configuration file so that the NVIDIA X driver
is used. The pre-existing X configuration file will be backed up.
This option should not be used on systems that require a custom
X configuration, such as systems with multiple GPU vendors.
(y)es/(n)o/(q)uit [ default is no ]:

Install the CUDA 9.0 Toolkit?
(y)es/(n)o/(q)uit: y

Enter Toolkit Location
 [ default is /usr/local/cuda-9.0 ]:

Do you want to install a symbolic link at /usr/local/cuda?
(y)es/(n)o/(q)uit: y

Install the CUDA 9.0 Samples?
(y)es/(n)o/(q)uit: y

Enter CUDA Samples Location
 [ default is /home/dmis ]:

Installing the NVIDIA display driver...
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
$ sudo tar -zxvf ./cudnn-8.0-linux-x64-v5.1.tgz (or .solitairetheme8)
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/
$ sudo chmod a+r /usr/local/cuda/include/cudnn.h
$ sudo chmod a+r /usr/local/cuda/lib64/libcudnn*
```

## Server welcome notice
```bash
$ sudo apt-get install figlet
$ sudo vi /etc/update-motd.d/00-header

# add this to bashrc
printf "\nWelcome to Ubuntu 16.04.5 LTS (GNU/Linux-Mint-18 x86_64)\n"
printf "This is the server for the Data Mining & Information System Lab.\n\n"
printf " * Documentation: https://github.com/meliketoy/server-policy\n\n"
printf "##############################################################\n"
figlet -f slant "G-POWER [:#]"
printf "\n\n"
printf " Data Mining & Information System Lab\n"
printf " GPU Computing machine : 163.152.163.[:ip]\n\n"
printf " Administrator   : [:admin]\n"
printf " Please read the document\n"
printf "    https://github.com/meliketoy/server-policy/README.md\n"
printf "##############################################################\n\n"
```

## Github
```bash
$ sudo apt-get install git
$ git config --global alias.lg "log -10 --oneline --graph"
```
