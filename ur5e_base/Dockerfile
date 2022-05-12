FROM osrf/ros:melodic-desktop-full

RUN apt update
# RUN apt install -y usbutils
RUN apt install -y nano
RUN apt install -y usbutils
RUN apt install -y libxtst6
RUN apt install -y python-pip
RUN echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

RUN sudo apt install -y ros-melodic-moveit
RUN sudo apt install -y ros-melodic-trac-ik-kinematics-plugin
RUN mkdir -p ~/ur5_ws/src
RUN cd ~/ur5_ws
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/ur5_ws; catkin_make'
RUN /bin/bash -c 'cd ~/ur5_ws/src; \
    git clone https://github.com/UniversalRobots/Universal_Robots_ROS_Driver.git Universal_Robots_ROS_Driver;\
    git clone git clone -b calibration_devel https://github.com/fmauch/universal_robot.git fmauch_universal_robot;\
    git clone https://github.com/ros-industrial/ur_msgs.git;'
RUN apt udate -qq
RUN rosdep update
RUN /bin/bash -c 'cd ~/ur5_ws; rosdep install --from-paths src --ignore-src -y;'
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/ur5_ws; catkin_make'
RUN echo "source ~/ur5_ws/devel/setup.bash" >> ~/.bashrc