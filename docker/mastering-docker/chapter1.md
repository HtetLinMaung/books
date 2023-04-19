# Chapter 1

# Introduction to Docker

## What is Docker?

Docker is an open-source platform that automates the deployment, scaling, and management of applications using containerization technology. Containers are lightweight, portable, and self-sufficient environments that package all the necessary dependencies, libraries, and configuration files required for an application to run consistently across different environments. This allows developers and IT professionals to streamline application development, testing, and deployment processes, reducing the "works on my machine" problem and ensuring that applications run smoothly in production.

## The history of Docker

Docker was created by Solomon Hykes and initially released as an open-source project in 2013. It was built on top of the Linux container technology (LXC), leveraging existing Linux kernel features such as namespaces and cgroups to provide isolation between containers. The project quickly gained popularity and attracted the attention of developers and organizations worldwide, leading to the formation of Docker, Inc., which continues to maintain and develop the platform.

## The advantages of using Docker

1. Consistency: Docker containers provide a consistent environment for applications, eliminating differences between development, testing, and production environments. This reduces the risk of encountering unexpected issues during deployment.

2. Portability: Docker containers can run on any platform that supports Docker, making it easy to migrate applications between different cloud providers or local development environments.

3. Scalability: Docker enables easy scaling of applications by running multiple containers on the same host or distributing containers across multiple hosts.

4. Isolation: Containers run in isolation, providing a secure environment for applications and preventing conflicts between different application dependencies.

5. Resource Efficiency: Containers share the host operating system kernel and resources, resulting in lower overhead compared to virtual machines.

## Docker architecture

Docker utilizes a client-server architecture where the Docker client communicates with the Docker daemon, which is responsible for building, running, and managing Docker containers. The Docker client and daemon can run on the same host or communicate over a network. Docker images, which are the blueprints for containers, are stored in registries, and Docker Hub is the default public registry.

## Docker components

1. Docker Engine: The core component responsible for creating and managing containers.
2. Docker Image: A lightweight, portable, and self-sufficient template that includes the application code, runtime, libraries, and dependencies required to run the application.
3. Docker Container: A running instance of a Docker image, providing an isolated environment for the application.
4. Docker Registry: A centralized storage and distribution system for Docker images, allowing users to share and reuse images across different environments.
5. Docker Compose: A tool for defining and running multi-container applications using a single YAML configuration file.

## Summing up

In Chapter 1, we introduced Docker, an open-source platform that leverages containerization technology to automate application deployment, scaling, and management. We discussed the history of Docker and its various advantages, such as consistency, portability, scalability, isolation, and resource efficiency. We also explored Docker's client-server architecture, where the Docker client communicates with the Docker daemon for building, running, and managing containers. Lastly, we delved into the primary Docker components: Docker Engine, Docker Image, Docker Container, Docker Registry, and Docker Compose, highlighting their roles in the Docker ecosystem.

## Knowledge Test

1. Install Docker on your local machine:

Follow the official Docker documentation to install Docker on your preferred operating system:

- [Windows](https://docs.docker.com/desktop/install/windows-install/)
- [Mac](https://docs.docker.com/desktop/install/mac-install/)
- [Linux](https://docs.docker.com/engine/install/)

2. Run a basic Docker container:

After installing Docker, open a terminal or command prompt and run the following command to download and run a basic "Hello, World!" Docker container:

```bash
docker run --rm hello-world
```

The output should display a message confirming the successful execution of the "hello-world" container.

3. Create a simple Node.js application:

a. Create a new directory called "node-app" and navigate to it:

```bash
mkdir node-app
cd node-app
```

b. Create a file named "app.js" with the following content:

```javascript
const http = require("http");

const hostname = "0.0.0.0";
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello, Docker!\n");
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

c. Create a "Dockerfile" with the following content:

```Dockerfile
FROM node:14

WORKDIR /usr/src/app

COPY app.js .

EXPOSE 3000

CMD ["node", "app.js"]
```

d. Build the Docker image for the Node.js application:

```bash
docker build -t node-app-image .
```

e. Run the Docker container:

```bash
docker run --rm -d -p 3000:3000 --name node-app-container node-app-image
```

f. Open a web browser and navigate to http://localhost:3000. You should see "Hello, Docker!" displayed in your browser.

4. Explore Docker Hub:

Visit the [Docker Hub](https://hub.docker.com/) website and explore the available public Docker images. Find an image that interests you, and follow the instructions in the image's documentation to download and run a container using that image.

5. Stop and remove the Node.js container:

When you're finished exploring, run the following command to stop and remove the Node.js container created in step 3:

```bash
docker stop node-app-container
```
