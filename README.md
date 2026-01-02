 <h1 align="center"> DOCKER</h1>
 
- [Overview](#example-0)
- [Docker-Setup](#example-1)
- [Some Command's](#example-2)

<a id="example-0"></a>

Docker is an open-source containerization platform used to build, ship,
and run applications in lightweight containers.

It solves the "works on my machine" problem by packaging the application
along with all its dependencies into a single unit called a container.


A container packages:

- your application
- all required libraries & dependencies
- configuration files

So the app runs the same way everywhere—on your laptop, servers, or cloud.

| **Docker-Workflow** | **How it works** |
|--------------------|-----------------|
| <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/docker%20workflow.png?raw=true" width="400"/> | <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/d%20work.png?raw=true" width="400"/> |

--------------------------------------------------
## 📌 Who created Docker?

- Creator: Solomon Hykes
- Company: dotCloud
- Year started: 2010
- Public launch: 2013 (PyCon Conference)
- Donated to CNCF: 2017

👉 Docker became open-source, and the container ecosystem became popular.

--------------------------------------------------

## Key Docker Components

### Docker Image
- Read-only template used to create containers
- Example: `nginx`, `mysql`, `ubuntu`

### Docker Container
- Running instance of a Docker image

### Dockerfile
- Text file with instructions to build an image
  
Example:


```Dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html/
```

### Docker Engine

- Core service that runs containers

### Docker Hub

- Public/private image registry
- Like GitHub, but for Docker images


--------------------------------------------------

## WHY DOCKER was created?

Before Docker:

- App worked on developer machine
- Failed on QA / Prod server
- “It works on my machine” problem 😅

Docker solves this by:

- Providing same environment everywhere
- Making apps portable, lightweight, fast


--------------------------------------------------

## WHAT IS A CONTAINER?

A container is a lightweight, isolated environment in which:

- Application
- Libraries
- Dependencies
- Configurations

  - Shares the host OS kernel
  - Does not include a full operating system
  - Runs applications faster with less resources


All of this is bundled into a single package.
  
❌ A container does not have a full operating system.<br>
✅ It shares the host machine’s kernel.




--------------------------------------------------

## Container vs Virtual Machine (VM)

| Feature        | Container      | Virtual Machine |
| -------------- | -------------- | --------------- |
| OS             | Shares host OS | Full OS         |
| Size           | MBs            | GBs             |
| Speed          | Very fast      | Slow            |
| Resource usage | Low            | High            |
| Boot time      | Seconds        | Minutes         |

👉 Docker containers are NOT virtual machines

  <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/containers_vs_vm.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

--------------------------------------------------

## DOCKER ARCHITECTURE

0. End User

1. Docker Client
   - CLI tool (docker run, docker build, docker pull)

2. Docker Daemon (dockerd)
   - Runs containers
   - Builds images
   - Manages networks & volumes

3. Docker Registry
   - Stores Docker images
   - Example: Docker Hub

--------------------------------------------------

## What Is DOCKER IMAGE.?


A Docker Image is:

- Read-only template
- Blueprint for creating containers

Example:

- `nginx` image
- `mysql` image
- `python:3.10` image

Think like:

>Image = Class<br>
Container = Object


--------------------------------------------------

## WHAT IS DOCKER CONTAINER .?

A container is a running instance of an image.

Example:
```
docker run nginx
```

- Image: nginx
- Container: running nginx web server

You can run multiple containers from one image.

--------------------------------------------------

## DOCKERFILE (How image is built)

A text file containing instructions to build an image

Example:
```
FROM python:3.10
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

Steps:

1. Write Dockerfile
2. Build image
3. Run container
   
--------------------------------------------------

## DOCKER WORKFLOW (End-to-End)

1. Write application code
2. Create Dockerfile
3. Build Docker image
4. Push image to registry
5. Pull image on server
6. Run container

--------------------------------------------------

## ADVANTAGES OF DOCKER

✅ Portability <br>
✅ Faster deployment<br>
✅ Consistent environments<br>
✅ Easy rollback<br>
✅ Microservices friendly<br>
✅ DevOps & CI/CD ready<br>

--------------------------------------------------
---
---
<a id="example-1"></a>

 <h1 align="center"> DOCKER SETUP</h1>

We can directly launch an EC2 instance by going to the AWS Console just for `practice`.<br>

But as a `Best practice`, instead of doing it manually, we should launch EC2 using Infrastructure as Code tools like Terraform (or similar tools) that are used to create infrastructure.

  <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20080908.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

- For better understanding, let’s change the hostname and assume we are working inside a Docker container.

```
sudo hostnamectl hostname Docker
```
- Switching to the root user.

```
  sudo -i
```
- Update the system

```
yum update
```
- install the docker

```
yum install docker -y
```

 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20081233.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

- After that, start the Docker service, enable it, and verify its status.

  ```
  systemctl start docker
  systemctl enable docker
  systemctl status docker
  ```

 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20081424.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

- Check docker version
- Docker default directory
- Check whether images are available on your local machine. ( To list out the images )

```
docker --version
cd /var/lib/docker/
docker images

```
   <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20081816.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

- Then run this command

```
docker run nginx
```
When the command was executed, the output showed that no image was found locally.<br>
So Docker started pulling the image from the Docker Hub registry.  

 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20083959.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---




The container has started, but I am not able to enter commands because the previous command is<br>
running in the Docker foreground. The terminal got stuck.<br>
We want the container to run in the background, so here is the command.

```
docker run -d nginx
```

- List out the running state container Command
- List out the images
- list out the all containers  ( -a represent all )

```
docker ps
docker images
docker ps -a
```


 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20090212.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

- Previously, to access the server, we opened a browser and entered the public IP address to view the Nginx page.
- Now it is not visible because the concept of `port mapping` comes into play here.
- Verify by entering the IP address in a web browser.
- Stop and remove the previous container before running with container port mapping.


```
docker ps -a
docker stop b4f 160
docker ps -a
docker rm b4f 160
docker ps -a
```

Here is the command for port mapping. Now, verify that the Nginx page is visible in the browser.
```
docker run -d -p 80:80 --name mynginx nginx
docker ps 
```

 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20092107.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

 <p align="center">
  <img src="https://github.com/nikiimisal/Docker_info-and-setup/blob/main/img/Screenshot%202025-12-29%20092210.png?raw=true" width="500" alt="Initialize Repository Screenshot">
</p>

---

---
---

<a id="example-2"></a>

 <h1 align="center"> COMMAND'S</h1>

###  🔹 Docker Installation & Service Setup

```
yum update
# Update all system packages

yum install docker -y
# Install Docker using yum package manager

systemctl start docker
# Start Docker service

systemctl enable docker
# Enable Docker to start automatically on system boot

systemctl status docker
# Check Docker service status

docker --version
# Verify Docker installation and check version


```

---

### 🔹 Docker Directory Check 

```
cd /var/lib/docker/
# Navigate to Docker's default data directory

ls
# List Docker internal files and directories


```

---

### 🔹 Docker Images & Containers 

```
docker images
# List all Docker images available locally

docker run nginx
# Pull nginx image (if not present) and run container in foreground

docker run -d nginx
# Run nginx container in detached (background) mode


# This command has three parts. They are combined into one for single-step execution, or you can run them separately.
docker run nginx

i.
docker pull nginx    # image pull's

ii.
docker create nginx   # images create

iii.
docker start nginx    # images start

```

---

###  🔹 Container Status Commands

```
docker ps
# Show currently running containers

docker ps -a
# Show all containers (running + stopped)
```

---

### 🔹 Stop & Remove Containers

```

docker stop 827
# Stop container with ID starting with 827

docker rm 827 543
# Remove stopped containers with IDs 827 and 543

docker rm -f 5ec
# Force remove running container with ID 5ec
------------------------------------------------------------------------------

docker rm -f $(docker ps -aq)
# Stop and remove all containers forcefully

--------------------------------------------------------------------------------
docker images
# List all images

docker rmi $(docker images -aq)
# Remove all Docker images
```

---

### 🔹 Run Container with Port Mapping 

> `p` `manually Port assign` & `P` `Dynamic Port Assignment`

```
docker run -d -p 80:80 --name mynginx nginx
# Run nginx container in background
# Map host port 80 to container port 80
# Assign container name as "mynginx"
```

---

###  🔹 Automatic Port Mapping

```
docker run -d -P nginx
# Run nginx container with automatic port mapping

docker run -dP httpd
# Run Apache (httpd) container with auto port mapping
```

---

### 🔹 Execute Commands Inside Running Container

```
docker exec -it 4e3 pwd
# Print current working directory inside container

docker exec -it 4e3 whoami
# Show current user inside container

docker exec -it 4e3 ls
# List files inside container

docker exec -it 4e3 /bin/bash
# Login into container shell interactively
```

```
docker exec -it 4e3 /bin/bash     # Enter the running container shell

cd /usr/share/nginx/html/         # Go to Nginx default web directory

ls                                # List files in current directory

cat /etc/os-release               # Check OS inside the container

apt update                        # Update package index inside container

apt install nano -y               # Install nano editor inside container

nano index.html                   # Edit Nginx default web page

curl http://localhost             # Test Nginx page from inside container

exit                              # Exit from container shell

docker ps                         # List running containers

docker ps -a                      # List all containers

docker images                     # List Docker images

docker stop <container_id>        # Stop running container

docker rm <container_id>          # Remove stopped container
```

---






















---

---
---






