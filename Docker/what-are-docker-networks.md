# What Are `Docker Networks`?

**Docker networks** enable communication between Docker containers, the host machine, and external systems.  
They provide isolation, service discovery, and secure networking for containerized applications.

---

## Why Docker Networks Are Needed

By default, containers are isolated.  
Docker networks allow containers to:
- Communicate with each other
- Expose services to the host
- Connect securely to external networks

---

## Key Concepts

- Each container can be attached to one or more networks
- Containers communicate using **IP addresses or service names**
- Docker manages DNS and routing automatically

---

## Types of Docker Networks

### 1. Bridge Network (Default)

- Used by containers on a single host
- Containers can communicate by name
- Most common for local development

```bash
docker network create my-bridge
````

---

### 2. Host Network

* Container shares the host’s network stack
* No port mapping required
* Less isolation

```bash
docker run --network host nginx
```

---

### 3. None Network

* Completely isolated
* No network access

```bash
docker run --network none alpine
```

---

### 4. Overlay Network

* Used in Docker Swarm
* Enables multi-host container communication
* Required for distributed applications

---

### 5. Macvlan Network

* Assigns a MAC address to containers
* Appears as physical devices on the network
* Used for legacy apps

---

## Default Docker Networks

Run:

```bash
docker network ls
```

You’ll typically see:

* `bridge`
* `host`
* `none`

---

## Container Communication Example

```bash
docker network create app-network

docker run -d --name api --network app-network node-app
docker run -d --name web --network app-network nginx
```

Containers can communicate using:

```text
http://api:3000
```

---

## Docker Networks with Docker Compose

```yaml
services:
  backend:
    build: .
    networks:
      - app-net

  frontend:
    image: nginx
    networks:
      - app-net

networks:
  app-net:
```

Docker Compose automatically:

* Creates the network
* Enables DNS-based service discovery

---

## Exposing Services with Networks

* Use **port binding** to expose to host
* Use **internal networks** to restrict access

```yaml
networks:
  internal-net:
    internal: true
```

---

## Inspecting Docker Networks

```bash
docker network inspect bridge
```

---

## Network Best Practices

* Use custom bridge networks instead of default
* Avoid `host` network in production
* Separate frontend and backend networks
* Limit exposed ports
* Use internal networks for databases

---

## Docker Networks vs Kubernetes Networking

| Feature    | Docker Networks      | Kubernetes |
| ---------- | -------------------- | ---------- |
| Scope      | Single host (mostly) | Multi-node |
| DNS        | Built-in             | Built-in   |
| Complexity | Simple               | Advanced   |

---

## Summary

* Docker networks connect containers securely
* Multiple network types for different use cases
* Docker handles routing and DNS automatically
* Essential for microservices and multi-container apps

---

## Learn More

* [https://docs.docker.com/network/](https://docs.docker.com/network/)
