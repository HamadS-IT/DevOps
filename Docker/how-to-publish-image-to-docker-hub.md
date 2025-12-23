# How to `Publish` an `Image` to `Docker Hub`?

Publishing an image to **Docker Hub** allows you to share your Docker images publicly or privately so others (or servers) can pull and run them.

---

## Prerequisites

- Docker installed
- Docker Hub account (https://hub.docker.com)
- A Docker image built locally
- Logged in via Docker CLI

---

## Step 1: Create a Docker Hub Account

1. Go to https://hub.docker.com
2. Sign up or log in
3. Note your **Docker Hub username**

Example:
```

username: hamaddev

````

---

## Step 2: Log In to Docker Hub from CLI

```bash
docker login
````

Enter:

* Docker Hub username
* Password or access token

Verify login:

```bash
docker info
```

---

## Step 3: Build Your Docker Image

```bash
docker build -t my-app .
```

Check the image:

```bash
docker images
```

---

## Step 4: Tag the Image Correctly

Docker Hub requires this format:

```text
username/repository:tag
```

Example:

```bash
docker tag my-app hamaddev/my-app:1.0
```

Or directly while building:

```bash
docker build -t hamaddev/my-app:1.0 .
```

---

## Step 5: Push the Image to Docker Hub

```bash
docker push hamaddev/my-app:1.0
```

If successful, you’ll see upload progress for each layer.

---

## Step 6: Verify on Docker Hub

1. Go to [https://hub.docker.com](https://hub.docker.com)
2. Open your repository
3. Confirm the image and tag are visible

---

## Step 7: Pull the Image Anywhere

```bash
docker pull hamaddev/my-app:1.0
```

Run it:

```bash
docker run -p 3000:3000 hamaddev/my-app:1.0
```

---

## Image Tags Best Practices

Common tags:

* `latest`
* `1.0`
* `1.0.1`
* `dev`
* `prod`

Example:

```bash
docker tag my-app hamaddev/my-app:latest
docker push hamaddev/my-app:latest
```

---

## Make Image Private (Optional)

1. Go to your repository on Docker Hub
2. Settings → Visibility
3. Set to **Private**

⚠️ Free accounts have limited private repositories.

---

## Common Errors & Fixes

### ❌ `denied: requested access to the resource is denied`

* Ensure you're logged in
* Check image name format
* Verify repository ownership

### ❌ `repository does not exist`

* Docker Hub creates repos automatically on first push
* Ensure username is correct

---

## Security Tips

* Never push secrets or `.env` files
* Use `.dockerignore`
* Use Docker Hub access tokens instead of passwords
* Scan images for vulnerabilities

---

## Summary

* Build your Docker image
* Tag it using `username/image:tag`
* Log in to Docker Hub
* Push the image
* Pull and run it anywhere

Publishing images makes your app **shareable, portable, and deployment-ready**.

---

## Learn More

* [https://docs.docker.com/docker-hub/](https://docs.docker.com/docker-hub/)
* [https://hub.docker.com](https://hub.docker.com)

