Lab #8: Create an image with ARG instruction

The ARG directive in Dockerfile defines the parameter name and defines its default value. This default value can be overridden by the --build-arg <parameter name>=<value> in the build command docker build.

`ARG <parameter name>[=<default>]`

The build parameters have the same effect as ENV, which is to set the environment variables. The difference is that the environment variables of the build environment set by ARG will not exist in the future when the container is running. But don’t use ARG to save passwords and the like, because docker history can still see all the values.
Pre-requisite:
Tested Infrastructure
Platform 	Number of Instance 	Reading Time
Play with Docker 	1 	5 min
Pre-requisite

    Create an account with DockerHub
    Open PWD Platform on your browser
    Click on Add New Instance on the left side of the screen to bring up Alpine OS instance on the right side

Assignment

    Writing a Dockerfile with ARG instruction
    Building Docker Image with default argument
    Running container argv:v1
    Passing the argument during image build time
    Running container argv:v2

Writing a Dockerfile with ARG instruction

We are writing a Dockerfile which echo “Welcome $WELCOME_USER, to Docker World!” where default argument value for WELCOME_USER as Collabnix.

FROM alpine:3.9.3
LABEL maintainer="Collabnix"

#Setting a default value to Argument WELCOME_USER
ARG WELCOME_USER=Collabnix
RUN echo "Welcome $WELCOME_USER, to Docker World!" > message.txt
CMD cat message.txt

Building Docker Image with default argument

$ docker image build -t arg:v1 .

Running container argv:v1

$ docker run arg:v1

Welcome Collabnix, to Docker World!

Passing the argument(WELCOME_USER) during image build time using –build-arg flag

$ docker image build -t arg:v2 --build-arg WELCOME_USER=Savio .

Running container argv:v2

$ docker run arg:v2

Welcome Savio, to Docker World!

NOTE: ARG is the only one instruction which can come before FROM instruction, but then arg value can be used only by FROM.
