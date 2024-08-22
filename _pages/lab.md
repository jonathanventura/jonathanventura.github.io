---
layout: archive
title: "Lab Information"
permalink: /lab/
author_profile: false
---

{% include base_path %}

# Lab Information #

El Capitan is our on-campus Linux server with four NVidia V100 GPUs (32 GB RAM each) dedicated to research use.  

Half Dome is our Windows workstation with two Nvidia RTX 3090 GPUs and a Meta Quest 2 headset.  This workstation is ideal for running ArcGIS Pro and virtual reality experiments.

## Frequently Asked Questions ##

Here answers to frequently asked questions about working on the El Capitan server.

### How do I log in? ###

You can log in with your Cal Poly credentials.  You need to be on the [Cal Poly VPN](https://cpvpn.calpoly.edu) if you are off campus.

To avoid having to type in your password, you can set up SSH keys:

* On your laptop, see if you already have a public key at ```~/.ssh/id_rsa.pub```.  If not, create it with ```ssh-keygen -t rsa``` and accept all the defaults.
* Copy the contents of ```~/.ssh/id_rsa.pub``` to ```~/.ssh/authorized_keys``` on the server.

You should now be able to SSH to the server without entering your password.

### I am out of disk quota, what do I do? ###

Your home directory under ```/home/<username>``` is on a shared network drive and has a small disk quota.  You shouldn't store your code or data in your home directory.

Instead, you should use the internal drives on El Capitan: ``/code`` and ``/data``.  We also have a network drive ``/data2``.

Each user has a directory at

    /code/<username>

where you can put your code, Github repository clones, etc.  If you need to download a dataset or create large files, put them in ``/data2``.  ``/data`` is currently near capacity and I plan to eventually replace it with a larger SSD where we can store datasets.

### How do I run a Juptyer notebook? ###

It is not easy to run a Jupyter server on El Capitan and I don't recommend it.  Instead, you should use VS Code to run notebooks (see next question.)

### How do I use VS Code on the server?  ###

You can connect to the server using VS Code through the "Remote - SSH" extension.  Please disable the "Typescript and Javascript Language Services" extension before connecting:

- Navigate to "Extensions" (click the building blocks button in the left toolbar)
- Search for ```@builtin TypeScript```
- Disable the "Typescript and Javascript Language Services" extension

### How do I install Python packages? ###

Don't use the system python.  Instead, install miniconda and create conda environments.

To install conda, run this script:

    sh /code/install_conda.sh
    
Then, after exiting out and reconnecting, run:

    conda update -y conda

VS Code should detect your conda environments so that you can select the appropriate Python kernel when running code.

### My program stops running when I disconnect from SSH -- how can I run a long process? ###
     
You should run your sessions inside of ``tmux`` to avoid SSH timeout and be able to return to sessions after disconnecting.  Start a session with ``tmux``, use ``ctl-b ctl-d`` to leave tmux and ``tmux attach`` to get back into it.  You can finds lots other [keyboard commands for tmux online](https://gist.github.com/MohamedAlaa/2961058).

### How do I upload and download files to and from the server? ###

You can use ``scp`` or ``sftp`` from the command line.  For a nicer experience, you need an SFTP client.  Some free options are [FileZilla](https://filezilla-project.org) and [WinSCP](https://winscp.net/eng/index.php).

### I am getting CUDA out-of-memory errors, what do I do? ###

There are four GPUs on the machine but typically your code will only use the first one unless you tell it otherwise. 

You can use 
    
    nvidia-smi
    
to check GPU availability.  Then, to select a particular GPU to use:

    export CUDA_VISIBLE_DEVICES=<0,1,2, or 3>

### What if I can't correctly set up my environment in conda?  How do I compile C++ programs? Can you please install a specific program or CUDA version?  ###

In cases where you need specific versions of drivers, libraries, etc. installed or you need to compile C++, use Docker so that you can manage the system environment yourself.  You need to be added to the docker group in order to use docker -- ask me about it and I will help you determine if Docker is actually necessary.

To use Docker, you need to create a Dockerfile and store it in a sub-directory.   For example, create a text file at "docker/Dockerfile."  Here is an example Dockerfile for Tensorflow:
      
    FROM tensorflow/tensorflow:latest-gpu-py3
    RUN apt-get update ; apt-get install vim git wget -y
    RUN pip install --upgrade scikit-image tqdm opencv-python

To build the Dockerfile:
      
    docker build docker -t <tag>

You can choose whatever you want for the tag.
      
Docker normally runs as root which is dangerous.  However, with this command you can run Docker as your user rather than root:
      
    docker run -u $(id -u):$(id -g) --rm --gpus device=<gpu number> -it -v /code:/code -v /data:/data -v /data2:/data2 -e USER=$USER -e HOME=/code/$USER -w $PWD <tag> bash


