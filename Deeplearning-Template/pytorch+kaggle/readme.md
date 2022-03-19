# 使用说明

- 将自己的kaggle.json文件移至目录下
    ```bash
    cp kaggle.json ../pytorch+kaggle/
    ```

- 构建镜像
    ```bash
    cd ../Templates/
    docker build --rm -t lemonmouse/torch-kaggle:miniconda37-cuda11.3.1-cudnn8-ubuntu20.04 .
    ```

- 加载容器并打开bash
    ```bash
    # please replace the <USERNAME>(lemonmouse) with your own directory
    # please change IMAGE_NAME if you have changed it in previous docker build
    # please map the correct port number at -p xxx:xxx
    # -v <localpath>:<containerpath> is preferred as absolute path. also, please replace it by your own path
    docker run --gpus all --name DL-torch-kaggle -p 12345:12345 -v /home/lemonmouse/Data/share/:/workspace/share/ -it lemonmouse/torch-kaggle:miniconda37-cuda11.3.1-cudnn8-ubuntu20.04 /bin/bash
    ```