# Docker Image
```bash
# List images
$ docker image ls
$ docker image ls -a 
$ docker images

# Pull image from registry
$ docker image pull httpd         # By default tag is a  'latest' from Docker hub registry
$ docker image pull httpd:2.4.41  # Pull httpd image with a tag '2.4.41' from Docker hub registry

# Push image to registry
$ docker push <image_name>
$ docker push <private_repository_name>/<image_name>

# Remove httpd image
$ docker image rm httpd    
$ docker rmi httpd
$ docker image prune              # Remove unused images

# Inspect image (Display detailed information of image)
$ docker image inspect httpd
$ docker image inspect httpd --format "{{.Architecture}} {{.Os}}" # Format output
$ docker inspect httpd


$ docker image history nginx      # View file system layers in an image
```
