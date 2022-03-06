# Swin-Transformer for Object Detection Docker Image

本Docker镜像可用于构建[Swin-Transformer for Object Detection](https://github.com/microsoft/Swin-Transformer/blob/main/get_started.md)所要求的基本开发环境 (不含NVIDIA Apex)。可以有效解决深度学习中多版本CUDA和cuDNN的冲突问题和NVIDIA Apex不兼容Windows的问题。

目前该方法最大的缺点是占用硬盘空间过大。~~(反过来说，如果你有足够大的硬盘，则这个问题就不再是问题了。)~~

## 准备工作
构建完成的基本镜像。若还未构建完成，请参考[Swin-Transformer Docker Image](../README.md)进行构建。

可通过`docker image ls --all`检查已有镜像和确认基本镜像的名称。

## 构建步骤
1. 构建Image
    ```bash
    # if you have changed the IMAGE_NAME of the base image, please modify FROM <IMAGE_NAME> in Dockerfile BEFORE execute following bash commands
    cd ../Swin-Transformer/Image_Classification/
    docker build --rm -t lemonmouse/swin-image:classification .
    ```

2. 创建容器
    ```bash
    # please replace the <USERNAME> with your own directory
    # please change IMAGE_NAME if you have changed it in previous docker build
    docker run --gpus all --name swin-od -p 12345:12345 -v /home/<USERNAME>/share/:/workspace/share/ -it lemonmouse/swin-image:classification
    ```
    如若无需容器目录挂载，也可执行以下指令
    ```bash
    # please change IMAGE_NAME if you have changed it in previous docker build
    docker run --gpus all --name swin-od -p 12345:12345 -it lemonmouse/swin-image:classification
    ```
    个人推荐使用目录挂载，便于模型微调和进一步开发。

    _**NB.** 关于Docker 在Linux中的GPU虚拟化技术相关信息，请参阅<https://docs.docker.com/engine/reference/commandline/run/#access-an-nvidia-gpu>。_
    
    _**NB.** 本教程**暂不支持**使用WSL2开启的docker运行。本容器搭载的PyTorch版本过低，无法正确执行Swin模型。相关内容和可能的解决方案可参考<http://t.csdn.cn/fgbYi>。 ~~关于如何使用WSL2开启远程Docker的详细步骤，请参阅 [Docker Desktop WSL 2 backend](https://docs.docker.com/desktop/windows/wsl/)。~~_

3. 在开启后的Container中执行如下安装命令
    ```bash
    cd /workspace/presrc/
    git clone https://github.com/NVIDIA/apex
    cd apex
    pip install -v --disable-pip-version-check --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" ./
    ```

## 参考资料
本镜像的搭建主要参考了以下资料。

<https://github.com/NVIDIA/apex>  
<https://developer.nvidia.com/cuda/wsl>