# Docker commands
## Image
```bash
$ docker images                   # List images
$ docker image pull httpd         # Pull httpd image with a tag 'latest' from Docker hub registry
$ docker image pull httpd:2.4.41  # Pull httpd image with a tag '2.4.41' from Docker hub registry
$ docker image inspect httpd      # Display detailed information on httpd image

# Remove httpd image
$ docker image rm httpd    
$ docker rmi httpd

# Inspect image
$ docker image inspect httpd
$ docker inspect httpd
```

## Container
```bash
# Create container with random name
$ docker container run httpd

# Create container with a name container1 \
# -d, --detach        Run container in background and print container ID \
# -p, --publish list  Publish a container's port(s) to the host
$ docker container run --name container1 -d -p 80:80 httpd # Create container with name container1

# Run a command in a running container
$ docker container exec -it container1 /bin/bash
$ docker container exec -it container1 cat /etc/hosts

# Display a live stream of container(s) resource usage statistics
$ docker container stats container1

# Display the running processes of a container
$ docker container top container1

# Start container 
$ docker container start container1

# Stop container 
$ docker container stop container1

# Inspect container
$ docker container inspect container1
$ docker inspect container1

# Delete container
$ docker container stop container1
$ docker container rm container1
$ docker rm container1

# Check port usage for container 
$ docker container port container1
```

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
$
```

