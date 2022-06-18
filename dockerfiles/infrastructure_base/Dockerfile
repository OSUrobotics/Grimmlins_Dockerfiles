FROM osrf/ros:melodic-desktop-full

RUN apt update
RUN apt install -y usbutils
RUN apt install -y nano
RUN apt install -y usbutils
RUN apt install -y libxtst6
# RUN apt install -y python3-pip
RUN echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
# RUN source ~/.bashrc
RUN sudo apt install -y ros-melodic-moveit
RUN sudo apt install -y ros-melodic-trac-ik-kinematics-plugin
# added
RUN sudo apt install -y net-tools
# ---
RUN mkdir -p ~/infrastructure_ws/src
RUN cd ~/infrastructure_ws
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/infrastructure_ws; catkin_make'
RUN /bin/bash -c 'cd ~/infrastructure_ws/src; \
    git clone --recurse-submodules -b main https://github.com/OSUrobotics/infrastructure-packages.git; \
    apt install -y ros-melodic-flexbe-behavior-engine; \
    git clone https://github.com/FlexBE/flexbe_app.git '

# RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/infrastructure_ws; catkin_make'

RUN echo "source /root/infrastructure_ws/devel/setup.bash" >> ~/.bashrc
