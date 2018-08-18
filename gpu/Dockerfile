FROM nvidia/cudagl:9.0-runtime-ubuntu16.04

MAINTAINER Arjun Sreekumar <ajsrk1207@gmail.com>

# PyTorch Dependencies - 
# 	1.  build-essential 
#       2.  cmake 
#       3.  git 
#       4.  curl 
#       5.  vim 
#       6.  ca-certificates 
#       7.  libnccl2=2.1.2-1+cuda9.0 
#       8.  libnccl-dev=2.1.2-1+cuda9.0 
#       9.  libjpeg-dev 
#       10. libpng-dev 
#       11. conda install - numpy pyyaml scipy ipython mkl
#       12. conda install -c pytorch pytorch torchvision cuda90 magma-cuda90
# Tensorflow Dependencies - 
#       1. build-essential 
#       2. curl 
#       3. libfreetype6-dev 
#       4. libpng12-dev 
#       5. libzmq3-dev 
#       6. pkg-config 
#       7. python 
#       8. python-dev 
#       9. rsync 
#       10. software-properties-common 
#       11. unzip 
#       12. conda install pip jupyter Pillow h5py ipykernel
#       13. conda install -c conda-forge matplotlib numpy pandas scipy
# Mayavi Dependencies - 
#       1. mesa-utils
#       2. libglu1-mesa
#       3. libqtgui4 

ENV LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 LANGUAGE=en_US.UTF-8

ENV PATH /opt/conda/bin:$PATH

ENV HOME /home

RUN echo "deb http://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64 /" > \ 
    /etc/apt/sources.list.d/nvidia-ml.list && \
    apt-get update --fix-missing && \
    apt-get install -y --no-install-recommends wget=1.17.1-1ubuntu1.4 bzip2=1.0.6-8 ca-certificates=20170717~16.04.1 \
    mesa-utils=8.3.0-1 libglu1-mesa=9.0.0-2.1 libqtgui4=4:4.8.7+dfsg-5ubuntu2 \
    git=1:2.7.4-0ubuntu1.4 \
    build-essential=12.1ubuntu2 cmake=3.5.1-1ubuntu3 curl=7.47.0-1ubuntu2.8 vim=2:7.4.1689-3ubuntu1.2 \
    libnccl2=2.2.13-1+cuda9.0 libnccl-dev=2.2.13-1+cuda9.0 libjpeg-dev=8c-2ubuntu8 libpng12-dev=1.2.54-1ubuntu1.1 \
    libfreetype6-dev=2.6.1-0.1ubuntu2.3 libzmq3-dev=4.1.4-7 pkg-config=0.29.1-0ubuntu1 python-dev=2.7.12-1~16.04 \
    rsync=3.1.1-3ubuntu1.2 software-properties-common=0.96.20.7 unzip=6.0-20ubuntu1 \
    locales=2.23-0ubuntu10 && \
    locale-gen en_US.UTF-8 && \
    \
    rm -rf /var/lib/apt/lists/* && \
    \
    echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/miniconda/Miniconda3-4.5.4-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh &&\
    \
    apt-get clean &&\ 
    conda config --add channels conda-forge && \
    conda update -n base conda && \
    conda install -y -c conda-forge \
    numpy \
    pandas \
    qt vtk pyvtk pyside envisage traitsui mayavi\
    matplotlib \
    scipy \
    scikit-learn \
    scikit-image \
    jsoncpp \
    tensorboardx \
    opencv \
    pyyaml \
    mkl_fft \
    mkl_random \
    jupyter \
    jupyterlab \
    jupyterhub \
    h5py \
    pyhamcrest && \
    conda install -y pytorch torchvision -c pytorch && \
    pip install mayavi && \
    pip --no-cache-dir install \
    https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.10.0-cp36-cp36m-linux_x86_64.whl


CMD [ "/bin/bash" ]
