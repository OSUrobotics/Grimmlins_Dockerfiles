* Start gui capabilities for docker containers (host os terminal):
    ```console
    xhost +local:docker &> /dev/null
    ```

* Build docker image:
    ```console
    docker build -t <image_name> .
    ```
    * If you want to push to docker hub use this format: (repo_name is like the image_name)
        ```console
        docker build -t <dockerhub_username>/<repo_name>:<tag_name> .
        ```

* Create a container from an image:
    ```console
    docker run -it --name <container_name> <image_name>
    ```
    * If you want gui support and you have a Nvidia graphics card use these commands instead
        ```console
        DOCKER_COMMON_ARGS="--gpus all --env=NVIDIA_VISIBLE_DEVICES=all --env=NVIDIA_DRIVER_CAPABILITIES=all --env=DISPLAY --env=QT_X11_NO_MITSHM=1 -v /tmp/.X11-unix:/tmp/.X11-unix:rw"

        docker run -it --net=host --privileged $DOCKER_COMMON_ARGS --name <name_of_container> <image_name>
        ```

* Open an additional terminal in the container:
    ```console
    docker exec -it <container_name> bash
    ```

* Start container:
    ```console
    docker start <container_name>
    ```

* Stop container:
    ```console
    docker stop <container_name>
    ```

* See running containers:
    ```console
    docker ps
    ```

* See all containers on computer:
    ```console
    docker container ls -a 
    ```
    
* See all images on computer:
    ```console
    docker image ls -a
    ```

* Delete container:
    ```console 
    docker rm <container_name or container_ID>
    ```

* Delete Image:
    ```console
    docker rmi <image_name or image_ID>
    ```

* Push image to docker hub:(make sure you made a repo on docker hub, that you named the image corretly and you signed into docker on your computer)
    ```console
    docker push <dockerhub_username>/<repo_name>:<tag_name>
    ```
