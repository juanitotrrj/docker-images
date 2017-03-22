# docker-images
My docker images for builds, deploys, and whatnot

###### Start a detached docker instance
```bash
docker run --privileged -d -ti -e "container=docker" [IMAGE]:[TAG] /usr/sbin/init
```

###### Go into the shell of a running docker instance
```bash
docker exec -it [CONTAINER ID] /bin/bash
```
