ARG ROS_DISTRO=jazzy
FROM osrf/ros:$ROS_DISTRO-desktop

ARG USERNAME=ros
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Install Docker inside of Docker so Makefile can build image to deploy code to robot controller
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y curl
RUN install -m 0755 -d /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
RUN chmod a+r /etc/apt/keyrings/docker.gpg
RUN echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install -y docker-ce docker-ce-cli

# Install ssh client so that Makefile can deploy code to robot controller
RUN apt-get install -y openssh-client

# Create a non root user with UID and GID that VSCode can change to match the host's UID and GID on start to
# avoid ownership and permission conflicts with the host's user
# RUN groupadd --gid $USER_GID $USERNAME \
#     && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/bash \
#     #
#     # Add sudo support (required for docker in docker)
#     && apt-get update \
#     && apt-get install -y sudo screen \
#     && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME \
#     #
#     # Add user to dialout group so they can access serial devices
#     && usermod -a -G dialout $USERNAME

# Install dependencies
RUN apt-get install -y 

# Run command to source ROS in each new terminal so you only have to source your local install
RUN echo ". /opt/ros/$ROS_DISTRO/setup.sh" >> /etc/profile

