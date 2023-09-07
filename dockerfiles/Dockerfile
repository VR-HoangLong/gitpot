FROM ubuntu:20.04

# Non-interactive installation mode
ENV DEBIAN_FRONTEND=noninteractive

# Update apt database
RUN apt update

# Install essentials
RUN apt install -y git git-lfs sudo

# Set the locale
RUN locale-gen en_US.UTF-8

# Install python
RUN apt install -y python-is-python3
    
# Install other dependencies
RUN apt-get install -y ccache bc flex cpio m4 libncurses5

# Create user gitpod
RUN useradd -l -u 33333 -G sudo -md /home/gitpod -s /bin/bash -p gitpod gitpod && \
    # passwordless sudo for users in the 'sudo' group
    sed -i.bkp -e 's/%sudo\s\+ALL=(ALL\(:ALL\)\?)\s\+ALL/%sudo ALL=NOPASSWD:ALL/g' /etc/sudoers

# Switch to gitpod user
USER gitpod

# Clean up unnecessary installation products
RUN rm -Rf /var/lib/apt/lists/*
