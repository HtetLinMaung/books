# Chapter 3

# Docker Images

In this chapter, we will discuss Docker images, their creation, Dockerfile syntax, building Docker images, and Docker image repositories.

## What is a Docker image?

A Docker image is a lightweight, portable, and self-sufficient template that includes the application code, runtime, libraries, and dependencies required to run the application. Docker images serve as the blueprints for creating Docker containers, which are the running instances of an image. Images are organized in a layered file system, with each layer representing a set of changes made to the previous layer. This structure allows Docker to cache layers, reduce image sizes, and promote sharing and reusability.

## Creating Docker images

There are two primary methods to create Docker images:

1. Committing changes: Run a Docker container from an existing image, modify the container (e.g., by installing new packages or updating configuration files), and then commit the changes to create a new image.
2. Using a Dockerfile: Write a Dockerfile, a script containing instructions on how to build the image, and use the `docker build` command to create the image based on the Dockerfile.

The second method is considered best practice, as it provides a repeatable, version-controlled, and automated process for creating images.

## Dockerfile syntax

A Dockerfile is a text file containing a series of instructions, one per line, used to build a Docker image. Each instruction creates a new layer in the image. The most common instructions include:

- `FROM`: Sets the base image to build upon.
- `RUN`: Executes a command within the image, usually for installing packages or setting up the environment.
- `COPY`: Copies files or directories from the host system into the image.
- `ADD`: Similar to `COPY`, but also supports fetching remote files and extracting archives.
- `WORKDIR`: Sets the working directory for subsequent `RUN`, `COPY`, `ADD`, and `ENTRYPOINT` instructions.
- `CMD`: Specifies the default command to run when starting a container from the image.
- `ENTRYPOINT`: Specifies the command prefix that will be prepended to any command run in the container.
- `ENV`: Sets an environment variable within the image.
- `EXPOSE`: Indicates that the container will listen on the specified network ports at runtime.
- `VOLUME`: Creates a mount point for persistent data storage in the container.

Example of a simple Dockerfile:

```Dockerfile
# Use the official Node.js image as the base
FROM node:14

# Set the working directory
WORKDIR /app

# Copy the package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the application source code
COPY . .

# Expose the application port
EXPOSE 8080

# Start the application
CMD ["npm", "start"]
```

This Dockerfile creates a Docker image for a Node.js application, using the official Node.js image as the base, installing dependencies, copying the source code, and setting the default command to start the application.

## Building Docker images

To build a Docker image, run the `docker build` command in the same directory as the Dockerfile:

```bash
docker build -t my-image:my-tag .
```

This command will create a new Docker image with the name `my-image` and the tag `my-tag`. The `.` at the end of the command specifies that the build context (i.e., the files and directories to include in the image) is the current directory.

## Docker image repositories

Docker images can be stored and shared in centralized storage and distribution systems called Docker registries. Docker Hub is the default public registry and provides access to thousands of pre-built images and official repositories maintained by various organizations and open-source projects. Apart from Docker Hub, there are other public registries, such as Google Container Registry and Amazon Elastic Container Registry, as well as private registries that can be hosted on-premises or in the cloud.

Users can push their images to a registry and pull images from it, making it easy to share and reuse images across different environments. To push a Docker image to a registry, you first need to tag the image with the registry's URL and your username:

```bash
docker tag my-image:my-tag myusername/my-image:my-tag
```

Next, log in to the registry:

```bash
docker login
```

Enter your username and password when prompted. Finally, push the image to the registry:

```bash
docker push myusername/my-image:my-tag
```

To pull an image from a registry and run it as a container on your local machine, use the `docker pull` and `docker run` commands:

```bash
docker pull myusername/my-image:my-tag
docker run -d -p 8080:8080 myusername/my-image:my-tag
```

In this example, the `-d` flag runs the container in the background, and the `-p` flag maps port 8080 on the host to port 8080 on the container.

## Summing up

In this chapter, we explored Docker images, the foundation for creating Docker containers. We discussed what Docker images are, the process of creating them through committing changes or using a Dockerfile, the syntax and common instructions used in Dockerfiles, and how to build Docker images. Furthermore, we looked into Docker image repositories, where images can be stored and shared, enabling easy distribution across different environments. By understanding how to create, build, and manage Docker images, you can efficiently develop, test, and deploy your applications using containers.

## Knowledge Test

1. Create a simple Dockerfile for a Python web application:

a. Use the official Python 3.9 image as the base.
b. Set the working directory to `/app`.
c. Copy the `requirements.txt` file and install the dependencies using `pip`.
d. Copy the application source code.
e. Expose port 5000.
f. Set the default command to run the application using `python app.py`.

2. Build a Docker image using the Dockerfile created in exercise 1. Name the image `my-python-webapp` and tag it with `v1`.

3. Run a container using the image created in exercise 2. Map the container's port 5000 to the host's port 5000, and run the container in the background.

4. Push the `my-python-webapp:v1` image to a Docker registry of your choice (e.g., Docker Hub, Google Container Registry, Amazon Elastic Container Registry). If you don't have an account, create one and follow the necessary steps to push the image.

5. Pull the `my-python-webapp:v1` image from the registry to another machine or a colleague's machine and run a container using the pulled image. Verify that the application is running and accessible on port 5000.
