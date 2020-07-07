# Docker Swarm
## Manager
Initialize the swarm manager

NB! use the private IP (NOT the public IP) for the --advertise-addr:

```bash
$ docker swarm init --advertise-addr <swarm manager private IP>
```

## Worker
Get a join token from Swarm manager

```bash
# for add worker node
$ docker swarm join-token worker

# for add manager node
$ docker swarm join-token manager
```

Run output command on worker node(s)

```bash
$ docker swarm join --token <token> <swarm manager private IP>:<port>
```

## Status
Check docker swarm status
```bash
$ docker info
```

Check swarm nodes information and status 
```bash
$ docker node ls
```
