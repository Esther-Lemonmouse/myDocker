FROM nvidia/cuda:11.3.1-cudnn8-devel-ubuntu20.04
LABEL Author=lemonmouse
################################################################################
# This Dockerfile is used as a base Image to build a deeplearning developement Container under Ubuntu 20.04-CUDA 11.3-cuDNN8 NVIDIA docker.

# this is also a template for people to determine their own image.

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
    apt-get install -y --no-install-recommends wget git && \
    apt-get clean

################################################################################
# if you wanna choose another conda version, refer the following instructions and change the downloading package's name. These commands work for conda, you may simply use vanilla python. Currently I don't know how to do that, you may install it by yourself.

# Use Internet to get package miniconda python3.7
RUN wget --no-check-certificate -O /workspace/miniconda3.sh https://repo.anaconda.com/miniconda/Miniconda3-py37_4.11.0-Linux-x86_64.sh

# Install miniconda3 for python 3.7
RUN /bin/bash /workspace/miniconda3.sh -b -p /usr/local/bin/miniconda3
# For more information about this shell's parameters, please use "bash miniconda3.sh --help" or open the headerfile to obtain detailed information.

# Add the conda interpreter into the PATH
ENV PATH=/usr/local/bin/miniconda3/bin:$PATH

# Activate the PATH
RUN source ~/.bashrc

# Activate base enviorment for further step
RUN source activate base

# clean the caches
RUN rm /workspace/miniconda3.sh && \
    rm -rf /tmp/* /var/cache/*  /usr/share/doc/* /usr/share/man/* /var/lib/apt/lists/* && \
    conda clean -a -y
################################################################################