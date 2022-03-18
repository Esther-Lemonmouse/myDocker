FROM lemonmouse/miniconda37:cuda11.3.1-cudnn8-ubuntu20.04
LABEL Author=lemonmouse

################################################################################
# This Dockerfile is used to build an image with Swin-Unet based on requirements.txt.
# So PLEASE MAKE SURE you have moved it under the Workspace

# Reference Pages:
# https://github.com/HuCaoFighting/Swin-Unet
################################################################################

# activate bash shell (for conda use)
SHELL [ "bash", "-c" ]

COPY requirements.txt /workspace/

# install dependencies of Swin-Unet, for users out of CHN, remove or edit -i parameter
RUN source activate base && \
    pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/

# clean caches
RUN conda clean -a -y && \
    rm -rf /root/.cache/*

# # Create a bash commandline as default
# CMD [ "/bin/bash", "-c" ]