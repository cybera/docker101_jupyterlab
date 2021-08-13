# Docker 101
## Introduction to containerization for data science

This repo is part of the introductory workshop on [Docker][docker] focussing specifically on containerization for data-science applications. This workshop is offered under the [Data Science for Albertans program](dsfa) at [Cybera][cybera]. It contains the setup/config files to build and successfully run a [JupyterLab][jupyterlab] container using [Docker][docker]. [JupyterLab][jupyterlab] provides a web-based interactive development environment for jupyter notebooks, code, and data. It’s widely used in different data-science applications. To learn more about JupyterLab, visit the link [here](jupyterlab). 

## Table of Contents
1. [Introduction to Docker](#1)
2. [Docker Installation](#2)
3. [Need for Containerization](#3)
4. [Benefits for Data Science Enthusiasts](#4)
5. [Setup](#5)

<a id="1"></a>
### 1. Introduction to Docker
[Docker](docker) is a open platform for developing, shipping and running applications. It reduces delay between writing code and running it in production.
For starters, the [official Docker guide][guide] provides a good head start to using [Docker][docker]. 

<a id="2"></a>
### 2. Docker Installation 
- Download installation wizard from [Dockerhub][install-docker]. 
- It will lead you through all the steps for your operating system. You can also create an online account. 
- Once it’s finished installing, open your favourite terminal application and enter the following commands to verify that the Docker is running:  
```
docker --version
docker-compose --version
```

<a id="3"></a>
### 3. What is a container?
- A container is a standard software unit which encapsulates each application with its own operating environment. 
- Containers package up an application with all of the parts it needs, such as libraries and other dependencies, and ship it all out as one package. 
- The isolation and security allow you to run many containers simultaneously on a given host.  

<a id="4"></a>
### 4. Benefits for Data Science Enthusiasts
- Automate the boring stuff
- Reproducibility
- Fast, consistent delivery of your applications
- Responsive deployment and scaling
- Running more workloads on the same hardware

<a id="5"></a>
### 5. Setup 
Run the following commands in your terminal to build and deploy the JupyterLab container:
```
cd docker101_jupyterlab
docker-compose up --build
```
Use `CTRL + C` to exit out of the container at any time. 

To run the container in detached mode add `-d` as follows
```
docker-compose up --build -d
```

If you have successfully built and deployed the JupyterLab image container using either of the above commands, you can access the web interface of the JupyterLab at 
```
http://localhost:8888
```

You might be prompted to enter the token while accessing the `http://localhost:8888`. The token can be obtained from the logs of the running JupyterLab container as follows. 

```
docker logs <container-id>
```

To view the list of all the containers and get the container id of the jupyter, run 
```
docker ps -a
```

To stop the running container, run
```
docker stop <container-id>
```

To remove the container, run
```
docker rm <container-id>
```


### Microsoft Windows Setup

If you are using Microsoft Windows, and are unable to reach your JupterLab container please make sure your firewall is allowing Docker to use your selected port.  You may also need to enter the following commands:
```
net stop winnat
docker start ...
net start winnat
```

[dsfa]:https://www.cybera.ca/data-science-for-albertans/
[jupyterlab]:https://jupyter.org/
[docker]:https://www.docker.com/
[guide]:https://docs.docker.com/get-started/overview/
[cybera]:https://www.cybera.ca/
[install-docker]:https://docs.docker.com/get-docker/
