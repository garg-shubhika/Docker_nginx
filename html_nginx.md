### Step 1: Create HTML File for Nginx

1. Create the `nginx-html` directory and navigate into it:
   ```sh
   mkdir -p ~/nginx-html
   cd ~/nginx-html
   ```

2. Create and edit the `index.html` file:
   ```sh
   nano index.html
   ```

   Add the following content to `index.html`:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>nginx docker</title>
   </head>
   <body>
       <h1>This is nginx inside a Docker container.</h1>
       <p>This is the index page</p>
   </body>
   </html>
   ```

### Step 5: Run the Nginx Docker Container

1. Run the Nginx Docker container, mapping port 8000 on your host to port 80 in the container and mounting the `nginx-html` directory:
   ```sh
   docker run -d -p 8000:80 -v ~/nginx-html:/usr/share/nginx/html --name new-nginx nginx
   ```

2. Verify the Docker container is running:
   ```sh
   docker ps
   ```

### Accessing Nginx

Open your web browser and navigate to `http://localhost:8000`. You should see your HTML content displayed, showing the Nginx page from within the Docker container.

### Stopping and Removing the Docker Container

1. List all running Docker containers to get the container ID:
   ```sh
   docker ps
   ```

2. Stop the running container (replace `CONTAINER_ID` with the actual container ID from the previous command):
   ```sh
   docker stop CONTAINER_ID
   ```
   OR
    ```sh
   docker stop CONTAINER NAME
   ```

    Example of stopping a container using container name:
   ```sh
   docker stop new-nginx
   ```
4. Remove the stopped container (replace `CONTAINER_ID` with the actual container ID from the previous command):
   ```sh
   docker rm CONTAINER_ID
   ```

### Step 2: Add another HTML File for Nginx

1. Navigate to the `nginx-html` directory:
   ```sh
   cd ~/nginx-html
   ```

2. Create and edit the `about.html` file:
   ```sh
   nano about.html
   ```

   Add the following content to `about.html`:
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>About nginx</title>
   </head>
   <body>
       <h1>About Page.</h1>
       <p>This is the about page served by nginx inside a docker container.</p>
   </body>
   </html>
   ```
3. Since the nginx-html directory is mounted to `/usr/share/nginx/html` in the running container, the new file should be automatically available. Open your web browser and navigate to `http://localhost:8000/about.html` to verify that the new page is accessible.
