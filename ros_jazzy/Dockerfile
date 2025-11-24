FROM osrf/ros:jazzy-desktop

ARG UID
ARG GID
ARG USERNAME

# Remove default user if exists
RUN deluser --remove-home ubuntu || true && \
    delgroup ubuntu || true

# Install necessary packages
RUN apt-get update && apt-get install -y \
    git \
    python3-virtualenvwrapper \
    python3-pip \
    unzip \
    xclip \
    wl-clipboard \
    zsh \
    zoxide

# Create a new user with specified UID and GID
RUN groupadd -o --gid $GID $USERNAME && \
    useradd -o --uid $UID --gid $GID -m -s /bin/zsh $USERNAME

# set sudo for the new user
RUN usermod -aG sudo $USERNAME && \
    echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/000-nopassword

# Switch to the new user
USER $USERNAME

# Set working directory
WORKDIR /home/$USERNAME

ENV RUNNING_IN_DOCKER true
ENV DOCKER_NAME jazzy

ENV XDG_RUNTIME_DIR=/run/user/$UID
RUN sudo mkdir -p $XDG_RUNTIME_DIR
RUN sudo chown -R $UID:$GID $XDG_RUNTIME_DIR
RUN sudo chmod 700 $XDG_RUNTIME_DIR

