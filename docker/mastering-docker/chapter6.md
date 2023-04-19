# Chapter 6

# Docker Swarm

In this chapter, we will explore Docker Swarm, setting up a Docker Swarm cluster, swarm management commands, service creation and scaling, and load balancing in Docker Swarm.

## What is Docker Swarm?

Docker Swarm is a native orchestration tool for Docker that allows you to create and manage a swarm of Docker nodes and deploy services across them. It provides fault tolerance, scaling, and load balancing features for distributed applications. Docker Swarm employs a declarative approach to service deployment, which means you define the desired state of the service, and Docker Swarm takes care of maintaining that state.

## Setting up a Docker Swarm cluster

To set up a Docker Swarm cluster, you need at least one manager node and one or more worker nodes. Manager nodes are responsible for maintaining the cluster state, while worker nodes execute tasks and run containers.

To initialize a swarm and create a manager node, run the following command on the manager node:

```bash
docker swarm init --advertise-addr [MANAGER_IP]
```

Replace `[MANAGER_IP]` with the IP address of the manager node. The command will return a token that you will use to join worker nodes to the swarm. Save this token for later use.

To join a worker node to the swarm, run the following command on the worker node:

```bash
docker swarm join --token [TOKEN] [MANAGER_IP]:2377
```

Replace `[TOKEN]` with the token obtained from the manager node, and `[MANAGER_IP]` with the manager node's IP address.

## Swarm management commands

Docker provides several commands to manage the swarm and its nodes:

`docker node ls`: Lists all nodes in the swarm.
`docker node inspect [NODE_ID]`: Displays detailed information about a specific node.
`docker node promote [NODE_ID]`: Promotes a worker node to a manager node.
`docker node demote [NODE_ID]`: Demotes a manager node to a worker node.
`docker node rm [NODE_ID]`: Removes a node from the swarm.

## Service creation and scaling in Docker Swarm

To create a service in Docker Swarm, use the `docker service create` command:

```bash
docker service create --name my-service --replicas 3 --publish published=8080,target=80 nginx
```

In this example, we create a service named `my-service` that runs three replicas of the `nginx` image. We publish port 8080 on the swarm nodes and map it to port 80 on the containers.

To scale a service in Docker Swarm, use the `docker service update` command with the `--replicas` flag:

```bash
docker service update --replicas 5 my-service
```

In this example, we scale the my-service to have five replicas.

## Load balancing in Docker Swarm

Docker Swarm provides built-in load balancing for services. When a service is published with the `--publish` flag, as in the example above, Docker Swarm automatically sets up a load balancer that distributes incoming requests to the service instances across the swarm nodes.

In addition, Docker Swarm supports service discovery and internal load balancing between services. Services can communicate with each other using their service names as hostnames, and Docker Swarm will load balance the traffic between the instances of the target service.

In conclusion, Docker Swarm is a powerful orchestration tool for Docker that simplifies the deployment and management of distributed applications. It provides built-in load balancing, service discovery, and scaling features, making it an excellent choice for deploying and managing containerized applications at scale.

## Summing up

In this chapter, we delved into Docker Swarm, a native orchestration tool for Docker. We discussed how to set up a Docker Swarm cluster consisting of manager and worker nodes, various swarm management commands, and how to create and scale services within the swarm. We also covered the built-in load balancing capabilities offered by Docker Swarm, including service discovery and internal load balancing between services. Docker Swarm's powerful features make it an ideal solution for deploying and managing containerized applications at scale, simplifying the process and ensuring application availability and performance.

## Knowledge Test

1. Set up a Docker Swarm cluster with one manager node and two worker nodes. To simulate this environment, you can use three separate virtual machines or cloud instances.

- Initialize the swarm on the manager node.
- Join the two worker nodes to the swarm using the token obtained from the manager node.

2. Create a new Docker service in the swarm:

Name the service `my-web-app`.
Use the `httpd:latest` image.
Set the desired number of replicas to 3.
Publish the service on port 8080, mapping it to port 80 on the container.

3. Inspect the state of the swarm and the created service:

- List all nodes in the swarm.
- Display detailed information about one of the worker nodes.
- Inspect the service `my-web-app` to review its configuration and status.

4. Scale the `my-web-app` service to have 5 replicas. Verify that the number of replicas has been updated by inspecting the service again.

5. Experiment with node management commands:

- Promote one of the worker nodes to a manager node.
- Demote the promoted node back to a worker node.
- Remove one of the worker nodes from the swarm.

6. Deploy a second service in the swarm that acts as a backend for the `my-web-app` service:

- Name the service `my-backend`.
- Use the `redis:latest` image.
- Set the desired number of replicas to 2.

7. Verify that the two services can communicate with each other using their service names as hostnames. (Hint: You can use the `docker exec` command to run a command inside a container to test connectivity.)
