---
layout: archive
title: "Lab Information"
permalink: /lab/
author_profile: false
---

{% include base_path %}

## Server Info ##

The lab has two multi-GPU servers on campus dedicated to research use: El Capitan and Half Dome.

### Logging In ###

You can log in with your Cal Poly credentials.  You need to be on the [Cal Poly VPN](https://cpvpn.calpoly.edu) if you are off campus.

### Storage ###

You will want to work on the local storage rather than your home directory which is network storage.  Each user has a directory at

    /data/<username>
  
Datasets can be stored under
  
    /data2

or

    /data3
    
    
### Conda ###

We are moving towards using Anaconda instead of Docker to manage Python configurations.

You first need to install Miniconda.  First run:

    /data/install_conda.sh
    
Then, after exiting out and reconnecting, run:

    conda update -y conda

#### Creating Conda environments ####


### Docker ###

Docker should only be used if you can't get a working set up with conda.

To use Docker, you need to create a Dockerfile and store it in a sub-directory.   For example, create a text file at "docker/Dockerfile."  Here is an example Dockerfile for Tensorflow:
      
    FROM tensorflow/tensorflow:latest-gpu-py3
    RUN apt-get update ; apt-get install vim git wget -y
    RUN pip install --upgrade scikit-image tqdm opencv-python

To build the Dockerfile:
      
    docker build docker -t <tag>

You can choose whatever you want for the tag.
      
To start Docker:
      
    docker run -u $(id -u):$(id -g) --rm --gpus device=<gpu> -it -v /data:/data -v /data2:/data2 -v /data3:/data3 -e USER=$USER -e HOME=/data/$USER -w $PWD <tag> bash
    
Set <gpu> to the GPU number that you want to use (0,1,2, or 3).  You can use 
    
    nvidia-smi
    
to check GPU availability.

### tmux ###
      
You can run Docker sessions inside of “tmux”.  Use ctl-b ctl-d to leave tmux and “tmux attach” to get back into it.  You can finds lots other [keyboard commands for tmux](https://gist.github.com/MohamedAlaa/2961058).
