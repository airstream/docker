# Docker Volumes
```bash
$ docker volume ls                            # List volumes
$ docker volume create testvol                # Create volume testvol
$ docker volume inspect testvol               # Inspecting a volume
$ docker volume rm testvol                    # Remove volume testvol
```

## Volume: Bind mounts
Mount a specific path on the host machine to the container; not portable, dependent on the host's machine file system and directory structure.
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
Stores data on the host file system, but the storage location is managed by Docker; portable, can mount the same volume to mupltiple containers, more scenarious for work.
```bash
$ docker container run -d \
 --name nginx-volume1 \
 --mount type=volume,source=html-volume,target=/usr/share/nginx/html/ \
 nginx

$ docker volume inspect html-volume
```
