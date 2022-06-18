# Grimmlins Dockerfiles

Contains instructions to [setup](docker_setup.md) docker onto your computer, how to use docker and the dockerfiles used to create the docker images found on our lab's [dockerhub](https://hub.docker.com/u/grimmlins) organization (grimmlins).

Dockers are similiar to virtual machines, but lighter weight(they share the host OS kernel). This will allow for your computer to be running the newest version of linux and still run ROS melodic in an Ubuntu 18.04 enviroment.
Another benefit is you can create an image per project that has all of the reqirements for that project installed and give it to someone else to run.

I encourage you to use docker for research allowing you to publish your container with the paper so others can more easily replicate what you have done.



## Table of Contents:

Docker Setup Instructions: [link](docker_setup.md)

Using Docker Instructions: [link](docker_howto.md)

### Robot Base Images:

Images have ROS Melodic installed and a workspace setup with the needed packages installed for the robot.


* ur5e: 
    * Dockerfile: [link](dockerfiles/ur5e_base/Dockerfile)
    * Docker Image: grimmlins/robot_base_images:ur5e
* Kinova Gen2:
    * Dockerfile: [link](dockerfiles/kinova_base/Dockerfile)
    * Docker Image: grimmlins/robot_base_images:kinova


### Project Base Images:

Images have the requested file structure and files by the main project owner.

* Infrastructure:
    * Dockerfile: [link](dockerfiles/infrastructure_base/Dockerfile)
    * Docker Image: grimmlins/infrastructure:base_image
