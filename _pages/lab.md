---
layout: archive
title: "Lab Information"
permalink: /lab/
author_profile: false
---

{% include base_path %}

## Server Info ##

The lab has a multi-GPU server on campus dedicated to research use called El Capitan.

### Logging In ###

You can log in with your Cal Poly credentials.  You need to be on the [Cal Poly VPN](https://cpvpn.calpoly.edu) if you are off campus.

### Storage ###

You will want to work on the local storage rather than your home directory which is network storage.  Each user has a directory at

    /data/<username>
  
Datasets can be stored under
  
    /data2

### Docker ###

Everything is done through Docker on the server.
      

To use Docker, you need to create a Dockerfile and store it in a sub-directory.   For example, create a textfile at "docker/Dockerfile."  Here is an example Dockerfile for Tensorflow:
      
    FROM tensorflow/tensorflow:latest-gpu-py3
    RUN apt-get update ; apt-get install vim git wget -y
    RUN pip install --upgrade scikit-image tqdm opencv-python

To build the Dockerfile:
      
    docker build docker -t <tag>

You can choose whatever you want for the tag.
      
To start Docker:
      
    docker run -u $(id -u):$(id -g) --rm --gpus=1 -it -v /data:/data -v /data2:/data2 -e USER=$USER -e HOME=/data/$USER -w $PWD <tag> bash

### tmux ###
      
You can run Docker sessions inside of “tmux”.  Use ctl-b ctl-d to leave tmux and “tmux attach” to get back into it.  You can finds lots other [keyboard commands for tmux](https://gist.github.com/MohamedAlaa/2961058).
