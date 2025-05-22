# Port Mapping in Docker

Port mapping in Docker is the process of exposing a container’s internal ports to the host machine, so that services running inside the container can be accessed from outside (e.g., via a web browser or API client).

## Why It’s Needed
Containers are isolated and have their own internal network. Without port mapping, you can’t access services running inside them from our host machine.

## Syntax
```bash
docker run -p <host_port>:<container_port> IMAGE
```
- host_port: Port on our local machine
- container_port: Port inside the Docker container

## Example
```bash
docker run -p 8080:80 nginx
```
This command runs an Nginx container and maps port 80 inside the container to port 8080 on our host machine. You can access the Nginx server by navigating to `http://localhost:8080` in our web browser.
