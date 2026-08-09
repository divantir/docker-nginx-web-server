# Docker Nginx Web Server Deployment & Troubleshooting

## Project Overview

In this project, I deployed an Nginx web server inside a Docker container on my Ubuntu Linux server. I verified that the Docker service was running, created and managed containers, configured port mapping, and tested the web server from the command line.

I also encountered a container issue during deployment and used Docker troubleshooting commands to identify and resolve the problem.

## Scenario

The goal was to deploy an Nginx web server using Docker and make the web server accessible through port 8080 on the Ubuntu server.

## Technologies Used

- Ubuntu Linux
- Docker
- Nginx
- Linux Terminal
- curl
- VirtualBox

## Deployment Process

First, I verified that the Docker service was running:

```bash
sudo systemctl status docker

I checked the currently running Docker containers:
docker ps

The Nginx container was configured to run in detached mode with port 8080 on the Ubuntu host mapped to port 80 inside the container:
docker run -d -p 8080:80 --name company-web nginx

Troubleshooting

During deployment, Docker reported that the container name company-web was already in use.

Running:

docker ps

did not show the container because it was not currently running.

I then checked all containers, including stopped and created containers:

docker ps -a

This showed that company-web already existed and was in the Created state.

Instead of creating another container, I started the existing container:

docker start company-web

I then used:

docker ps

to verify that the container status changed to Up.

Verification

I tested the Nginx web server from the Ubuntu terminal using:

curl http://localhost:8080

The server returned the Nginx HTML response, confirming that the container was running and the web server was responding successfully through port 8080.
Commands Used
Command	Purpose
sudo systemctl status docker	Check the status of the Docker service
docker ps	Display running containers
docker ps -a	Display all containers
docker run	Create and start a new container
docker start	Start an existing container
docker logs	View container logs
docker inspect	View detailed container information
curl http://localhost:8080	Test the Nginx web server
Skills Demonstrated
Linux command-line administration
Docker container deployment
Container troubleshooting
Port mapping
Nginx web server deployment
HTTP connectivity testing
Troubleshooting container states
Technical documentation


