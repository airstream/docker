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
```

## Container
```bash
$ docker container run httpd
$ docker container run --name container1 -P -d -p 80:80 httpd
# Delete container
$ docker container stop container1
$ docker container rm container1
$ docker rm container1
```
