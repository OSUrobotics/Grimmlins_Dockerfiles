# Docker Setup Instructions


## Linux Guide:

Other distros docker engine install instructions here: https://docs.docker.com/engine/

Docker Desktop here: https://docs.docker.com/desktop/

Nvidia Graphics Cards (do docker install first): https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html
  * The first step has you installing docker skip that part but do run: sudo systemctl --now enable docker


### Step by Step for Docker Engine install on Ubuntu:

1)  ```console,
    sudo apt-get remove docker docker-engine docker.io containerd runc
    ```

2)  ```console,
    sudo apt-get update
    ```

3) ```console,
    sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
    ```

4)  ```console,
    sudo mkdir -p /etc/apt/keyrings
    ```

5)  ```console,
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```

6)  ```console,
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

7)  ```console,
    sudo apt-get update
    ```

8)  ```console,
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
    ```
9)  ```console,
    sudo groupadd docker
    ```

10) ```console,
    sudo usermod -aG docker $USER
    ```

11) reboot the computer

<----------------------Docker is installed at this point----------------------------------->

Do the Nvidia [install](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) instructions if you have a Nvidia graphics card.

### Setup for using docker with vs code

1)  ```console,
    snap install --classic code
    ```

2) Go to the extensions with in vs code and install the following (They are all made by Microsft):
    * Docker
    * Remote - Containers

 
### Create a Container: [docker_howto.md](docker_howto.md)




## Guide(Windows):

Docker is able to use wsl2 as the backend allowing you to more efficiently run a Linux container on Windows. (Windows 11 required for gui support)

* Guide for setting up docker on Windows with wsl2: https://docs.docker.com/desktop/windows/wsl/
 * Guide for setting up wslg(gives gui support): https://github.com/microsoft/wslg



## How to get into docker container after the computer is turned on:
* If you want guis(for Linux):
  ```console
  xhost +local:docker &> /dev/null
  ```
* Start the container(for windows/wslg you can use the docker application or run this in the wsl terminal): 
  ```console
  sudo docker start <name_of_container>
  ```
* Access the bash of the container:
  ```console
  sudo docker exec -it <name_of_container> bash
  ```
   
## Useful commands:
* See running containers: 
  ```console
  sudo docker ps
  ```
* See all containers on computer: 
  ```console
  sudo docker container list -a
  ```
* Stop the container once you are done:
  ```console
  sudo docker stop <name_of_container>
  ```

## Useful Tips:
* When working with a usb device the easiest method is to give the container --privileged access when doing the docker run command. (This method does have security risks) Ensure to plug in the device before executing the "docker start <container name>".
  * If the container is already running use the stop command plug in usb device then execute the start command.

## References for this Guide:

* https://github.com/koenlek/docker_ros_nvidia
* https://docs.docker.com/engine/install/ubuntu/
* https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html
* https://docs.docker.com/engine/install/linux-postinstall/