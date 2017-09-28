---
layout: post
title: Install Nvidia CUDA 8 and cuDNN 6
comments: true
---

Many deep learning libraries use Nvidia GPU to accelerate the computation. The [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit) needs to install to make use of the GPU. The [NVIDIA CUDA Deep Neural Network library (cuDNN)](https://developer.nvidia.com/cudnn) is a GPU-accelerated library of primitives for deep neural networks which is worth installing.  Current version of CUDA is 9 and current version of cuDNN is 7. But many deep learning libraries have yet to upgrade to the current versions of CUDA and cuDNN. So here I present a way to install CUDA 8 and cuDNN 6. 


* OS: Ubuntu 16.04 x86_64

* Download [CUDA 8.0](https://developer.nvidia.com/cuda-toolkit) and install as follows:
  
  ```bash
  wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn6_6.0.21-1%2Bcuda8.0_amd64.deb
  wget http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn6-dev_6.0.21-1%2Bcuda8.0_amd64.deb
  sudo dpkg -i cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
  sudo dpkg -i libcudnn6_6.0.21-1+cuda8.0_amd64.deb
  sudo dpkg -i libcudnn6-dev_6.0.21-1+cuda8.0_amd64.deb
  sudo apt-get update
  sudo apt-get install cuda=8.0.61-1
  sudo apt-get install libcudnn6-dev
  ```
  
* Reboot the system to load the NVIDIA drivers.
  
* Set up the development environment by modifying the `PATH` and `LD_LIBRARY_PATH` variables, also add them to the end of `.bashrc` file:

  ```bash
  export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}
  export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
  ```

* Test installation:

```bash
~$ nvidia-smi
Mon Jun 13 11:43:53 2016
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 367.27                 Driver Version: 367.27                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Quadro 5000         Off  | 0000:03:00.0      On |                  Off |
| 30%   64C   P12    N/A /  N/A |    376MiB /  2493MiB |      3%      Default |
+-------------------------------+----------------------+----------------------+
|   1  GeForce GTX 1080    Off  | 0000:04:00.0     Off |                  N/A |
| 27%   38C    P8     6W / 180W |      1MiB /  8113MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

