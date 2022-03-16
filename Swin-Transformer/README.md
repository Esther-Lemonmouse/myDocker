# Swin-Transformer Docker Image

本Docker镜像基于NVIDIA Docker Image构建，可作为运行Swin-Transformer的Docker容器的基本镜像。为减少构建复杂度，请根据自身需求，参考不同子文件夹下的Dockerfile构建特定的开发环境。

本镜像也可用于其他需求PyTorch1.7.1-CUDA10.1-cuDNN7深度学习环境的搭建。请通过Dcokerfile构建自定义需求。亦可使用该示例为模板进行对应调整，从而获得自己所需要的其他NVIDIA docker容器。

_**NB.** 默认执行宿主机为Ubuntu操作系统。对于Windows操作系统，建议使用WSL2执行构建容器操作，可以开启容器显卡支持，获得更好的操作体验。_

## 构建步骤
1. 构建Image
    ```bash
    # if you want to change the IMAGE_NAME, please modify FROM <IMAGE_NAME> in later Dockerfiles if you need to build a specific swin container
    cd ../Swin-Transformer/
    docker build --rm -t lemonmouse/swin-base-image:torch1.7.1-cuda10.1-cudnn7-ubuntu18.04 .
    ```

2. 根据需要运行的Swin-Transformer种类 (Swin-T, S, B, L)，使用对应子文件夹下Dockerfile构建特定Image。
    ```
    ../Swin-Transformer/
        |-Image_Classification
        |-Object_Detection (TBC)
        |-Semantic_Segmentation (TBC)
        |-(TBC)
    ```

## 参考资料
本镜像的搭建主要参考了以下资料。

<https://github.com/microsoft/Swin-Transformer>  
<https://www.zhihu.com/question/460864869>  
<https://www.jianshu.com/p/1015dd0670db>