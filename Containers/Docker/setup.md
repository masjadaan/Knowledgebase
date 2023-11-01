# Docker setup
* * *
## Build & Run
```
mkdir /home/msbit/Docker/<name>
cd Docker/<name>
nano Dockerfile
docker build -t <name>-kali .
docker run -it --privileged <name>-kali

# Docker IDs
docker ps
```

## File Operation
```
# Copy: Host -> Docker
docker cp /path/on/host/file.txt container_id:/path/in/container/

# Copy: Docker -> Host
docker cp container_id:/path/in/container/file.txt /path/on/host/
```

## Delet Container
```
docker stop $(docker ps -a -q --filter ancestor=your-image-name)
docker rm $(docker ps -a -q --filter ancestor=your-image-name)
docker rmi your-image-name
docker image prune
docker system prune
```
