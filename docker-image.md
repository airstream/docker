# Docker Image
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
