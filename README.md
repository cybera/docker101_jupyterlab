# Setting up reverse proxy

## Caddy

Caddy 2 is a powerful, enterprise-ready, open-source web server with automatic HTTPS. [Caddy](https://caddyserver.com/docs/) documentation provides in-depth information and getting started tutorials for starters. 


To enable `HTTPS` on the JupyterLab container, please set the domain name of the server that you are hosting as an environment variable. 

```
export DOMAIN_NAME='your-domain-name'
cd docker101_jupyterlab
docker-compose up --build 
```

This will build and run the JupyterLab and Caddy containers. If the build is successful, you can access the running jupyter Lab container at 

```
https://host/jupyter/lab
```
