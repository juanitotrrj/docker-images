# docker-images
My docker images for builds, deploys, and whatnot

###### Start a detached docker instance
docker run --privileged -d -ti -e "container=docker" [IMAGE]:[TAG] /usr/sbin/init

###### Go into the shell of a running docker instance
docker exec -it [CONTAINER ID] /bin/bash
