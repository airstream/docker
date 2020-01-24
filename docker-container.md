# Docker Container
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
