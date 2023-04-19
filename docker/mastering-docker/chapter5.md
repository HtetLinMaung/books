# Chapter 5

# Docker Compose

In this chapter, we will cover Docker Compose, its installation process, writing a Docker Compose file, starting and stopping services, and scaling services with Docker Compose.

## What is Docker Compose?

Docker Compose is a tool that simplifies the management of multi-container applications. It allows developers to define, configure, and run multi-container applications using a single declarative configuration file, typically named `docker-compose.yml`. Compose enables users to streamline the process of building, deploying, and managing multi-container applications by handling tasks such as container creation, starting, stopping, and scaling.

## Installing Docker Compose

Docker Compose comes installed with Docker Desktop for Windows and macOS. However, for Linux users, Docker Compose needs to be installed separately. To install Docker Compose on Linux, follow the instructions in the [official documentation](https://docs.docker.com/compose/install/).

## Writing a Docker Compose file

A Docker Compose file is a YAML file that defines services, networks, and volumes. A simple Docker Compose file could look like the following example:

```yaml
version: "3.9"
services:
  web:
    image: my-web-app:latest
    build: .
    ports:
      - "8080:80"
  database:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```

In this example, we define two services: `web` and `database`. The `web` service is built from the current directory (`build: .`) and uses the `my-web-app:latest` image. It maps port 8080 on the host to port 80 on the container. The database service uses the `mysql:5.7` image and sets an environment variable `MYSQL_ROOT_PASSWORD`.

## Starting and stopping Docker Compose services

To start the services defined in a `docker-compose.yml` file, navigate to the directory containing the file and run the following command:

```bash
docker-compose up
```

This command will start the services in the foreground and display their logs in the terminal. To start the services in the background, use the `-d` (detached) flag:

```bash
docker-compose up -d
```

To stop the services, run the following command:

```bash
docker-compose down
```

## Scaling services with Docker Compose

Docker Compose allows users to scale services by running multiple instances of a single service. To scale a service, use the `docker-compose up` command with the `--scale` flag followed by the service name and the desired number of instances:

```bash
docker-compose up -d --scale web=3
```

In this example, we scale the `web` service to run three instances.

When using Docker Compose to scale services, ensure that the services are designed to handle multiple instances, such as by using load balancing or other clustering techniques.

In conclusion, Docker Compose is a powerful tool for managing multi-container applications. It simplifies the deployment and scaling process, making it easier to manage complex applications consisting of multiple interconnected services.

## Summing up

In summary, this chapter focused on Docker Compose, a valuable tool for managing multi-container applications. The chapter covered Docker Compose's installation process, composing a Docker Compose file, and starting, stopping, and scaling services. Docker Compose simplifies the deployment and scaling process, allowing developers to define, configure, and run multi-container applications using a single declarative configuration file, typically named `docker-compose.yml`. By efficiently handling tasks such as container creation, starting, stopping, and scaling, Docker Compose streamlines the management of complex applications that consist of multiple interconnected services.

## Knowledge Test

1. Install Docker Compose on your machine (if not already installed). If you are using Windows or macOS, Docker Compose should already be installed with Docker Desktop. For Linux users, follow the instructions in the [official documentation](https://docs.docker.com/compose/install/).

2. Create a new directory named `my-compose-project`, and inside it, create a file named `docker-compose.yml`. Write a Docker Compose file with the following services:

- A web service that uses the `nginx:latest` image and maps port 8080 on the host to port 80 on the container.
- A redis service that uses the `redis:latest` image.

3. Navigate to the `my-compose-project` directory in your terminal and start the services by running the following command:

```bash
docker-compose up -d
```

4. Verify that the services are running using the `docker-compose ps` command. You should see the `web` and `redis` services listed.

5. Access the `web` service by visiting http://localhost:8080 in your browser. You should see the default Nginx welcome page.

6. Stop the services by running the following command:

```bash
docker-compose down
```

7. Modify the `docker-compose.yml` file to scale the `web` service to 3 instances. Hint: you can use the `replicas` key under the `deploy` key for the `web` service:

```yaml
web:
  # ...
  deploy:
    replicas: 3
```

8. Start the services again using the `docker-compose up -d` command. Note that you'll need to use the `--compatibility` flag when using the `deploy` key in a non-swarm mode:

```bash
docker-compose up -d --compatibility
```

9. Check the status of the services using `docker-compose ps` and ensure that there are three instances of the `web` service running.

10. Stop and remove the services by running `docker-compose down`.
