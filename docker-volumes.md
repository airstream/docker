# Docker Volumes
```bash
$ docker volume ls                            # List volumes
$ docker volume create testvol                # Create volume testvol
$ docker volume inspect testvol               # Inspecting a volume
$ docker volume rm testvol                    # Remove volume testvol
```

## Volume: Bind mounts
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

## Volume for Persistent Storage
```bash
$ docker container run -d \
 --name nginx-volume1 \
 --mount type=volume,source=html-volume,target=/usr/share/nginx/html/ \
 nginx

$ docker volume inspect html-volume
```
