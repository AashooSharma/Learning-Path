# Docker Images and Containers

Welcome to the Docker Images and Containers README! This section will provide you with an in-depth understanding of Docker images and containers. You will learn how to create Docker images using Dockerfiles, explore the Docker image registry, and master the creation, management, and interaction with Docker containers. Let's dive into the detailed step-by-step instructions for each topic.

## Table of Contents

- [Understanding Docker Images](#understanding-docker-images)
  - [What are Docker Images?](#what-are-docker-images)
  - [Creating Docker Images with Dockerfiles](#creating-docker-images-with-dockerfiles)
  - [Exploring the Docker Image Registry](#exploring-the-docker-image-registry)
- [Working with Docker Containers](#working-with-docker-containers)
  - [Creating Docker Containers](#creating-docker-containers)
  - [Managing Docker Containers](#managing-docker-containers)
  - [Interacting with Docker Containers](#interacting-with-docker-containers)
  - [Additional Docker Commands](#additional-docker-commands)


## Understanding Docker Images

### What are Docker Images?

Docker images are the building blocks of containers. An image is a lightweight, standalone, and executable package that includes everything needed to run an application - code, runtime, libraries, environment variables, and more. Docker images are based on a layered file system, allowing for efficient sharing and reusability.

### Creating Docker Images with Dockerfiles

Dockerfiles are text files that contain instructions for building a Docker image. These instructions specify the base image, add application code and dependencies, set environment variables, and configure the image behavior. By following the steps in the Dockerfile, you can create consistent and reproducible images for your applications.

Here's an example Dockerfile for a Node.js application:

```Dockerfile
# Use the official Node.js image as the base image
FROM node:14

# Set the working directory inside the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Expose the application port
EXPOSE 3000

# Define the command to run the application
CMD ["npm", "start"]
```

### Exploring the Docker Image Registry

Docker provides a centralized repository called the Docker image registry, which stores Docker images. The default public registry is Docker Hub, where you can find a vast collection of pre-built images. You can also create and use private registries for secure image storage within your organization.

To pull an image from Docker Hub, use the `docker pull` command:

```bash
docker pull nginx:latest
```

## Working with Docker Containers

### Creating Docker Containers

To run an application, you need to create a container from a Docker image. Containers are instances of Docker images, and they run in an isolated environment with their own file systems, processes, and network interfaces. You can create containers using the `docker run` command and specify various options such as ports, volumes, and environment variables.

To create a container from an image, use the following command:

```bash
docker run -d -p 8080:80 --name my_nginx nginx:latest
```

This command creates a container named `my_nginx` from the `nginx:latest` image, maps port 8080 on the host to port 80 in the container, and runs the container in detached mode (`-d`).

### Managing Docker Containers

Docker provides commands for managing containers throughout their lifecycle. You can start, stop, restart, pause, and remove containers as needed. Monitoring container logs and resource usage is also essential for effective container management.

To list all running containers, use:

```bash
docker ps
```

To stop a running container, use:

```bash
docker stop CONTAINER_ID_or_NAME
```

To remove a stopped container, use:

```bash
docker rm CONTAINER_ID_or_NAME
```

### Interacting with Docker Containers

Interacting with Docker containers involves executing commands inside the container or accessing the application running within it. The `docker exec` command allows you to run commands interactively inside a running container.

For example, to open a shell session inside a container, use:

```bash
docker exec -it CONTAINER_ID_or_NAME sh
```

This command opens a shell session (`sh`) inside the specified container in interactive mode (`-it`).


## Additional Docker Commands

### List All Containers

To list all containers, both running and stopped, use the `docker ps -a` command. This command provides information about each container, including their container ID, status, names, ports, and more.

```bash
docker ps -a
```

### Stop All Containers

To stop all running containers at once, you can use a combination of `docker ps -q` to get the container IDs of all running containers and `docker stop` to stop them.

```bash
docker stop $(docker ps -q)
```

### Remove All Stopped Containers

To remove all stopped containers from your system, use the `docker container prune` command. This command cleans up all stopped containers, freeing up disk space.

```bash
docker container prune
```

### Remove All Unused Images

To remove all unused Docker images (dangling images), which are images that are not associated with any containers, you can use the `docker image prune` command.

```bash
docker image prune
```

### View Container Logs

To view the logs of a specific container, use the `docker logs` command followed by the container's name or ID.

```bash
docker logs CONTAINER_ID_or_NAME
```

### Execute a Command in a Running Container

You can execute a command inside a running container using the `docker exec` command.

```bash
docker exec -it CONTAINER_ID_or_NAME COMMAND
```

For example, to open a shell session inside a running container:

```bash
docker exec -it CONTAINER_ID_or_NAME sh
```

### Copy Files Between Host and Container

To copy files between the host and a container, use the `docker cp` command. This command allows you to transfer files to and from containers.

To copy a file from the host to a container:

```bash
docker cp HOST_PATH CONTAINER_ID_or_NAME:CONTAINER_PATH
```

To copy a file from a container to the host:

```bash
docker cp CONTAINER_ID_or_NAME:CONTAINER_PATH HOST_PATH
```

### Rename a Container

To rename an existing container, use the `docker rename` command followed by the current container name and the new name.

```bash
docker rename CURRENT_NAME NEW_NAME
```

### Pause and Unpause a Container

You can pause and unpause a running container using the `docker pause` and `docker unpause` commands, respectively.

To pause a container:

```bash
docker pause CONTAINER_ID_or_NAME
```

To unpause a container:

```bash
docker unpause CONTAINER_ID_or_NAME
```

### Prune Unused Docker Resources

To clean up unused Docker resources, such as stopped containers, unused networks, and dangling images, use the `docker system prune` command.

```bash
docker system prune
```

These special Docker commands can be very helpful in managing your containers and images efficiently. By incorporating them into your Docker workflow, you can streamline your development and deployment processes.

## Next Steps

With a solid understanding of Docker images and containers, you're well-equipped to continue your Docker journey. In the "Table of Contents" above, you'll find links to more topics, including Docker networking, volumes, and orchestration tools.

Feel free to experiment with Docker images and containers to gain hands-on experience. By mastering these concepts, you'll be able to efficiently deploy and manage containerized applications. Happy containerizing! 😊


