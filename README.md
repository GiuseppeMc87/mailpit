### Setup Steps

#### 1. Create container 

    sudo docker-compose up -d

#### 6. Access via browser 
    http://localhost:8025/


### Debugging

#### 1. Remove everything 
    sudo docker-compose down --rmi local --remove-orphans --volumes 
    docker system prune --volumes 
    docker network prune 
    sudo systemctl restart docker

#### 2. Create network
    docker network create shared-network

#### 3. Rebuild container
    sudo docker-compose up -d 

### If the problem persists, check in this order: 

#### List containers (to get the container name)
    docker ps

#### Container logs (check for errors in logs)
    sudo docker logs {container name}
    Example: sudo docker logs mailpit

#### Network list (to get network name)
    docker network ls

#### Inspect network (to see if the services are running in the same network)
    docker network inspect {network name}
    Example: docker network inspect shared-network

#### If required, connect container to network 
    docker network connect {network name} {container name}
    Example: docker network connect shared-network mailpit