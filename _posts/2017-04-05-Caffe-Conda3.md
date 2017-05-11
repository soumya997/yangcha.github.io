---
layout: post
title: Install Caffe With Anaconda (Python 3 version)
---

If you want to install [Caffe](http://caffe.berkeleyvision.org/) on Ubuntu 16.04 along with Anaconda3(Python 3.6 version), here is an installation guide:


# Install Nvidia driver and Cuda (Optional)

If you want to use GPU to accelerate, follow instructions [here]({% post_url 2016-06-12-GTX-1080 %}) to install Nvidia drivers, CUDA 8RC and cuDNN 5 (skip caffe installation there).

# Install Anaconda

Download Anaconda from [here](https://www.continuum.io/downloads). Choose Python 3.6 version 64-BIT INSTALLER to install it. Then update it:

```bash
conda update conda
```

If you want to create an environment such as `testcaffe`, execute commands:

```bash
conda create -n testcaffe python=3.5
source activate testcaffe
```

Install OpenCV:

```bash
conda install -c menpo opencv3
```

# Install Dependencies

```bash
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install -y build-essential cmake git pkg-config

sudo apt-get install -y libprotobuf-dev libleveldb-dev libsnappy-dev protobuf-compiler

sudo apt-get install -y libatlas-base-dev 

sudo apt-get install -y --no-install-recommends libboost-all-dev

sudo apt-get install -y libgflags-dev libgoogle-glog-dev liblmdb-dev
```

# Build Caffe

Go to [https://github.com/BVLC/caffe](https://github.com/BVLC/caffe), download zip archive and unpack it. Or clone the source code. Enter the `<caffe-home>` directory in the terminal window:

```bash
mkdir build
cd build
cmake -D python_version=3 ..
make all
make install
```

Enter `<caffe-home>/python` directory to install Python packages:

```bash
conda install cython scikit-image ipython h5py nose pandas protobuf pyyaml jupyter
sed -i -e 's/python-dateutil>=1.4,<2/python-dateutil>=2.0/g' requirements.txt
for req in $(cat requirements.txt); do pip install $req; done
cd ../build
make runtest
```

If you want to use some other packages in the Conda evnviroment, you need to install them now, otherwise the packages might not find the dependences you installed in the evnviroment.

Add the module directory to your `$PYTHONPATH` by 

```bash
cd ../python
export PYTHONPATH=`pwd`${PYTHONPATH:+:${PYTHONPATH}}
```

# Test Run

First verify the installation:

```bash
python -c "import caffe;print(caffe.__version__)"
```

If the Caffe version number is shown up correctly, then change directory to `examples`, execute command:

```bash
jupyter notebook
```

Choose one of the notebook examples to test the Caffe installation.



