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

# Install CUDA

```bash
$ sudo <[:download_dir]>/cuda_8.0.44_linux.run
```
```bash
export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=/usr/local/cuda/lib64
export CUDA_HOME=/usr/local/cuda
```
# Install cuDNN

```bash
$ cd <DOWNLOAD DIR>
$ tar -zxvf ./cudnn-8.0-linux-x64-v5.1.tgz
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/
$ sudo chmod a+r /usr/local/cuda/include/cudnn.h
$ sudo chmod a+r /usr/local/cuda/lib64/libcudnn*
```
