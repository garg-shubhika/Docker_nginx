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
