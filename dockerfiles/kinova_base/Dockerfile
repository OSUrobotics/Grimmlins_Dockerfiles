FROM osrf/ros:melodic-desktop-full

RUN apt-get update
# RUN apt install -y usbutils
RUN apt-get install -y nano
RUN apt-get install -y usbutils
RUN apt-get install -y libxtst6
RUN echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

RUN apt-get install -y ros-melodic-moveit
RUN apt-get install -y ros-melodic-trac-ik-kinematics-plugin
RUN mkdir -p ~/kinova_ws/src
RUN cd ~/kinova_ws
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/kinova_ws; catkin_make'
RUN /bin/bash -c 'cd ~/kinova_ws/src; \
    git clone https://github.com/Kinovarobotics/kinova-ros.git kinova-ros; \
    cd ~/kinova_ws/src/kinova-ros; \
    catkin_create_pkg kinova_scripts std_msgs rospy roscpp'
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/kinova_ws; catkin_make'