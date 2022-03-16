FROM lemonmouse/swin-base-image:torch1.7.1-cuda10.1-cudnn7-ubuntu18.04
LABEL Author=lemonmouse

################################################################################
# This Dockerfile is used to build a Swin-Transformer Object Detection Image. However, the NVIDIA Apex should be installed in the container manually.

# Reference Pages:
# https://github.com/microsoft/Swin-Transformer
################################################################################

# activate bash shell (for conda use)
SHELL [ "bash", "-c" ]

# Install related dependencies (without Apex)
RUN pip install timm==0.3.2 opencv-python==4.4.0.46 termcolor==1.1.0 yacs==0.1.8 && \
    conda clean -a -y

# Create a bash commandline as default
CMD [ "/bin/bash", "-c" ]