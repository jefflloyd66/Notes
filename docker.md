# Images

- list: `docker images -a`
- delete: `docker rmi IMAGE IMAGE ...`
- dangling: `docker images -f dangling=true`
- delete dangling: `docker rmi $(docker images -f dangling=true -q)`

# Containers

- list: `docker ps -a`
- delete: `docker rm ID_or_Name ID_or_Name ...`
- all exited: `docker ps -a -f status=exited`
- delete all exited: `docker rm ($docker ps -a -f status=exited -q)`
- stop all: `docker stop $(docker ps -a -q)`
- delete all: `docker rm $(docker ps -a -q)`

# Volumes

- list: `docker volume ls`
- delete: `docker volume rm vol_name vol_name ...`
- dangling: `docker volume ls -f dangling=true`
- delete dangling: `docker volume rm $(docker volume ls -f dangling=true -q)`

# Container and Volume

- delete both together: `docker rm -v container_name`
