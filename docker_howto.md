
## Linux

To simplify the container process add do the following to ~/.bashrc, allow for docker to publish a window and make a bash variable with most of the needed arguments for the container.

1)  Gives docker permission to publish gui windows.
    ```console 
    echo "xhost +local:docker &> /dev/null" >> ~/.bashrc
    ```

2)  Container arguments for graphics
    * Nvidia Graphics Cards:
        ```console,
        echo "DOCKER_COMMON_ARGS="--gpus all --env=NVIDIA_VISIBLE_DEVICES=all --env=NVIDIA_DRIVER_CAPABILITIES=all --env=DISPLAY --env=QT_X11_NO_MITSHM=1 -v /tmp/.X11-unix:/tmp/.X11-unix:rw"" >> ~/.bashrc
        ```
    * Intel Integrated Graphics:
        ```console,
        echo "DOCKER_COMMON_ARGS="--env="DISPLAY" --env="QT_X11_NO_MITSHM=1" -v "/tmp/.X11-unix:/tmp/.X11-unix:rw"" >> ~/.bashrc
        ```
3) Create a docker container:
    ```console,
    docker run -it --net=host --privileged $DOCKER_COMMON_ARGS --name <name_of_container> <docker_image_name>
    ```
    *   If you want to have a shared folder between your host computer and the container use the following instead:
        ```console,
        docker run -it --net=host -v <path_to_folder_on_host>:<path_to_folder_in_container> --privileged $DOCKER_COMMON_ARGS --name <name_of_container> <docker_image_name>
        ```
        * Both paths need to be absolute. For the container /root/ is the same as doing ~/.
    *   See [README.md](README.md) for the updated list of docker images
    *   <name_of_container> can be anything thing you would like as long as it is unique from any other container name.
    





        
4) To connect an aditional terminal to the container run:
    ```console
    sudo docker exec -it <name_of_container> bash
    ```

### For connecting vs code to the container:
1)  Open a vs code window
2)  Select "Docker" from the left hand side of the vs code window.
3)  Right click on the container and select "start" if it is not started
4)  Right click on a container that is started and select "Attach Visual Studio Code"
5)  The new window that opens will be attached to the container, meaning any terminals that you open from that vs code window will already be in the container.