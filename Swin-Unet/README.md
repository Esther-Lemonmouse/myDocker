# 注意事项
1. requirments.txt**不要从原项目搬了**，如果我没看错报错信息的话，大概是在吐槽我的PyTorch版本太低了。。。除此之外，鉴于这个项目依托于Swin-Transformer的基本模型，因此还需要一些相关的依赖库安装盒盒盒。我自己根据划红线的部分更新了一下requirements，以后有需要会持续更新的。。。

# 使用说明
1. 创建镜像
    ```bash
    # if you want to change the IMAGE_NAME, please modify FROM <IMAGE_NAME> in later Dockerfiles if you need to build a specific swin container
    cd ../Swin-Unet/
    docker build --rm -t lemonmouse/    swin-unet:miniconda37-cuda11.3-cudnn8-ubuntu20.04 .
    # note that torch and torchvision will automatch the latest version
    ```

2. 创建容器
    ```bash
    # please replace the <USERNAME> with your own directory
    # please change IMAGE_NAME if you have changed it in previous docker build
    docker run --gpus all --name Swin-Unet -p 12345:12345 -v /home/lemonmouse/share/:/workspace/share/ -it lemonmouse/swin-unet:miniconda37-cuda11.3-cudnn8-ubuntu20.04 /bin/bash
    ```

3. 执行容器 (可选)
    ```bash
    docker exec -it Swin-Unet /bin/bash
    # or python
    ```