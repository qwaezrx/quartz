---
tags:
  - CS/Programming/DevOps/Docker
---

## Command Lines
---
__Create network__: `docker network create <network-name>`
__View Networks__: `docker network ls`
__Inspect__: `docker network inspect <network-name>`
__Remove Networks__: `docker network rm <network-name>`
__Clean Network__: `docker network prune`

### Connect Container to Network

```sh
docker network inspect bridge
```

```sh
docker network connect <network-name> <container-name>
```

__Disconnect Container__:
```sh
docker network disconnect bridge one
```

### Networking between Containers

__Send Ping__:
```sh
docker exec <container-name> ping <container-name>
```

## Resources
---
- https://www.daleseo.com/docker-networks/