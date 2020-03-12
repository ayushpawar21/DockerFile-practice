Lab #10: VOLUME instruction
Pre-requisite:
Tested Infrastructure
Platform 	Number of Instance 	Reading Time
Play with Docker 	1 	5 min
Pre-requisite

    Create an account with DockerHub
    Open PWD Platform on your browser
    Click on Add New Instance on the left side of the screen to bring up Alpine OS instance on the right side

Assignment

    Create an image with VOLUME instruction
    Finding the volume created on the host
    Testing mount working as exepected

Create an image with VOLUME instruction

Dockerfile

FROM nginx:alpine
LABEL maintainer="Collabnix"

VOLUME /myvol
CMD [ "nginx","-g","daemon off;" ]

Building Docker image

$ docker build -t volume:v1 .

Create a container based on volume:v1 image

$ docker container run --rm -d --name volume-test volume:v1

Finding the volume created on the host
Checking the volume name of the container

$ docker container inspect -f '' volume-test
ed09456a448934218f03acbdaa31f465ebbb92e0d45e8284527a2c538cc6b016

Listout Volume in the host

$ docker volume ls
DRIVER              VOLUME NAME
local               ed09456a448934218f03acbdaa31f465ebbb92e0d45e8284527a2c538cc6b016

You will see the volume has been created.
Volume mount path in host

$ docker container inspect -f '' volume-test
/var/lib/docker/volumes/ed09456a448934218f03acbdaa31f465ebbb92e0d45e8284527a2c538cc6b016/_data

Testing mount working as exepected
Create a file in this folder

$ touch /var/lib/docker/volumes/ed09456a448934218f03acbdaa31f465ebbb92e0d45e8284527a2c538cc6b016/_data/mytestfile.txt

Checking file is there in run container

$ docker container exec -it volume-test ls myvol

Contributor
