# docker network

## ls
- List all networks
```bash
docker network ls
```

## create
- Create a new network
```bash
docker network create <network-name>
```

### `--driver` or `-d`
- Create a new network with a specific driver
```bash
docker network create --driver <driver-name> <network-name>
```
### `--subnet` or `-s`
- Create a new network with a specific subnet
```bash
docker network create --subnet <subnet> <network-name>
```
### `--gateway` or `-g`
- Create a new network with a specific gateway
```bash
docker network create --gateway <gateway> <network-name>
```

## inspect
- Inspect a network
```bash
docker network inspect <network-name>
```
## rm 
- Remove a network
```bash
docker network rm <network-name>
```
## prune
- Remove all unused networks
```bash
docker network prune
```
## connect
- Connect a container to a network
```bash
docker network connect <network-name> <container-name>
```
## disconnect
- Disconnect a container from a network
```bash
docker network disconnect <network-name> <container-name>
```
## help
- Get help for the network command
```bash
docker network --help
```
## options
- List all options for the network command
```bash
docker network --help
```
