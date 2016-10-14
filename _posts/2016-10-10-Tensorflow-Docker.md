---
layout: post
title: Tensorflow Docker Installation and Missing CUDNN Library
---

Installing multiple deep learning frameworks in a single system is a dependency hell. Docker provides a solution to this issue.

[Here](https://www.tensorflow.org/versions/r0.11/get_started/os_setup.html#docker-installation) is the instructions to install Tensorflow with Docker.

There is a bug in the gcr.io/tensorflow/tensorflow:latest-gpu docker image: 

>I tensorflow/stream_executor/dso_loader.cc:99] Couldn't open CUDA library libcudnn.so. LD_LIBRARY_PATH: /usr/local/nvidia/lib:/usr/local/nvidia/lib64:
>
>I tensorflow/stream_executor/cuda/cuda_dnn.cc:1562] Unable to load cuDNN DSO

The solution is to excute this command in Docker instance:

```bash
ln -s /usr/lib/x86_64-linux-gnu/libcudnn.so.4 /usr/lib/x86_64-linux-gnu/libcudnn.so
```

For devel verison, the following instructions are needed:

```bash
cd /usr/local/nvidia/lib64
export LD_LIBRARY_PATH=`pwd`${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
