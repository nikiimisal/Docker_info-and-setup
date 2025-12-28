 <h1 align="center"> DOCKER</h1>

Docker is an open-source containerization platform used to build, ship,
and run applications in lightweight containers.

It solves the "works on my machine" problem by packaging the application
along with all its dependencies into a single unit called a container.


A container packages:

- your application
- all required libraries & dependencies
- configuration files

So the app runs the same way everywhere—on your laptop, servers, or cloud.

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

<br>


- Shares the host OS kernel
- Does not include a full operating system
- Runs applications faster with less resources

<br>

 In container packages:

- your application
- all required libraries & dependencies
- configuration files

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

## WHAT IS DOCKER CONTAINER

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


