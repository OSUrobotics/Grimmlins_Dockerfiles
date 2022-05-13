FROM osrf/ros:melodic-desktop-full

RUN apt-get update
# RUN apt install -y usbutils
RUN apt-get install -y nano
RUN apt-get install -y usbutils
RUN apt-get install -y libxtst6
RUN apt-get install -y python-pip
RUN echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc

RUN apt-get install -y ros-melodic-moveit
RUN apt-get install -y ros-melodic-trac-ik-kinematics-plugin
RUN mkdir -p ~/ur5_ws/src
RUN cd ~/ur5_ws
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/ur5_ws; catkin_make'
RUN /bin/bash -c 'cd ~/ur5_ws/src; \
    git clone https://github.com/UniversalRobots/Universal_Robots_ROS_Driver.git Universal_Robots_ROS_Driver;\
    git clone -b calibration_devel https://github.com/fmauch/universal_robot.git fmauch_universal_robot;\
    git clone https://github.com/ros-industrial/ur_msgs.git;'
RUN apt update -qq
RUN rosdep update
RUN /bin/bash -c 'cd ~/ur5_ws; rosdep install --from-paths src --ignore-src -y;'
RUN /bin/bash -c '. /opt/ros/melodic/setup.bash; cd ~/ur5_ws; catkin_make'
RUN echo "source ~/ur5_ws/devel/setup.bash" >> ~/.bashrc