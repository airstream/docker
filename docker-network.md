# Docker Network
```bash
$ docker network -h
$ docker network ls
$ docker network create br00                  # Create new network with name br00
$ docker network inspect br00                 # Show details about the br00 network
$ docker network rm br00                      # Remove br00 network
$ docker network connect br00 container1      # Add the container to the bridge network
$ docker network disconnect br00 container1   # Remove network br00 from container
```
