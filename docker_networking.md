# Docker Networking Setup

This guide details how to set up and run an NGINX container and a Postgres container, connect them through a secured Docker network, and inspect their IP addresses. 


## Steps

### 1. Start the Docker Daemon

```bash
sudo dockerd
```

This command starts the Docker daemon, which is required to run Docker containers.

### 2. Pull the Docker Images

Pull the NGINX and Postgres images from Docker Hub:

```bash
docker pull nginx
docker pull training/postgres
```

### 3. Run the Containers

Run the NGINX container and map port 8000 on the host to port 80 in the container:

```bash
docker run -d -p 8000:80 --name mynginxnetwork nginx
```
You can access NGINX by navigating to `http://localhost:8000/` in your browser.

Run the Postgres container:

```bash
docker run -d --name mypostgresnetwork training/postgres
```

### 4. Create a Custom Docker Network

Create a secure Docker network for the containers:

```bash
docker network create mysecure-network-docker
```

### 5. List Docker Networks

List all Docker networks to verify the creation of the custom network:

```bash
docker network ls
```

### 6. Inspect Containers

Inspect the NGINX container to get its IP address:

```bash
docker inspect mynginxnetwork
```

Example output for the IP address:

```
"IPAddress": "173.19.0.2"
```

Inspect the Postgres container to get its IP address:

```bash
docker inspect mypostgresnetwork
```

Example output for the IP address:

```
"IPAddress": "173.19.0.3"
```

### 7. Inspect the Custom Network

Inspect the custom network to get its subnet information:

```bash
docker network inspect mysecure-network-docker
```

Example output for the subnet:

```
"Subnet": "173.22.0.0/16"
```

### 8. Connect Containers to the Custom Network

Connect the NGINX container to the custom network:

```bash
docker network connect mysecure-network-docker mynginxnetwork
```

Re-inspect the NGINX container to get its new IP address:

```bash
docker inspect mynginxnetwork
```

Example output for the new IP address:

```
"IPAddress": "173.23.0.2"
```

Connect the Postgres container to the custom network:

```bash
docker network connect mysecure-network-docker mypostgresnetwork
```

Re-inspect the Postgres container to get its new IP address:

```bash
docker inspect mypostgresnetwork
```

Example output for the new IP address:

```
"IPAddress": "173.23.0.3"
```

### 9. Inspect Host and Bridge Networks

Inspect the host network (usually has no IP address assigned):

```bash
docker network inspect host
```

Inspect the bridge network (default Docker network):

```bash
docker network inspect bridge
```

Example output for the bridge network IP address:

```
"IPAddress": "173.16.0.3/16"
```
