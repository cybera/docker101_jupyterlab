# docker101_jupyterlab

This repo is part of the introductory workshop on *Docker101: Containerization for Data-Science*. It contains the setup files to build and successfully run the [JupyterLab](https://jupyter.org/) container using [Docker](https://www.docker.com/). [JupyterLab](https://jupyter.org/) provides a web-based interactive development environment for jupyter notebooks, code, and data. It’s widely used in different data-science applications. To learn more about the JupyterLab, visit the link [here](https://jupyter.org/). 

### What is Docker?
[Docker](https://www.docker.com/) is an open platform for developing, shipping, and running applications. It provides the ability to package and run an application in a loosely isolated environment called a container. For starters, the [official Docker guide](https://docs.docker.com/get-started/overview/) provides a good head start to using [Docker](https://www.docker.com/). 

### Installation
Before proceeding further, please install [Docker](https://www.docker.com/) following the instructions provided in the [link here](https://docs.docker.com/get-docker/) for your choice of operating system. 

### Setup 

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
http://localhost:8889
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

To remote the container, run
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
