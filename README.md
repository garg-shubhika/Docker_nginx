# Docker_nginx

This repository provides a guide for setting up Docker and running a Nginx container on a WSL environment.

## Prerequisites

Ensure you have WSL installed and set up on your Windows machine.


### Step 1: Open WSL and Update System

1. Open your WSL terminal.

2. Update the package list:
   ```sh
   sudo apt update
   ```

### Step 2: Install Docker

1. Install Docker:
   ```sh
   sudo apt install docker.io
   ```

2. Start the Docker daemon:
   ```sh
   sudo dockerd
   ```

### Step 3: Verify Docker Installation

Open a new terminal (Terminal-2) to run the following commands:

1. Check Docker version:
   ```sh
   docker --version
   ```

2. Pull the `hello-world` image to verify your Docker installation:
   ```sh
   docker pull hello-world
   ```

3. List Docker images to confirm `hello-world` image is downloaded:
   ```sh
   docker images
   ```

### Step 4: Pull and Run Nginx Container

1. Pull the latest Nginx image:
   ```sh
   docker pull nginx:latest
   ```

2. List running Docker containers:
   ```sh
   docker ps
   ```

3. Run the Nginx container and map port 8000 on your host to port 80 in the container:
   ```sh
   docker run -p 8000:80 nginx
   ```

4. List all Docker containers, including stopped ones:
   ```sh
   docker ps -a
   ```

5. Remove a Docker container (replace `CONTAINER_ID` with the actual container ID from the previous command):
   ```sh
   docker rm CONTAINER_ID
   ```

## Accessing Nginx

Once the Nginx container is running, you can access it by navigating to `http://localhost:8000` in the web browser.

