# Docker 101
## Introduction to containerization for data science

This repo is part of the introductory workshop on [Docker][docker] focusing specifically on containerization for data-science applications. This workshop is offered as a part of the [Applied Data Science Lab program](adsl) at [Cybera][cybera]. It contains the setup/config files to build and successfully run a [JupyterLab][jupyterlab] container using [Docker][docker]. [JupyterLab][jupyterlab] provides a web-based interactive development environment for jupyter notebooks, code, and data. It’s widely used to prototype and develop different data-science applications. To learn more about JupyterLab, visit the link [here](jupyterlab). 

## Table of Contents
1. [Introduction](#1)
2. [Installation](#2)
3. [Need for Containerization](#3)
4. [Benefits for Data Science Enthusiasts](#4)
5. [Build Jupyter Lab Container](#5)
6. [Build GPU enabled Jupyter Lab Container](#6)

<a id="1"></a>
## 1. Introduction
<a id="1.1"></a>
### 1.1. Docker
[Docker](docker) is an open-source platform for developing, shipping, and running applications. It reduces the delay between writing code and deploying it in production.
For starters, the [official Docker guide][guide] provides a good head start on using `Docker`. 
<a id="1.2"></a>
### 1.2. Docker Compose
[Docker Compose](compose) is a tool that enables running multiple `Docker` containers. `Docker Compose` is defined as a YAML file to configure different applications' services.  

<a id="2"></a>
## 2. Installation
### 2.1. Docker 
- Download the installation wizard from [Dockerhub][install-docker]. 
- It will lead you through all the steps for your operating system. You can also create an online account. 
- Once it’s finished installing, open your CLI and enter the following commands to verify if the `Docker` is running successfully:  
```
docker --version
```
### 2.1. Docker Compose
- Please note that if you have installed `Docker Desktop` correctly using the above steps. Then, the `Docker Compose` comes pre-installed. If not, please go through this link to install [Docker Compose](install-compose). 
- To check if `Docker Compose` is configured correctly, please run
```
docker compose --version
```

<a id="3"></a>
### 3. What is a container?
- A container is a standard software unit that encapsulates each application with its operating environment. 
- Containers package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package. 
- The isolation and security allow you to run many containers simultaneously on a given host.  

<a id="4"></a>
### 4. Benefits for Data Science Enthusiasts
- Automate the boring stuff
- Reproducibility
- Fast, consistent delivery of your applications
- Responsive deployment and scaling
- Running more workloads on the same hardware
- Not having to worry about package dependencies

<a id="5"></a>
### 5. Build Jupyter Lab Container 
First, clone this repository on your remote server/virtual machine (vm) or local by using `https` or `ssh` or `Github CLI`. 

Then, run the following commands in your terminal to build and deploy the JupyterLab container:
```
cd docker101_jupyterlab
docker compose up --build
```
The above step extracts and downloads the specified `JupyterLab` image onto your VM or local and then spins it onto a running instance called as the container. 

Use `CTRL + C` to exit out of the container at any time. 

To run the container in detached mode so that you can reuse the existing terminal, please add `-d` while building the image as follows
```
docker compose up --build -d
```
You could also run 
```
docker compose up -d
```
This will just reuse the image if it already exists on your VM or local, If not, it will extract again. But `--build` forces the docker to rebuild the image every time it's run. This is helpful and must when you are adding new requirements to your container.  

If you have multiple containers listed on the `Docker Compose` file and you wish to start only the `JupyterLab` container, run the above command with the desired `Docker` service name as follows. 
```
docker compose up -d jupyter101
```

If you have successfully built and deployed the JupyterLab image container using the above commands, you can access the web interface of the JupyterLab at 
```
http://localhost:8777
```

You might be prompted to enter the token while accessing the `http://localhost:8777`. The token can be obtained from the logs of the running JupyterLab container as follows. 

```
docker logs <container-id>
```

To view the list of all the containers and get the associated container id of the jupyter, run 
```
docker ps -a
```
Then locate and copy the container id from the displayed list of containers that are built. 


If you are able to access and run the `Welcome.ipnb` notebook, you are all set and have configured JupyterLab correctly. 


To stop the running container, run
```
docker stop <container-id>
```

To remove the container, run
```
docker rm -f <container-id>
```

To cleanup all the old images and associated containers, run
```
docker system prune -a
```
Please exercise caution while running the above command as it deletes the old images and stopped containers. 

#### Microsoft Windows Setup

If you are using Microsoft Windows, and are unable to reach your JupterLab container please make sure your firewall is allowing Docker to use your selected port.  You may also need to enter the following commands:
```
net stop winnat
docker start ...
net start winnat
```
<a id="6"></a>
### 5. Build GPU enabled Jupyter Lab Container
[This medium article](https://cschranz.medium.com/set-up-your-own-gpu-based-jupyterlab-e0d45fcacf43) describes how to set up our own customized GPU-based Jupyter easily using docker. Please use this to configure your GPU instance. 

After following the above steps in the article,  from the terminal run: 
```
docker compose --profile gpu up -d
```
If you have successfully built and deployed the GPU JupyterLab image container using the above command, you can access the web interface of the JupyterLab, after relevant port forwarding, at 
```
http://localhost:8778
```

[adsl]:https://www.cybera.ca/adsl/
[jupyterlab]:https://jupyter.org/
[docker]:https://www.docker.com/
[guide]:https://docs.docker.com/get-started/overview/
[cybera]:https://www.cybera.ca/
[install-docker]:https://docs.docker.com/get-docker/
[compose]:https://docs.docker.com/compose/
[install-compose]:https://docs.docker.com/compose/install/
