---
title: "Day 20: Docker Commands Cheat-Sheet"
datePublished: Tue Nov 14 2023 04:30:10 GMT+0000 (Coordinated Universal Time)
cuid: cloxu4moq000109lacpb89h6f
slug: day-20-docker-commands-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699890099039/7edaa4d8-ec42-4f18-86a7-093e471b02c5.png
tags: software-development, linux, docker, devops, software-engineering

---

### 🚀**Introduction**

As we delve into the dynamic landscape of DevOps, containerization stands out as a game-changing phenomenon, completely transforming the deployment and scalability of applications📦🚀

At the forefront of this transformative shift lies Docker – a robust platform that empowers the packaging, distribution, and execution of applications within self-contained containers🐳📦

Within this piece, we present a comprehensive compilation of Docker commands, covering tasks such as managing images and containers, orchestrating networks, and navigating complex implementation scenarios, offering you a one-stop reference for all your Docker needs📚🐳

### 📋**General Commands**

Essential commands like version information retrieval, system analysis, and help index access lay the groundwork for a successful Docker journey💼🔍

✔Display detailed information about your Docker CLI and daemon versions:

```dockerfile
docker version
```

✔List data about your Docker environment, including active plugins, containers, and images:

```dockerfile
docker system info
```

✔View the help index, which provides references for all supported commands:

```dockerfile
docker help
```

✔View detailed help information about a specific command, including option flags:

```dockerfile
docker <command> --help
```

### 🏗️**Build Images**

Constructing Docker images using Dockerfiles and tags facilitates the creation of custom and optimized environments. Options for setting build arguments and pulling updated images enhance flexibility.

✔Build the Dockerfile in your current directory into a new image:

```dockerfile
docker build .
```

✔Build the Dockerfile in your current directory and tag the image as example-image:latest:

```dockerfile
docker build -t example-image:latest .
```

✔Build the Dockerfile located at docker/app-dockerfile path:

```dockerfile
docker build -f docker/app-dockerfile
```

✔Build an image while setting the foo build argument to bar:

```dockerfile
docker build --build-arg foo=bar .
```

✔Instruct Docker to pull updated image versions referenced in FROM instructions before building:

```dockerfile
docker build --pull .
```

✔Build an image quietly without emitting build output:

```dockerfile
docker build --quiet .
```

### 🏃**Run Containers**

Launching containers from images is a core Docker operation. Commands for naming, connecting to networks, setting environment variables, and handling restart policies enable fine-grained control over container behavior.

✔Run a new container using the example-image:latest image:

```dockerfile
docker run example-image:latest
```

✔Run a command inside the container while appending it to the image's entry point:

```dockerfile
docker run example-image:latest demo-command
```

✔Run a container and automatically remove it when it exits:

```dockerfile
docker run --rm example-image:latest
```

✔Detach your terminal from the running container, leaving it in the background:

```dockerfile
docker run -d example-image:latest
```

✔Attach your terminal and a TTY to the container for interactive commands:

```dockerfile
docker run -it example-image:latest
```

✔Name the new container as my-container:

```dockerfile
docker run --name my-container example-image:latest
```

✔Set the container's hostname to my-container:

```dockerfile
docker run --hostname my-container example-image:latest
```

✔Set an environment variable foo=bar inside the container:

```dockerfile
docker run --env foo=bar example-image:latest
```

✔Populate environment variables from the file config.env:

```dockerfile
docker run --env-file config.env example-image:latest
```

✔Bind port 8080 on the host to port 80 inside the container:

```dockerfile
docker run -p 8080:80 example-image:latest
```

✔Bind mount a directory from the host to the container:

```dockerfile
docker run -v /host-directory:/container-directory example-image:latest
```

✔Mount a Docker volume named data to /data inside the container:

```dockerfile
docker run -v data:/data example-image:latest
```

✔Connect the container to a Docker network named my-network:

```dockerfile
docker run --network my-network example-image:latest
```

✔Set the container to restart automatically unless manually stopped:

```dockerfile
docker run --restart unless-stopped example-image:latest
```

✔Run the container with privileged access to the host system:

```dockerfile
docker run --privileged example-image:latest
```

### 🛠️**Manage Containers**

Efficiently handle running and stopping containers, from listing and attaching to them to committing states, inspecting details, and managing lifecycles.

✔List all running containers:

```dockerfile
docker ps
```

✔List all containers, including stopped ones:

```dockerfile
docker ps -a
```

✔Attach your terminal to a container's foreground process:

```dockerfile
docker attach <container>
```

✔Save a container's state to a new image:

```dockerfile
docker commit <container> new-image:latest
```

✔Retrieve detailed information about a container in JSON format:

```dockerfile
docker inspect <container>
```

✔Send a SIGKILL signal to a container's foreground process to force it to stop:

```dockerfile
docker kill <container>
```

✔Rename a container:

```dockerfile
docker rename <container> my-container
```

✔Pause and unpause processes within a container:

```dockerfile
docker pause <container>
docker unpause <container>
```

✔Stop a running container:

```dockerfile
docker stop <container>
```

✔Start a stopped container:

```dockerfile
docker start <container>
```

✔Delete a container by its ID or name:

```dockerfile
docker rm <container>
```

### 📂**Copy to and From Containers**

Seamlessly transfer files between containers and the host system with ease, streamlining development and data management.

✔Copy a file from your host to a container:

```dockerfile
docker cp example.txt my-container:/data
```

✔Copy a file from a container to your host:

```dockerfile
docker cp my-container:/data/example.txt /demo/example.txt
```

If transferring files between two containers, copy from the first to your host, then from your host to the second container.

### 💻**Execute Commands in Containers**

Execute commands interactively or non-interactively within running containers, enabling efficient debugging and maintenance.

✔Run a process inside a container and display the output:

```dockerfile
docker exec my-container demo-command
```

✔Run a command interactively within a container:

```dockerfile
docker exec -it my-container demo-command
```

### 📜**Access Container Logs**

Easily access and follow container logs for monitoring and troubleshooting purposes.

✔Stream existing container logs and exit:

```dockerfile
docker logs <container>
```

✔Stream existing and new logs continuously:

```dockerfile
docker logs <container> --follow
```

✔Get the last 10 logs from a container:

```dockerfile
docker logs <container> -n 10
```

Container logs consolidate data from standard output and error streams of the container's foreground process.

### 📊**View Container Resource Utilization**

Monitor resource consumption of containers to optimize performance and resource allocation.

✔Stream resource utilization information for a container:

```dockerfile
docker stats <container>
```

This provides details about CPU, memory, I/O usage, and the number of running processes.

### 🏞️**Manage Images**

List, tag, and delete images as needed, ensuring efficient image management and storage utilization.

✔List all stored images:

```dockerfile
docker images
```

✔Delete an image by its ID or tag:

```dockerfile
docker rmi <image>
```

✔Add a new tag to an existing image:

```dockerfile
docker tag <image> example-image:latest
```

### 🚀**Pull and Push Images**

Seamlessly manage images on remote registries, allowing for efficient distribution and sharing.

✔Push an image to a remote registry:

```dockerfile
docker push example.com/user/image:latest
```

✔Pull an image from a remote registry:

```dockerfile
docker pull example.com/user/image:latest
```

### 🌐**Manage Networks**

Create, connect, and disconnect containers from networks, facilitating communication and isolation between services.

✔Create a new network (default bridge driver):

```dockerfile
docker create network my-network
```

✔Create a new network with an alternative driver, e.g., host:

```dockerfile
docker create network my-network -d host
```

✔Connect a container to an existing network:

```dockerfile
docker network connect <network> <container>
```

✔Remove a container from a network:

```dockerfile
docker network disconnect <network> <container>
```

✔List available Docker networks, including built-ins like bridge and host:

```dockerfile
docker network ls
```

✔Delete a network (when no containers are connected):

```dockerfile
docker network rm <network>
```

### 📦**Manage Volumes**

Handle data storage effectively with volume creation, listing, and removal commands.

✔Create a new named volume:

```dockerfile
docker volume create my-volume
```

✔List volumes on your host:

```dockerfile
docker volume ls
```

✔Delete a volume (ensure it's not used by any container):

```dockerfile
docker volume rm <volume>
```

### 🏢**Docker Hub Account**

Interact with Docker Hub to facilitate image sharing and management.

✔Login to your account:

```dockerfile
docker login
```

✔Log out of your account:

```dockerfile
docker logout
```

✔Search Docker Hub for images:

```dockerfile
docker search nginx
```

### 🧹**Clean Up Unused Resources**

Maintain a clutter-free Docker environment by removing unused resources and optimizing space

✔Remove unused data, including dangling image layers:

```dockerfile
docker system prune
```

✔Remove all unused images:

```dockerfile
docker system prune -a
```

✔Remove volume data along with other unused resources:

```dockerfile
docker system prune --volumes
```

✔Remove dangling images:

```dockerfile
docker image prune
```

✔Remove all unused images:

```dockerfile
docker image prune -a
```

✔Remove unused networks:

```dockerfile
docker network prune
```

✔Remove unused volumes:

```dockerfile
docker volume prune
```

✔View the Docker installation's total disk usage:

```dockerfile
docker system df
```

These prune commands require confirmation before resource deletion. The -f (force) flag can be used to bypass the prompt.

### 📄**Dockerfile**

A Dockerfile is a script that contains a set of instructions for building a Docker image.

✔**Create a Dockerfile**:

Create a file named `Dockerfile` (no extension) in your project directory and define instructions.

**✔**Build an Image Using a Dockerfile\*\*:\*\*

```dockerfile
docker build -t my-image:latest .
```

This builds an image using the Dockerfile in the current directory.

✔Specify a Different Dockerfile:

```dockerfile
docker build -t my-image:latest -f path/to/Dockerfile .
```

This builds an image using a Dockerfile at a specified path.

✔Use Build Arguments:

```dockerfile
docker build -t my-image:latest --build-arg key=value .
```

This passes build arguments to the Dockerfile.

✔Build without Caching:

```dockerfile
docker build -t my-image:latest --no-cache .
```

This forces a fresh build without using the cache.

✔Set Image Metadata:

```dockerfile
docker build -t my-image:latest --label key=value .
```

This sets labels on the image.

✔Set Work Directory:

```dockerfile
WORKDIR /app
```

This sets the working directory in the Docker image.

✔Copy Files to Image:

```dockerfile
COPY src/ /app/
```

This copies files from the local machine to the image.

✔Run Commands in Image:

```dockerfile
RUN apt-get update && apt-get install -y package-name
```

This runs commands during image build.

✔Expose Ports:

```dockerfile
EXPOSE 80
```

This exposes a port when the container runs.

✔Set Environment Variables:

```dockerfile
ENV key=value
```

This sets environment variables in the image.

✔Set Container Execution Command:

```dockerfile
CMD ["executable", "arg1", "arg2"]
```

This sets the default command to run when the container starts.

✔Set Container Entrypoint:

```dockerfile
ENTRYPOINT ["executable", "arg1"]
```

This configures the entry point for the container.

✔Add Metadata to Describe the Image:

```dockerfile
LABEL key=value
```

This adds metadata labels to the image.

These commands and instructions allow you to work with Docker Compose to manage multi-container applications and create customized Docker images using Dockerfiles.

### 🎵**Docker Compose**

Docker Compose is a tool for defining and running multi-container Docker applications. It uses a YAML file to configure and manage the services, networks, and volumes of your application.

✔Define and Run Multi-Container Applications:

```dockerfile
docker-compose up
```

This command starts the services defined in your `docker-compose.yml` file.

✔Build and Run:

```dockerfile
docker-compose up --build
```

This command rebuilds images and starts services.

✔Run in Detached Mode:

```dockerfile
docker-compose up -d
```

This starts services in the background.

✔Stop Containers:

```dockerfile
docker-compose down
```

This stops and removes containers, networks, and volumes.

✔View Container Logs:

```dockerfile
docker-compose logs
```

This displays logs from all services.

✔Scale Services:

```dockerfile
docker-compose up -d --scale <service_name>=<number>
```

This scales the number of containers for a specific service.

### ⚙️**Use Configuration Contexts**

Easily switch between different Docker daemon instances for enhanced management of varied environments.

✔Create a new context to connect to a specified Docker host:

```dockerfile
docker context create my-context --host=tcp://host:2376,ca=~/ca-file,cert=~/cert-file,key=~/key-file
```

✔Modify the configuration of a context:

```dockerfile
docker context update <context>
```

✔List available contexts:

```dockerfile
docker context ls
```

✔Switch to a named context:

```dockerfile
docker context use <context>
```

✔Delete a context:

```dockerfile
docker context rm <context>
```

### 📄**Create Software Bill of Materials (SBOMs)**

Generate Software Bill of Materials (SBOMs) to track package dependencies within container images.

✔Produce an SBOM for an image:

```dockerfile
docker sbom example-image:latest
```

✔Produce an SBOM and save it to a file:

```dockerfile
docker sbom example-image:latest --output sbom.txt
```

✔Produce an SBOM in a specific format (e.g., SPDX JSON):

```dockerfile
docker sbom example-image:latest --format spdx-json
```

### 🔍**Scan for Vulnerabilities**

Integrate security practices by scanning container images for vulnerabilities, enhancing application safety.

✔Scan for vulnerabilities in an image:

```dockerfile
docker scan example-image:latest
```

✔Scan with detailed vulnerability information from a Dockerfile:

```dockerfile
docker scan example-image:latest --file Dockerfile
```

✔Scan for vulnerabilities of a specific severity level:

```dockerfile
docker scan example-image:latest --severity high
```

### 🎉**Conclusion**

In summary, this comprehensive guide delves into the essential Docker commands, Dockerfile instructions, and Docker Compose operations, providing a powerful toolkit for seamless containerization. From building custom images with precision to orchestrating multi-container applications, these commands empower developers and DevOps teams to create, manage, and optimize containerized environments. By mastering these tools, you can streamline development, enhance collaboration, and ensure the reliability and consistency of your applications across diverse platforms. With Docker's agility and versatility, you're well-equipped to navigate the intricate landscape of modern software deployment with confidence🛠️🚀🔧

Let's connect on [LinkedIn](https://www.linkedin.com/in/arjunmenon-devops/)