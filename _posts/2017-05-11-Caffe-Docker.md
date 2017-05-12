---
layout: post
title: Docker images of Caffe With Anaconda (Python 3 version)
---

Here is a link for docker images of [Caffe](http://caffe.berkeleyvision.org/) on Ubuntu 16.04 along with Anaconda (Python 3.6 version):

[https://hub.docker.com/u/yangcha/](https://hub.docker.com/u/yangcha/)

There are two versions: GPU version and CPU version. To run CPU version:

```bash
docker run -ti yangcha/caffe-cpu-conda bash
source activate condacaffe
python -c "import caffe;print(caffe.__version__)"
```

or for GPU support (You need a CUDA 8.0 capable driver and
[nvidia-docker](https://github.com/NVIDIA/nvidia-docker)):

```bash
nvidia-docker run -ti yangcha/caffe-gpu-conda bash
source activate condacaffe
python -c "import caffe;print(caffe.__version__)"
```

The Dockerfile for CPU version is [here](https://hub.docker.com/r/yangcha/caffe-cpu-conda/~/dockerfile/), the Dockerfile for GPU version is [here](https://hub.docker.com/r/yangcha/caffe-gpu-conda/~/dockerfile/).

