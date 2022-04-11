# Introduction to Docker

According to the official documentation from Docker;

  - Docker is an open platform for developing, shipping, and running applications. 
  - Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. 
  - With Docker, you can manage your infrastructure in the same ways you manage your applications.

It is a containerization platform which allows developers to package programs into containers.

  - In simpler words, Docker lets you run your operating system as a container.


Docker Engine

![](https://github.com/DrVicki/docker-for-beginners/blob/main/docker.png)



Docker Engine is the layer on which Docker runs. 
  - It is installed on the host machine. 
  - It’s a lightweight runtime and tooling which manages containers, images, builds, and more. 
  - Docker Engine acts as a client-server application with:
    - A server with a long-running daemon process dockerd.
    - Rest APIs which specify interfaces programs can use to talk to and instruct the Docker daemon.
    - A command line interface (CLI) client docker.

Docker Architecture
2020-05-12-16_37_26-PowerPoint-Slide-Show-Azure_AZ104_M01_Compute_ed1-1024x534.png

Docker Architecture is made up of 5 major components:

Docker Client

Docker Daemon

Docker Host

Docker Registry

Docker Objects

Docker Client
Helps users to interact with Docker. It communicates with the Docker Daemon using the commands and rest APIs. Docker client provides a command-line interface (CLI) that allows users to run, and stop application commands to a Docker daemon.

Docker Daemon
It runs on the operating system of the host. It handles Docker objects e.g images, containes, network and volumes by listening for Docker API requests. It is used to run containers and also manage services of the Docker. A Daemon can communicate with other Daemons to manage services. Itis responsible for handling the construction, execution and distribution of Docker containers.

Docker Host
It is very important because without it, users cannot make use of Docker. It is an environment in which apllications can be executed and run. Commands issued by the client are sent over to the docker host which is recieved by the Docker daemon.

Docker Registry
Docker Registry also known as Docker Hub is a repository of Docker images for almost all technology stack where you can install or pull images.

docker.PNG

Docker Objects
These are what we interact with while using Docker, for example you use images, containers, volumes, networks or plug-ins.

Docker Images: Docker images are read-only templates with instructions to create a docker container. Docker image can be pulled from a Docker hub and used as it is, or you can add additional instructions to the base image and create a new and modified docker image. You can create your own docker images also using a dockerfile.
The base layer is read-only, and the top layer can be written. When you edit a dockerfile and rebuild it, only the modified part is rebuilt in the top layer.

Docker Containers: Docker containers are isolated, packaged, and secured application environments that contain all the packages, libraries, and dependencies required to run an application. After you run a docker image, it creates a docker container. All the applications and their environment run inside this container. You can use Docker API or CLI to start, stop, delete a docker container.
For example, if you create a container associated with the Ubuntu image, you will have access to an isolated Ubuntu environment. You can also access the bash of this Ubuntu environment and execute commands.

An explanatory example
Lets say we want to pull an image in Docker, we need to make use of the Docker pull command (one of the docker commands) which would be sent from the Client to the Docker host. The Docker Daemon is the one that recieves this command. What it would do would be to check the images contained on the docker host for the specified image which the client asked to be pulled and if that image is not present, it proceeds to pull/get the image from the registry/docker hub. It retrives the image into the Docker Host and from it, containers could be created.

You might ask why not virtual machines?

GIFfdcb71e052fd45541320d36006bfceae.gif

Well I mean, Virtual machines can provide isolated environments, they can be used to package up and distribute software which is what the Docker container does and they have also been in existence for a while but why would we go for a Docker container instead? I have explained the differences between containers and virtual machines, the perks of using a container and how to know when to use the other in this article.

Installation of Docker
Docker can be installed on these various platforms; macOs, Windows, Linux Machine. Go through this documentation for proper guidance.

Basic Docker Commands
docker build <path to docker file>
This command is used to build an image from a specified docker file

docker -version
This command is used to get the currently installed version of docker

docker run -it -d <image name>
This command is used to create a container from an image

docker ps
This command is used to list the running containers

docker ps -a
This command is used to show all the running and exited containers

docker stop <container id>
This command stops a running container

docker kill <container id>
This command kills the container by stopping its execution immediately

docker pull
This command is used to pull images from the docker repository

docker push <username/image name>
This command is used to push an image to the docker hub repository

Docker rmi <image-id>
This command is used to delete an image from local storage

docker rm <container id>
This command is used to delete a stopped container

Why Docker?
Isolation
Docker ensures your applications and resources are isolated and segregated. Docker makes sure each container has its own resources that are isolated from other containers. You can have various containers for separate applications running completely different stacks. Regardless of where the app is deployed, everything remains consistent and this leads to massive productivity: less time debugging, and more time launching fresh features and functionality for users.

Rapid Deployment
Docker-powered containers are known for decreasing deployment time to seconds. This is due to the fact that it creates a container for every process and does not boot an OS. Data can be created and destroyed without worry that the cost to bring it up again would be higher than what is affordable.

Security
Docker ensures that applications that are running on containers are completely segregated and isolated from each other, granting you complete control over traffic flow and management. No Docker container can look into processes running inside another container. From an architectural point of view, each container gets its own set of resources ranging from processing to network stacks.

Scalability
You can quickly create new containers if demand for your applications requires them. When using multiple containers you can take advantage of a range of container management options. See the Docker documentation for more information on these options.

Despite Docker's advantages,it is not suitable to run all applications in containers. In particular, it is generally accepted that applications with a graphical user interface are not suitable for use with docker.

