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

To avoid having to type in your password, you can set up SSH keys. 

On your laptop, see if you already have a public key at ```~/.ssh/id_rsa.pub```.  If not, create it with ```ssh-keygen -t rsa``` and accept all the defaults.

Copy the contents of ```~/.ssh/id_rsa.pub``` to ``~/.ssh/authorized_keys``` on the server.

You should now be able to SSH to the server without entering your password.

### Storage ###

Your home directory under ```/home/<username>``` has a small disk quota.  You will want to work on the local storage rather than your home directory.  Each user has a directory at

    /data/<username>
  
Datasets can be stored under
  
    /data2

or

    /data3

### VS Code and Jupyter Notebooks ###

You can connect to the server using VS Code through the "Remote - SSH" extension.  Please disable the "Typescript and Javascript Language Services" extension before connecting:

- Navigate to "Extensions" (click the building blocks button in the left toolbar)
- Search for ```@builtin TypeScript```
- Disable the "Typescript and Javascript Language Services" extension

You can run Jupyter Notebooks through VS code.  Running your own a notebook server is complicated and not recommended.

### Conda ###

It is usually best to manage your Python environments using conda.  To install conda, run:

    /data/install_conda.sh
    
Then, after exiting out and reconnecting, run:

    conda update -y conda


#### Creating Conda environments ####

You can create a conda environment using "conda create."  For example:

    conda create --name tf tensorflow-gpu==2.2.0
    
will create an environment named "tf" that has a GPU-compatible version of Tensorflow 2.2.0 installed.

To use the environment, do:

    conda activate tf
    
For more dependencies, you can create a file that lists them named environment.yml:

    name: tf
    channels:
      - conda
      - conda-forge
    dependencies:
      - python==3.6
      - pip>=10.0
      - tensorflow-gpu==2.2.0
      -pip:
        -tensorflow-addons=0.10.0

Now do:

    conda env create
    
to create the environment using the environment.yml file that you created.

You can also simply do "conda install" or "pip install" to install dependencies inside the conda environment.  (Do "conda install pip" first to use pip.)

To select which GPU to use, you can do:

    export CUDA_VISIBLE_DEVICES=<0,1,2, or 3>
    
Use

    nvidia-smi
    
to check GPU availability.

### Docker ###

Docker should only be used if you can't get a working set up with conda.  You need to be added to the docker group in order to use docker.

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
      
You should run your sessions inside of “tmux” to avoid SSH timeout and be able to return to sessions after disconnecting.  Start a session with "tmux", use ctl-b ctl-d to leave tmux and “tmux attach” to get back into it.  You can finds lots other [keyboard commands for tmux](https://gist.github.com/MohamedAlaa/2961058).
    
### Uploading and downloading files ###
    
I like to use [Cyberduck](https://cyberduck.io/) to connect to the server via SFTP and download or upload files. 
    
