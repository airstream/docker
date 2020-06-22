# Docker Select a storage driver 
1. Set a flag `--storage-driver` in daemon file (example `--storage-driver overlay2`)
2. Set `storage-driver` in file `/etc/docker/daemon.json`
```bash
$ vi /etc/docker/daemon.json
{
  "storage-driver": "overlay2"
}
```

```bash
# Restart docker daemon
$ systemctl restart docker
# Check a storage driver
$ docker info
$ docker info | grep -i storage
```
