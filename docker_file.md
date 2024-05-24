1. **Create HTML File**: Open the WSL terminal and create a file named `index.html`:

```bash
nano index.html
```

Put below HTML content in the file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello Docker</title>
</head>
<body>
    <h1>Hello Docker!</h1>
    <p>This is a simple HTML file inside a Docker container.</p>
</body>
</html>
```

Save and exit the editor.

2. **Create Dockerfile**: Create a `Dockerfile` In the same directory where `index.html` is located to build our Docker image.

```bash
nano Dockerfile
```

Inside `Dockerfile`, put the following content:

```Dockerfile
# Use a base image
FROM nginx:alpine

# Copy HTML file to nginx web server root directory
COPY index.html /usr/share/nginx/html

# Expose port 80
EXPOSE 80
```

Save and exit the editor.

3. **Build Docker Image**: Now, build the Docker image using the `Dockerfile`:

```bash
docker build -t my-html-image .
```
This command will build a Docker image named `my-html-image`.

4. **Run Docker Container**: Finally, we can run a container using the image we just created:

```bash
docker run -d -p 8080:80 my-html-image
```

This command will run a Docker container based on `my-html-image` and map port 8080 on the host machine to port 80 inside the container.

Now, if we open a web browser on our host machine and navigate to `http://localhost:8080`, we should see our HTML content served from the Docker container.
