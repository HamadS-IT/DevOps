# What Are `Docker` Commands?

Docker commands are instructions used via the **Docker CLI (Command Line Interface)** to build, run, manage, and inspect Docker images and containers.

They allow developers to control Docker from the terminal efficiently.

---

## Docker Command Structure

```bash
docker <command> <subcommand> [options]
````

Example:

```bash
docker container ls
```

---

## Most Common Docker Commands

### Check Docker Version

```bash
docker --version
```

---

## Image Commands

### List Images

```bash
docker images
```

### Pull an Image

```bash
docker pull nginx
```

### Build an Image

```bash
docker build -t my-app .
```

### Remove an Image

```bash
docker rmi image_id
```

---

## Container Commands

### List Running Containers

```bash
docker ps
```

### List All Containers

```bash
docker ps -a
```

### Run a Container

```bash
docker run nginx
```

### Run Container in Detached Mode

```bash
docker run -d nginx
```

### Run with Port Mapping

```bash
docker run -p 8080:80 nginx
```

### Stop a Container

```bash
docker stop container_id
```

### Start a Container

```bash
docker start container_id
```

### Restart a Container

```bash
docker restart container_id
```

### Remove a Container

```bash
docker rm container_id
```

---

## Container Interaction

### Access Container Shell

```bash
docker exec -it container_id /bin/bash
```

### View Container Logs

```bash
docker logs container_id
```

### Inspect Container Details

```bash
docker inspect container_id
```

---

## Volume Commands

### List Volumes

```bash
docker volume ls
```

### Create a Volume

```bash
docker volume create my_volume
```

### Use a Volume

```bash
docker run -v my_volume:/data nginx
```

---

## Network Commands

### List Networks

```bash
docker network ls
```

### Create a Network

```bash
docker network create my_network
```

---

## Docker System Commands

### Disk Usage

```bash
docker system df
```

### Remove Unused Data

```bash
docker system prune
```

⚠️ **Warning:** This removes stopped containers, unused images, and networks.

---

## Docker Compose Commands

> Used for multi-container applications.

### Start Services

```bash
docker compose up
```

### Stop Services

```bash
docker compose down
```

### Build Services

```bash
docker compose build
```

---

## Helpful Shortcuts

| Command         | Purpose            |
| --------------- | ------------------ |
| `docker ps`     | Running containers |
| `docker images` | Local images       |
| `docker logs`   | Container output   |
| `docker exec`   | Enter container    |
| `docker prune`  | Cleanup            |

---

## Summary

Docker commands allow you to:

* Manage images and containers
* Control networking and storage
* Debug and inspect applications
* Automate deployments

Mastering these commands is essential for **Docker, DevOps, and cloud development**.

---

## Learn More

* [https://docs.docker.com/engine/reference/commandline/docker/](https://docs.docker.com/engine/reference/commandline/docker/)
