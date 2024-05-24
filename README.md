# Docker_nginx

Open WSL:

In terminal-1:
1. sudo apt update
2. sudo apt install docker.io
3. sudo dockerd

In terminal-2:
1. docker --version
2. docker pull hello-world
3. docker images
4. docker pull nginx:latest
5. docker ps
6. docker run -p 8000:80 nginx
7. docker ps -a
8. docker rm CONTAINER_ID
