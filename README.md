# Docker commands
## [Docker Images](./docker-images.md)

## [Docker Container](./docker-container.md)

## Network
```bash
$ docker network -h
$ docker network ls
$ docker network create br00                  # Create new network with name br00
$ docker network inspect br00                 # Show details about the br00 network
$ docker network rm br00                      # Remove br00 network
$ docker network connect br00 container1      # Add the container to the bridge network
$ docker network disconnect br00 container1   # Remove network br00 from container
```

## Volume
```bash
$ docker volume ls                            # List volumes
$ docker volume create testvol                # Create volume testvol
$ docker volume inspect testvol               # Inspecting a volume
$ docker volume rm testvol                    # Remove volume testvol
```

### Volume: Bind mounts
```bash
# Mount flag
$ mkdir mountfolder
$ docker container run -d \
  --name container-bind-mount1 \
  --mount type=bind,source="$(pwd)"/mountfolder,target=/app \
  nginx
```

```bash
# Volume flag
$ docker container run -d \
 --name nginx-bind-mount2 \
 -v "$(pwd)"/target2:/app \
 nginx
```

### Volume for Persistent Storage
```bash
$ docker container run -d \
 --name nginx-volume1 \
 --mount type=volume,source=html-volume,target=/usr/share/nginx/html/ \
 nginx

$ docker volume inspect html-volume
```

## Dockerfile
General guidelines:
* Keep containers as ephemeral as possible.
* Follow Principle 6 of the 12 Factor App.
* Avoid including unnecessary files.
* Use .dockerignore.
* Use multi-stage builds.
* Don’t install unnecessary packages.
* Decouple applications.
* Minimize the number of layers.
* Sort multi-line arguments.
* Leverage build cache.

## Building Docker Images
Useful flags:
* -f, --file string: This is the name of the Dockerfile (Default is PATH/Dockerfile).
* --force-rm: Always remove intermediate containers.
* --label list: Set metadata for an image.
* --rm: Remove intermediate containers after a successful build (default is true).
* --ulimit ulimit: This sets ulimit options (default is []).

```bash
# Building image by piping the Dockerfile through STDIN
$ docker image build -t <NAME>:<TAG> -<<EOF
Build instructions
EOF

# Example
$ docker image build -t linuxacademy/nginx:stind --rm -<<EOF
FROM nginx:latest
VOLUME ["/usr/share/nginx/html/"]
EOF
```

```bash
# Building an image using a URL
$ docker image build -t <NAME>:<TAG> <GIT_URL>#<REF>
$ docker image build -t <NAME>:<TAG> <GIT_URL>#:<DIRECTORY>
$ docker image build -t <NAME>:<TAG> <GIT_URL>#<REF>:<DIRECTORY>

# Example 
$ docker image build -t linuxacademy/weather-app:github https://github.com/linuxacademy/content-weather-app.git#remote-build
```

## Node labels
* label
```bash
 docker node ls
 docker node update --label-add availability_zone=east <NODE_NAME>
 ```
* la--placement-pref
```bash
 docker service create --name nginx-spread --placement-pref spread=node.labels.availability_zone --replicas 3 nginx
 docker service ps nginx-spread
```

## Docker Storage in Depth
overlay2 - [default] current Ubuntu and CentOS/RHEL versions 
```bash
docker container inspect storage_nginx # Use docker inspect to find the location of the container's data on the host
docker image inspect nginx #  docker inspect to find the location of an image's data
```
DeviceMapper - storage driver for CentOS7 and earlier. 
Supports two modes: **loop-lvm** and **direct-lvm**

**loop-lvm**: additional physical disk using files on the local disk; does not require an additional storage device; bad performance (only for testing)

**direct-vm**: data on separate disk; requires an addtional storage device, good performance (for production)

### [Docker Volumes](./docker-volumes.md)
