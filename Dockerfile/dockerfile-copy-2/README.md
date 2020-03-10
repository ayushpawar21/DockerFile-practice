Sending build context to Docker daemon  6.656kB
Step 1/7 : FROM alpine AS stage1
latest: Pulling from library/alpine
c9b1b535fdd9: Pull complete 
Digest: sha256:ab00606a42621fb68f2ed6ad3c88be54397f981a7b70a79db3d1172b11c4367d
Status: Downloaded newer image for alpine:latest
 ---> e7d92cdc71fe
Step 2/7 : LABEL maintainer="aayushpawar21"
 ---> Running in 88200d48823f
Removing intermediate container 88200d48823f
 ---> a267d2dfd7e5
Step 3/7 : RUN echo "Welcome to Docker Labs!" > /opt/index.html
 ---> Running in 1cc365f488e2
Removing intermediate container 1cc365f488e2
 ---> 640118e028bb
Step 4/7 : FROM nginx:alpine
 ---> 377c0837328f
Step 5/7 : LABEL maintainer="Collabnix"
 ---> Running in 27edc5bad146
Removing intermediate container 27edc5bad146
 ---> efb98ba3dcb0
Step 6/7 : COPY --from=stage1 /opt/index.html /usr/share/nginx/html/
 ---> 54ef0b85ca31
Step 7/7 : ENTRYPOINT ["nginx", "-g", "daemon off;"]
 ---> Running in 7c38ff942bcb
Removing intermediate container 7c38ff942bcb
 ---> a2e67961dcc7
Successfully built a2e67961dcc7
Successfully tagged cpy:v2

