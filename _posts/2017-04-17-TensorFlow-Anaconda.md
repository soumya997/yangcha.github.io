---
layout: post
title: Install TensorFlow With Anaconda
date:   2017-04-17
---

[Anaconda = Package Manager + Environment Manager + Additional Scientific Libraries](http://stackoverflow.com/questions/38217545/the-different-between-pyenv-virtualenv-anaconda-in-python). Based on my experience, it makes the python package management much easier. Also conda is a general-purpose package management system, it is designed to manage packages and dependencies of software from any language.  

If you want to install [TensorFlow](https://www.tensorflow.org) on Ubuntu 16.04 along with Anaconda, here is an installation guide:


# Install Nvidia driver and Cuda (Optional)

If you want to use GPU to accelerate, follow instructions [here]({% post_url 2016-06-12-GTX-1080 %}) to install Nvidia drivers, CUDA 8 and cuDNN 5 (skip caffe installation there).

# Install Anaconda

Download Anaconda from [here](https://www.continuum.io/downloads). Choose Python 2.7 or 3.6 version 64-BIT INSTALLER to install it, then update it:

```bash
conda update conda
```

Install TensorFlow following the instructions [here](https://www.tensorflow.org/install/install_linux#InstallingAnaconda).

