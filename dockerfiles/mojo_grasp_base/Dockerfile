FROM osrf/ros:melodic-desktop-full

RUN apt update
RUN apt install -y nano
RUN apt install -y usbutils
RUN apt install -y libxtst6
RUN apt install -y python-pip
RUN pip install gdown
RUN /bin/bash -c 'mkdir ~/software; \
    cd ~/software; \
    gdown --id 1AnxKMQQtJQUdR1trnOASvoX2yCaA66Lz; \
    tar xf blender-2.93.7-linux-x64.tar.xz;\
    mv blender-2.93.7-linux-x64 ./blender-2.93; \
    echo "alias blender="~/software/blender-2.93/blender"" >> ~/.bashrc; \
    source ~/.bashrc; \
    sudo apt update; sudo apt install -y python3-pip;\
    cd ~/ ; git clone https://github.com/JCampbell9/robot_manipulator_generator.git;\
    cd ~/robot_manipulator_generator/; pip3 install -r requirements.txt;\
    pip3 install pybullet;\
    cd ~/software/; git clone https://github.com/bulletphysics/bullet3.git; cd ./bullet3/; python3 setup.py build; python3 setup.py install;\
    '