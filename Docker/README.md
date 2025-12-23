# What Is Docker?

Docker is an open-source platform that allows developers to **build, package, and run applications in containers**. Containers bundle an application with everything it needs to run—code, runtime, libraries, and system tools—so it works consistently across different environments.

---

## Why Docker Exists

Before Docker, applications often worked on one machine but failed on another due to:
- Different operating systems
- Missing dependencies
- Conflicting library versions

Docker solves this by making applications **portable and predictable**.

---

## What Is a Container?

A **container** is a lightweight, isolated environment that runs an application.

- Shares the host OS kernel
- Starts in seconds
- Uses fewer resources than virtual machines
- Runs the same everywhere

> Think of a container as a standardized shipping container for software.

---

## Docker vs Virtual Machines

| Feature | Docker Container | Virtual Machine |
|------|-----------------|----------------|
| Startup time | Seconds | Minutes |
| Size | MBs | GBs |
| OS | Shares host OS | Full OS per VM |
| Performance | Near-native | Heavier |

---

## Key Docker Components

### Docker Image
A **read-only blueprint** for a container.  
Example: `nginx`, `node:18`, `python:3.12`

### Docker Container
A **running instance** of an image.

### Dockerfile
A text file with instructions to build an image.

Example:
```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
````

### Docker Engine

The core software that builds and runs containers.

### Docker Hub

A public registry for sharing Docker images.

---

## Common Use Cases

* Local development environments
* Microservices architectures
* CI/CD pipelines
* Cloud deployments
* Testing and sandboxing applications

---

## Benefits of Docker

* ✅ Consistent environments
* ✅ Faster deployments
* ✅ Lightweight and efficient
* ✅ Easy scaling
* ✅ Strong ecosystem and tooling

---

## When Not to Use Docker

Docker may not be ideal if:

* You need full OS virtualization
* You run GUI-heavy applications
* You require strict kernel-level isolation

---

## Summary

Docker makes it easy to:

* Package applications
* Run them anywhere
* Scale and deploy efficiently

It has become a **core tool in modern software development and DevOps**.


# Explaining:

- What Are `Docker` Commands?
- What Are `Docker Image Layers` and `Layers in Docker`?
- What Is `Port Binding` in `Docker`?
- How to `Dockerize` an `Express Server`?
- What Is `Docker Compose`?
- How to `Publish` an `Image` to `Docker Hub`?
- What Are `Docker Volumes`?