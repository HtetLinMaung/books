# Chapter 9

# Docker for Continuous Integration and Delivery

In this chapter, we will discuss the role of Docker in Continuous Integration (CI) and Continuous Delivery (CD) pipelines. We will also explore how Docker can be integrated with popular CI/CD tools like Jenkins, Travis CI, and CircleCI.

## Docker and CI/CD

Docker has become an essential tool in modern CI/CD pipelines, as it helps streamline the build, test, and deployment process for applications. The use of Docker enables developers to create consistent, reproducible environments that can be easily shared and maintained. This helps reduce the likelihood of encountering environment-specific issues during the development process.

Some benefits of using Docker in CI/CD pipelines include:

- Faster build times: Docker can cache intermediate build stages, reducing the time it takes to build and deploy applications.
- Consistent environments: Docker ensures that the application runs in a consistent environment throughout the entire pipeline, reducing the likelihood of encountering environment-specific issues.
- Isolation: Docker containers isolate applications and their dependencies, allowing multiple applications with conflicting dependencies to run on the same CI/CD environment.
- Resource efficiency: Containers are lightweight and share resources efficiently, making it possible to run multiple CI/CD pipelines on the same hardware.

## Docker and Jenkins

Jenkins is an open-source automation server that supports CI/CD processes. It is highly extensible, with hundreds of plugins available for various tasks, including integrating with Docker.

There are two main ways to use Docker with Jenkins:

1. Running Jenkins inside a Docker container: This method involves running the Jenkins server itself inside a Docker container. This provides an easy way to set up and maintain Jenkins environments.

Example: Running Jenkins in a Docker container

```bash
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

2. Using Docker in Jenkins pipelines: This method involves using Docker containers as build environments for Jenkins jobs. Jenkins pipelines can leverage Docker images to build, test, and package applications in isolated environments.

Example: Using Docker in a Jenkins pipeline

```
pipeline {
    agent {
        docker {
            image 'node:14'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
```

This pipeline uses a Node.js Docker image to run the build and test stages of a Node.js application.

## Docker and Travis CI

Travis CI is a popular hosted CI/CD service. It supports a wide variety of programming languages and platforms, and has built-in support for Docker.

To use Docker in Travis CI, you need to enable the Docker service in the .travis.yml configuration file.

Example: Using Docker in Travis CI

Create a `.travis.yml` file with the following content:

```yaml
language: node_js
node_js:
  - "14"
services:
  - docker
script:
  - npm install
  - npm test
  - docker build -t my-application .
```

This configuration sets up a Travis CI pipeline for a Node.js application, using Docker to build a container image for the application after running tests.

## Docker and CircleCI

CircleCI is another popular hosted CI/CD service. It provides native support for Docker and allows you to define your CI/CD pipeline using a `config.yml` file.

Example: Using Docker in CircleCI

Create a `.circleci/config.yml` file with the following content:

```yaml
version: 2.1
jobs:
  build:
    docker:
      - image: node:14
    steps:
      - checkout
      - run: npm install
      - run: npm test
      - setup_remote_docker
      - run: docker build -t my-application .

workflows:
  version: 2
  build-deploy:
    jobs:
      - build
```

This configuration sets up a CircleCI pipeline for a Node.js application. The pipeline uses a Node.js Docker image to run the build and test stages of the application, and then builds a Docker container image for the application.

In conclusion, Docker plays a crucial role in modern CI/CD pipelines by streamlining the build, test, and deployment process for applications. Integrating Docker with popular CI/CD tools like Jenkins, Travis CI, and CircleCI ensures consistent, reproducible environments throughout the entire pipeline. This results in reduced build times, fewer environment-specific issues, and more efficient resource utilization. By incorporating Docker into your CI/CD pipeline, you can improve the overall quality and speed of your software development and delivery process.

## Summing up

n Chapter 9, we explore the essential role of Docker in Continuous Integration (CI) and Continuous Delivery (CD) pipelines and its integration with popular CI/CD tools like Jenkins, Travis CI, and CircleCI. By streamlining the build, test, and deployment processes, Docker enables the creation of consistent, reproducible environments that can be easily shared and maintained, reducing the likelihood of encountering environment-specific issues. Some benefits of using Docker in CI/CD pipelines include faster build times, consistent environments, isolation, and resource efficiency. Examples for integrating Docker with Jenkins, Travis CI, and CircleCI are also provided, highlighting the advantages of incorporating Docker into your CI/CD pipeline to improve the overall quality and speed of your software development and delivery process.

## Knowledge Test

1. Setting up Jenkins with Docker

- Pull the official Jenkins Docker image.
- Run Jenkins in a Docker container.
- Visit Jenkins on your local machine using your web browser (hint: the default port is 8080).

2. Dockerizing a Simple Node.js Application

- Create a simple Node.js application with a `package.json` file and a basic test.
- Write a Dockerfile for the Node.js application.
- Build a Docker image for the application.
- Run the application in a Docker container.

3. Using Docker in a Jenkins Pipeline

- Create a Jenkins pipeline configuration that uses a Docker container as a build environment for your Node.js application from Exercise 2.
- Run the Jenkins pipeline, and ensure that the build and test stages execute successfully in the Docker container.

4. Using Docker with Travis CI

- Sign up for a Travis CI account (if you don't have one already) and set up a new repository with your Node.js application from Exercise 2.
- Create a `.travis.yml` configuration file that uses Docker to build a container image for the application after running tests.
- Push your changes to the repository, and verify that Travis CI successfully builds and tests your application using Docker.

5. Using Docker with CircleCI

- Sign up for a CircleCI account (if you don't have one already) and set up a new repository with your Node.js application from Exercise 2.
- Create a `.circleci/config.yml` configuration file that uses Docker to build a container image for the application after running tests.
- Push your changes to the repository, and verify that CircleCI successfully builds and tests your application using Docker.
