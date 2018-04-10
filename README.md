DMIS SERVER POLICY
=========================================================================
Server policy for Data Mining &amp; Information Lab

## Server ip
|   server   |     ip            |      VGA    |    admin   |   user   |  user+   |
|:----------:|:-----------------:|:-----------:|:----------:|:--------:|:--------:|
|  gPower 0  | 163.152.163.108   | GTX Titan X |   jinhyuk  |  hyunjae |  miyoung |
|  gPower 2  | 163.152.163.112   | GTX Titan X |   buru     |  gyeom   |    -     |
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

## Server welcome notice
```bash
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

## Multi-CUDA version

1. 아래 방법처럼 쿠다 9.0깔고 suda sh cuda-x.x.run --silent --toolkit --toolkitpath=/usr/local/cuda-x.x
2. /usr/local/cuda 이 심볼릭 링크를 /usr/local/cuda-8.0/ 이거로 되돌림 (1번과정떄문에 새 툴킷으로 바뀌었을것임)  
    ln -s /usr/local/cuda-8.0 /usr/local/cuda
3. 대신 내 환경의 환경설정을 바꿔서 다른 path의 툴킷을 사용. 
4. 이를 위해 ~/wonjinenv/bin/activate 파일의 제일 마지막 부분에 아래 코드들을 삽입(PATH=/usr/local/cuda-9.0/bin:$PATH 임에 주의)
```bash
export PATH=/usr/local/cuda-9.0/bin:$PATH  
export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64  
export CUDA_HOME=/usr/local/cuda-9.0  
```
    
https://blog.kovalevskyi.com/multiple-version-of-cuda-libraries-on-the-same-machine-b9502d50ae77
