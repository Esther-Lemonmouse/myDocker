FROM lemonmouse/miniconda37:cuda11.3.1-cudnn8-ubuntu20.04
LABEL Author=lemonmouse

################################################################################
# This Dockerfile is used to build an image with pytorch_latest-cuda11.3-cudnn8 and kaggle.
# So PLEASE MAKE SURE you have created your kaggle API token and move it into 

# Reference Pages:
# https://github.com/microsoft/Swin-Transformer
################################################################################

# activate bash shell (for conda use)
SHELL [ "bash", "-c" ]

# kaggle preparation
RUN mkdir /root/.kaggle
COPY kaggle.json /root/.kaggle/

# install pytorch and kaggle command line
RUN source activate base && \
    conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch -y && \
    pip install kaggle

# clean caches
RUN conda clean -a -y && \
    rm -rf /root/.cache/*

# # Create a bash commandline as default
# CMD [ "/bin/bash", "-c" ]