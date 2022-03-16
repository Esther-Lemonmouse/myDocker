FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
LABEL Author=lemonmouse
################################################################################
# This Dockerfile is used as a base Image to build a deeplearning developement Container under Ubuntu 18.04-PyTorch v1.7.1-CUDA 10.1-cuDNN7.

# Reference Pages:
# https://github.com/microsoft/Swin-Transformer
# https://www.zhihu.com/question/460864869
# https://www.jianshu.com/p/1015dd0670db
################################################################################

# activate bash shell (for conda use)
SHELL ["bash", "-c"]

# Initialize workspace
RUN mkdir -p /workspace/presrc/
WORKDIR /workspace

# Install useful dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget vim && \
    apt-get clean

# Use Internet to get package
RUN wget --no-check-certificate -O /workspace/miniconda3.sh https://repo.anaconda.com/miniconda/Miniconda3-py37_4.11.0-Linux-x86_64.sh

# Install miniconda3 for python 3.7
RUN /bin/bash /workspace/miniconda3.sh -b -p /usr/local/bin/miniconda3
# For more information about this shell's parameters, please use "bash miniconda3.sh --help" or open the headerfile to obtain detailed information.

# Add the conda interpreter into the PATH
ENV PATH=/usr/local/bin/miniconda3/bin:$PATH

# Activate the PATH
RUN source ~/.bashrc

# Install PyTorch 1.7.1 with CUDA 10.1
RUN source activate base && \
    conda install pytorch==1.7.1 torchvision==0.8.2 torchaudio==0.7.2 cudatoolkit=10.1 -c pytorch -y

# clean the caches
RUN rm /workspace/miniconda3.sh && \
    rm -rf /tmp/* /var/cache/*  /usr/share/doc/* /usr/share/man/* /var/lib/apt/lists/* && \
    conda clean -a -y