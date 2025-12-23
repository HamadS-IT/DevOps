# What Are `Docker Image Layers` and `Layers in Docker`?

Docker uses a **layered filesystem** to build images and run containers efficiently.  
Each layer represents a **change to the filesystem**, allowing Docker to reuse, cache, and share layers across images.

---

## What Are Docker Image Layers?

A **Docker image layer** is an immutable (read-only) filesystem snapshot created from:
- Each instruction in a `Dockerfile`
- Each change to the image filesystem

Example Dockerfile:
```dockerfile
FROM node:18
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
````

Each line creates a **new image layer**.

---

## How Docker Layers Work

* Layers are stacked on top of each other
* Each layer depends on the layer below it
* Docker caches layers to speed up builds
* Identical layers are shared between images

> If a layer doesn’t change, Docker reuses it instead of rebuilding it.

---

## Read-Only Image Layers

* Image layers are **read-only**
* They cannot be modified once built
* Multiple containers can share the same image layers

This makes Docker images:

* Space-efficient
* Fast to distribute
* Easy to version

---

## What Is the Container Layer?

When a container starts, Docker adds a **writable container layer** on top of the image layers.

* All file changes go to this layer
* Image layers remain unchanged
* Deleted files are hidden, not removed

Once the container is removed, the container layer is destroyed.

---

## Union File System (UnionFS)

Docker uses UnionFS technologies like:

* OverlayFS
* AUFS
* Btrfs

These allow Docker to:

* Combine multiple layers into one view
* Copy files only when modified (**copy-on-write**)

---

## Copy-on-Write Explained

When a container modifies a file:

1. Docker copies the file from the read-only layer
2. The copy is placed in the container layer
3. Changes apply only to that container

This improves performance and reduces disk usage.

---

## Why Layers Matter

### Faster Builds

* Docker caches layers
* Only changed layers are rebuilt

### Smaller Images

* Shared layers reduce duplication

### Efficient Storage

* One layer can be used by many images

### Version Control

* Each image version is a set of layers

---

## Best Practices for Layer Optimization

### Combine Commands

```dockerfile
RUN apt-get update && apt-get install -y curl
```

### Order Instructions Wisely

* Put rarely changing commands first
* Copy dependencies before source code

### Use `.dockerignore`

Exclude unnecessary files to reduce layer size.

---

## View Image Layers

### Show Image History

```bash
docker history image_name
```

### Inspect Image

```bash
docker inspect image_name
```

---

## Image Layers vs Container Layer

| Feature    | Image Layer | Container Layer |
| ---------- | ----------- | --------------- |
| Writable   | ❌ No        | ✅ Yes           |
| Shared     | ✅ Yes       | ❌ No            |
| Persistent | ✅ Yes       | ❌ No            |
| Created at | Build time  | Run time        |

---

## Summary

* Docker images are built from **immutable layers**
* Containers add a **writable layer** on top
* Layers enable caching, speed, and efficiency
* Understanding layers helps you build **smaller, faster Docker images**

---

## Learn More

* [https://docs.docker.com/storage/storagedriver/](https://docs.docker.com/storage/storagedriver/)
* [https://docs.docker.com/develop/develop-images/dockerfile_best-practices/](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

