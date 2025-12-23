# How to `Dockerize` an `Express Server`?

Dockerizing an Express server means packaging your Node.js application, its dependencies, and configuration into a Docker image so it can run consistently anywhere.

---

## Prerequisites

- Node.js installed
- Docker installed
- Basic knowledge of Express

---

## Sample Express Server

### Project Structure
```text
express-app/
├── Dockerfile
├── package.json
├── package-lock.json
└── server.js
````

### `server.js`

```js
const express = require("express");
const app = express();

const PORT = process.env.PORT || 3000;

app.get("/", (req, res) => {
  res.send("Hello from Dockerized Express!");
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

---

## Step 1: Create `package.json`

```json
{
  "name": "dockerized-express",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.19.2"
  }
}
```

---

## Step 2: Create a Dockerfile

```dockerfile
# Use official Node.js image
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy application source
COPY . .

# Expose the app port
EXPOSE 3000

# Start the application
CMD ["npm", "start"] # should always be the last command
```

---

## Step 3: Create `.dockerignore`

```dockerignore
node_modules
npm-debug.log
.env
```

This reduces image size and speeds up builds.

---

## Step 4: Build the Docker Image

```bash
docker build -t express-app .
```

---

## Step 5: Run the Docker Container

```bash
docker run -p 3000:3000 express-app
```

Visit:

```
http://localhost:3000
```

---

## Step 6: Run in Detached Mode (Optional)

```bash
docker run -d -p 3000:3000 --name express-container express-app
```

---

## Environment Variables (Recommended)

```bash
docker run -p 3000:3000 -e PORT=3000 express-app
```

Or using a `.env` file:

```bash
docker run --env-file .env -p 3000:3000 express-app
```

---

## Docker Compose (Optional)

For easier management:

### `docker-compose.yml`

```yaml
services:
  api:
    build: .
    ports:
      - "3000:3000"
    environment:
      - PORT=3000
```

Run:

```bash
docker compose up
```

---

## Common Mistakes

* ❌ App listens on `localhost` instead of `0.0.0.0`
* ❌ Forgetting to expose or bind ports
* ❌ Copying `node_modules` into the image
* ❌ Large images due to missing `.dockerignore`

---

## Best Practices

* Use `node:alpine` for smaller images
* Cache dependencies by copying `package.json` first
* Use environment variables for config
* Consider multi-stage builds for production

---

## Summary

* Create an Express app
* Write a Dockerfile
* Build the image
* Run the container
* Access the app via port binding

Dockerizing Express makes your app **portable, scalable, and production-ready**.

---

## Learn More

* [https://docs.docker.com/language/nodejs/](https://docs.docker.com/language/nodejs/)
* [https://expressjs.com/](https://expressjs.com/)

