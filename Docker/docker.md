# Docker



## Steps To Install Docker

**Pre requisite:** Enter your Computer Bios and make sure Virutalization is enabled


1. Go to the website and click Install
2. Run the executable
3. Restart computer if neccesary
4. Open Git Bash and run `Docker -v` to check if its installed

Extra Step: Once installed Enable `Expose daemon on tcp://localhost:2375 without TLS`

## Docker Architecture and Image Management

Docker follows a client-server architecture, where the Docker client interacts with the Docker daemon to manage containers and images. Understanding Docker's architecture is essential for efficiently working with Docker images.

### 1. Docker Client and Daemon

- **Docker Client**: The Docker client is a command-line tool that allows users to interact with Docker. It sends commands to the Docker daemon to perform actions such as building, running, and managing containers.

- **Docker Daemon**: The Docker daemon (also known as `dockerd`) is a background process responsible for managing Docker objects such as images, containers, volumes, and networks. It handles the heavy lifting of building, running, and distributing Docker containers.

### 2. Image Management

- **Image Creation**: Docker images are created using Dockerfiles, which contain instructions for building the image. When you run the `docker build` command, the Docker daemon reads the Dockerfile and builds the image layer by layer.

- **Image Storage**: Docker images are stored in a local repository on the host system. They can also be pushed to and pulled from remote registries such as Docker Hub or private registries. Images are downloaded from registries when they are needed to run a container.

**Diagram:**




### 3. Docker Compose

- **Docker Compose**: Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to specify the configuration of your application in a YAML file (`docker-compose.yml`) and manage multiple containers as a single application.

### 4. Client-Server Communication

- **REST API**: The Docker client communicates with the Docker daemon using a REST API. This API allows users to perform various operations on Docker objects programmatically.

- **Communication Channels**: The Docker client and daemon can communicate over UNIX sockets (on Linux) or named pipes (on Windows) for local communication. They can also communicate over a network interface, allowing you to connect a Docker client to a remote Docker daemon.

### Conclusion

Understanding Docker's client-server architecture and image management processes is crucial for effectively building, running, and managing Docker containers and images.







## How to create an image


1. **Run NGINX Container**:
   ```bash
   docker run -d -p 80:80 --name my-nginx nginx
   ```
   This command runs a new NGINX container in detached mode (`-d`), maps port 80 of the host to port 80 of the container (`-p 80:80`), and names the container `my-nginx`.

2. **Copy a File to the Container**:
   ```bash
   docker cp ~/Downloads/index.html my-nginx:/usr/share/nginx/html/index.html
   ```
   This command copies the `index.html` file from your local machine to the NGINX container at the specified path.

3. **Commit Changes to Create a New Image**:
   ```bash
   docker container commit -a "Your Name" -m "Added custom index.html" my-nginx my-nginx-custom
   ```
   This command commits the changes made to the `my-nginx` container, creating a new image named `my-nginx-custom` with the specified author (`-a`) and commit message (`-m`).

4. **Tag the Image**:
   ```bash
   docker tag my-nginx-custom username/my-nginx-custom:latest
   ```
   This command tags the newly created image with your Docker Hub username and a version tag (`latest` in this case). Replace `username` with your Docker Hub username.

5. **Login to Docker Hub**:
   ```bash
   docker login
   ```
   Enter your Docker Hub username and password when prompted to authenticate.

6. **Push the Image to Docker Hub**:
   ```bash
   docker push username/my-nginx-custom:latest
   ```
   This command pushes the tagged image to Docker Hub, making it available for others to use.

