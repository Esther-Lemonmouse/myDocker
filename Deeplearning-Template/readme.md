# 使用说明
本Dockerfile以NVIDIA docker作为基准镜像生成，示例的版本为nvidia/cuda:11.3.1-cudnn8-devel-ubuntu20.04，便于兼容pytorch工具包。使用该镜像可以生成一个含miniconda3-py3.7的python环境，便于接下来的进一步炼丹工作。如果你需要其他版本的python环境或是其他版本的基准镜像，可以根据Dockerfile进行自定义。


- 生成镜像
    ```bash
    # if you want to change the IMAGE_NAME, please modify FROM <IMAGE_NAME> in later Dockerfiles if you need to build a specific container
    cd ../Templates/
    docker build --rm -t lemonmouse/miniconda37:cuda11.3.1-cudnn8-ubuntu20.04 .
    ```

- 直接生成容器并打开bash终端
    ```bash
    # please replace the <USERNAME>(lemonmouse) with your own directory
    # please change IMAGE_NAME if you have changed it in previous docker build
    # please map the correct port number at -p xxx:xxx
    # -v <localpath>:<containerpath> is preferred as absolute path. also, please replace it by your own path
    docker run --gpus all --name DL-base -p 12345:12345 -v /home/lemonmouse/Data/share/:/workspace/share/ -it lemonmouse/miniconda37:cuda11.3.1-cudnn8-ubuntu20.04 /bin/bash
    ```