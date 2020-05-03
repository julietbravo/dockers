# The instructions below build the image from the Ubuntu 18.04 LTS image.
# Use Ubuntu as the base
FROM ubuntu:latest

# Complete install of required packages.
RUN apt-get update

RUN DEBIAN_FRONTEND=noninteractive apt-get -y install \
        gfortran fftw3 libfftw3-dev libnetcdf-dev libnetcdf-c++4 libnetcdf-c++4-dev cmake libboost-dev libopenmpi-dev openmpi-bin git vim python3-pip
RUN pip3 install numpy netcdf4

# Add user and allow sudo
RUN useradd -p $(openssl passwd -1 bart) -ms /bin/bash bart
RUN usermod -aG sudo bart

# User actions.
USER bart
WORKDIR /home/bart

# Suppress sudo message.
RUN touch .sudo_as_admin_successful

# Clone MicroHH source code.
RUN git clone https://github.com/microhh/microhh2

RUN echo "PS1='\u@\h:\w$ '" >> .bashrc
