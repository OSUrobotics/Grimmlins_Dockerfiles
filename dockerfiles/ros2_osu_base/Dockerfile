#Download base image ubuntu 22.04 Jammy
FROM ubuntu:22.04

RUN apt-get update && apt-get install
RUN apt-get install -y usbutils
RUN apt-get install -y nano
RUN apt-get install -y usbutils
RUN apt-get install -y libxtst6
RUN apt-get update && apt-get install -y vim
RUN apt-get -y install locales
# Set the locale
RUN sed -i '/en_US.UTF-8/s/^# //g' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8    
RUN apt-get install -y software-properties-common
RUN add-apt-repository universe
RUN apt-cache policy | grep universe
RUN apt-get update && apt-get install -y curl gnupg lsb-release 
RUN curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
RUN /bin/bash -c 'echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | tee /etc/apt/sources.list.d/ros2.list > /dev/null'
# Set time zone to prevent errors in python3-colcon install
RUN DEBIAN_FRONTEND=noninteractive TZ=America/Los_Angeles apt-get -y install tzdata
RUN apt update && apt install -y \
  build-essential \
  cmake \
  git \
  python3-colcon-common-extensions \
  python3-flake8 \
  python3-flake8-blind-except \
  python3-flake8-builtins \
  python3-flake8-class-newline \
  python3-flake8-comprehensions \
  python3-flake8-deprecated \
  python3-flake8-docstrings \
  python3-flake8-import-order \
  python3-flake8-quotes \
  python3-pip \
  python3-pytest \
  python3-pytest-cov \
  python3-pytest-repeat \
  python3-pytest-rerunfailures \
  python3-rosdep \
  python3-setuptools \
  python3-vcstool \
  wget
RUN /bin/bash -c 'mkdir -p ~/ros2_humble/src'
RUN /bin/bash -c 'vcs import --input https://raw.githubusercontent.com/ros2/ros2/humble/ros2.repos ~/ros2_humble/src'
RUN apt-get upgrade
RUN rosdep init
RUN rosdep update
RUN rosdep install --from-paths ~/ros2_humble/src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-6.0.1 urdfdom_headers"
RUN /bin/bash -c 'cd ~/ros2_humble && colcon build --symlink-install'
RUN /bin/bash -c '. ~/ros2_humble/install/local_setup.bash'
