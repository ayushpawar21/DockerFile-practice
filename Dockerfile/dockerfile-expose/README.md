Lab #11: EXPOSE instruction

The EXPOSE instruction expose a port, the protocol can be UDP or TCP associated with the indicated port, default is TCP with no specification. The EXPOSE won’t be able to map the ports on the host machine. Regardless of the EXPOSE settings, EXPOSE port can be override using -p flag while starting the container.
Pre-requisite:
Tested Infrastructure
Platform 	Number of Instance 	Reading Time
Play with Docker 	1 	5 min
Pre-requisite

    Create an account with DockerHub
    Open PWD Platform on your browser
    Click on Add New Instance on the left side of the screen to bring up Alpine OS instance on the right side

Assignment

    Create an image with EXPOSE instruction
    Inspecting the EXPOSE port in the image
    Publish all exposed port

Create an image with VOLUME instruction

Dockerfile

FROM nginx:alpine
LABEL maintainer="Collabnix"

EXPOSE 80/tcp
EXPOSE 80/udp

CMD [ "nginx","-g","daemon off;" ]

Building Docker image

$ docker build -t expose:v1 .

Create a container based on expose:v1 image

$  docker container run --rm -d --name expose-inst expose:v1

Inspecting the EXPOSE port in the image

$ docker image inspect --format  expose:v1

Publish all exposed ports

We can publish all EXPOSE port using -P flag.

$ docker container run --rm -P -d --name expose-inst-Publish expose:v1

Checking the publish port

$  docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                          NAMES
24983e09bd86        expose:v1           "nginx -g 'daemon of…"   46 seconds ago      Up 45 seconds       0.0.0.0:32768->80/tcp, 0.0.0.0:32768->80/udp   expose-inst-Publish

Contributor                                        
~                              
