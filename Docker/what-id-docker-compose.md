# What Is `Docker Compose`?

**Docker Compose** is a tool used to **define and run multi-container Docker applications** using a single configuration file called `docker-compose.yml`.

Instead of running multiple `docker run` commands, Docker Compose lets you manage everything with **one command**.

---

## Why Docker Compose Is Used

Modern applications often require multiple services, such as:
- Web server
- Backend API
- Database
- Cache (Redis)

Docker Compose helps you:
- Run all services together
- Manage networking automatically
- Share environment variables
- Simplify development and testing

---

## Key Concept

> **One application = multiple containers = one configuration file**

---

## How Docker Compose Works

1. You define services in `docker-compose.yml`
2. Each service uses an image or Dockerfile
3. Docker Compose creates:
   - Containers
   - Networks
   - Volumes
4. All services start together with one command

---

## Basic `docker-compose.yml` Example

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"

  api:
    build: .
    ports:
      - "3000:3000"
````

Run with:

```bash
docker compose up
```

---

## Main Components of Docker Compose

### Services

Containers that make up your application.

```yaml
services:
  app:
    build: .
```

---

### Networks

Allows containers to communicate by service name.

```yaml
networks:
  app-network:
```

---

### Volumes

Persistent storage for containers.

```yaml
volumes:
  db-data:
```

---

## Common Docker Compose Commands

### Start Services

```bash
docker compose up
```

### Start in Detached Mode

```bash
docker compose up -d
```

### Stop Services

```bash
docker compose down
```

### Rebuild Images

```bash
docker compose build
```

### View Logs

```bash
docker compose logs
```

### List Running Services

```bash
docker compose ps
```

---

## Example: App + Database

```yaml
services:
  backend:
    build: .
    ports:
      - "3000:3000"

  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: secret
```

* Containers can talk using `db` as hostname
* No manual networking required

---

## Docker Compose vs Docker CLI

| Feature              | Docker CLI | Docker Compose |
| -------------------- | ---------- | -------------- |
| Single container     | ✅ Yes      | ✅ Yes          |
| Multi-container apps | ❌ Hard     | ✅ Easy         |
| One-command startup  | ❌ No       | ✅ Yes          |
| Service networking   | ❌ Manual   | ✅ Automatic    |

---

## When to Use Docker Compose

✅ Local development
✅ Testing environments
✅ Microservices
✅ CI pipelines

❌ Large-scale orchestration (use Kubernetes instead)

---

## Best Practices

* Keep one service per container
* Use environment variables
* Name services clearly
* Use `.env` files for secrets
* Avoid hardcoding credentials

---

## Summary

* Docker Compose manages **multi-container applications**
* Uses `docker-compose.yml`
* Simplifies development and testing
* Ideal for local and small-to-medium projects

---

## Learn More

* [https://docs.docker.com/compose/](https://docs.docker.com/compose/)

