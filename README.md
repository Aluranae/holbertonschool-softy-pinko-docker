# Softy Pinko - Docker & Microservices Project

## 🧾 Project Overview

This project is a step-by-step introduction to **Docker**, **multi-container architecture**, and **proxy/load balancing** concepts. The main goal is to containerize a static front-end website (Softy Pinko template), connect it with a simple API backend, and progressively evolve the architecture using **Docker Compose**, **Nginx**, and **Flask**.

By the end of this project, the application consists of three main services: a **front-end static server**, a **back-end API server**, and a **reverse proxy server**, with optional horizontal scaling for the back-end.

---

## 🎯 Learning Objectives

- Understand the basics of Docker and how to build images
- Learn how to run containers with specific ports and context
- Use Nginx as a static file server and as a reverse proxy
- Connect containers together using Docker networks and service names
- Handle CORS between front-end and back-end services
- Use Docker Compose to orchestrate multi-container applications
- Scale services horizontally and load-balance with Nginx

---

## 📌 Tasks Breakdown

### ✅ Task 0. Static Server
- Serve the static **Softy Pinko** website using **Nginx**.
- Dockerize the front-end and expose it on port `9000`.

### ✅ Task 1. API Server
- Create a simple **Flask API** returning `"Hello, World!"` on `/api/hello`.
- Dockerize the back-end and expose it on port `5252`.

### ✅ Task 2. Compose
- Create a `docker-compose.yml` file to launch both front-end and back-end services together.
- Use Docker Compose to simplify orchestration.

### ✅ Task 3. Connecting the Front-end and Back-end
- Add a dynamic content block (`<h1 id="dynamic-content">`) to `index.html`.
- Use jQuery and AJAX to fetch data from `/api/hello`.
- Add **CORS support** using `flask-cors` in the API.

### ✅ Task 4. Proxy Server
- Add a third service: **proxy** using Nginx.
- Proxy `/` to the front-end and `/api` to the back-end.
- Update the JS to make AJAX call to `/api/hello` (through proxy).
- Only expose port `80` externally.

### ✅ Task 5. docker-compose.yml Proxy Integration
- Update `docker-compose.yml` to include the proxy service.
- Remove port exposure for front-end and back-end (internal only).
- Add routing logic to `proxy.conf` to support Nginx proxying.

### ✅ Task 6. Scale Horizontally
- Use `--scale back-end=2` with Docker Compose to spawn **two API containers**.
- Load-balance requests using Nginx round-robin algorithm.
- Observe API calls alternate between both back-end instances.

---

## 🚀 Run the Project

To launch all services:

```bash
docker-compose up --build
```

To run with multiple API servers (Task 6):

```bash
docker-compose up --scale back-end=2 --build
```

To stop and clean up:

```bash
docker-compose down
```

---

## 👨‍💻 Author

This project is part of the Holberton School curriculum and was completed by **Ben**.

---

## 📁 Directory Structure

```
Task6/
├── back-end/
│   ├── Dockerfile
│   └── api.py
├── front-end/
│   ├── Dockerfile
│   ├── softy-pinko-front-end/
│   └── softy-pinko-front-end.conf
├── proxy/
│   ├── Dockerfile
│   └── proxy.conf
├── docker-compose.yml
└── 2-api-servers.txt
```

---
