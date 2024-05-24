### Step 1: Pull and Run Nginx Container

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
