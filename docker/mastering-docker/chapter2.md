# Chapter 2

# Installing Docker

In this chapter, we will discuss the system requirements for installing Docker, the installation process for various operating systems (Windows, Mac, and Linux), and how to verify the installation.

## System requirements

Docker has certain system requirements depending on the operating system you are using:

### Windows

- A 64-bit version of Windows 10 or Windows Server 2016 or later
- Virtualization must be enabled in BIOS
- Hyper-V feature should be enabled
- At least 4 GB of RAM

### Mac

- A 2010 or newer Mac, running macOS 10.14 (Mojave) or newer
- At least 4 GB of RAM

### Linux

- A 64-bit version of a supported Linux distribution
- The Linux kernel version should be 3.10 or higher
- Docker requires access to the `overlay2` storage driver or a compatible storage driver

## Docker installation on Windows, Mac, and Linux

### Windows

1. Download Docker Desktop for Windows from the [official download page](https://www.docker.com/products/docker-desktop/).

2. Double-click the installer to start the installation process.

3. Follow the on-screen instructions and choose whether to use Windows containers or Linux containers (the default option is Linux containers).

4. Restart your computer after the installation is complete.

### Mac

1. Download Docker Desktop for Mac from the [official download page](https://www.docker.com/products/docker-desktop/).

2. Double-click the downloaded `.dmg` file and drag the Docker icon to the Applications folder.

3. Open Docker Desktop from the Applications folder.

4. Follow the on-screen instructions and allow Docker Desktop to install the necessary components.

### Linux

The installation process varies between Linux distributions. Please refer to the [official documentation](https://docs.docker.com/engine/install/) for specific instructions based on your distribution.

For example, for Ubuntu, you can follow these steps:

1. Update your package index and install prerequisite packages:

```bash
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

2. Add Docker's official GPG key:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

3. Add the Docker repository:

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

4. Update your package index and install Docker Engine:

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## Verification of Docker installation

To verify that Docker is installed correctly, open a terminal or command prompt and run the following command:

```bash
docker --version
```

The output should display the Docker version installed on your system. Additionally, you can run the `hello-world` Docker container to confirm that Docker is working as expected:

```bash
docker run --rm hello-world
```

If the installation is successful, you should see a message confirming that the `hello-world` container ran successfully.

## Summing up

In Chapter 2, we covered the essential aspects of installing Docker on different operating systems. We discussed the system requirements for Windows, Mac, and Linux installations, as well as the installation process specific to each OS. After installing Docker, we provided instructions on how to verify the installation by checking the Docker version and running the hello-world container to ensure that the software is functioning correctly. This chapter serves as a foundation for getting started with Docker and preparing your environment for containerized application development and deployment.

## Knowledge Test

1. Explore Docker images and containers:

a. List all Docker images on your system with the following command:

```bash
docker images
```

b. List all running Docker containers on your system with the following command:

```bash
docker ps
```

c. List all Docker containers on your system, including stopped containers, with the following command:

```bash
docker ps -a
```
