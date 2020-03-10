 docker build -t cpy:v1 .
Sending build context to Docker daemon  3.072kB
Step 1/4 : FROM nginx:alpine
alpine: Pulling from library/nginx
4167d3e14976: Pull complete 
bb292c78f105: Pull complete 
Digest: sha256:abe5ce652eb78d9c793df34453fddde12bb4d93d9fbf2c363d0992726e4d2cad
Status: Downloaded newer image for nginx:alpine
 ---> 377c0837328f
Step 2/4 : LABEL maintainer="Collabnix"
 ---> Running in 46b21e9ef648
Removing intermediate container 46b21e9ef648
 ---> ff931192b3f5
Step 3/4 : COPY index.html /usr/share/nginx/html/
 ---> a792c61114dd
Step 4/4 : ENTRYPOINT ["nginx", "-g", "daemon off;"]
 ---> Running in c86459022d0b
Removing intermediate container c86459022d0b
 ---> 19728d924d8b
Successfully built 19728d924d8b
Successfully tagged cpy:v1

