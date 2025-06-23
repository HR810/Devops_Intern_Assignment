# 🔀 Nginx Reverse Proxy with Go and Python Microservices

This project demonstrates how to use **Docker Compose** to set up a simple **reverse proxy architecture** using **Nginx**, with two backend microservices:

* 🟦 **Service 1**: A Go-based web service
* 🟨 **Service 2**: A Python (Flask)-based web service

Nginx handles routing between these services using clean URLs.

---

## 🚀 Setup Instructions

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Build and run all services**:

   ```bash
   docker-compose up --build
   ```

3. **Access the services via Nginx (reverse proxy)**:

   * [http://localhost:8080/service1/hello](http://localhost:8080/service1/hello)
   * [http://localhost:8080/service2/hello](http://localhost:8080/service2/hello)

---

## 🛣️ How Routing Works

Nginx listens on port **80** (exposed as **8080**) and proxies requests to:

| URL Path     | Proxied To              |
| ------------ | ----------------------- |
| `/service1/` | `http://service1:8001/` |
| `/service2/` | `http://service2:8002/` |

> These upstream names (`service1`, `service2`) match the container names in `docker-compose.yml`.

---

## 💡 Bonus Features Implemented

* ✅ **Clean Logging**:

  * `log.Println()` in Go
  * Flask's built-in logging for requests
* ✅ **Health Checks**:

  * Docker Compose health checks on `/ping` route of both services
  * Nginx only starts after services are healthy (`depends_on.condition`)
* ✅ **Modular Docker Setup**:

  * Separate `Dockerfile` for each service and for Nginx
* ✅ **Structured and simple response**:

  * JSON output on both `/ping` and `/hello` routes

---

## 📂 Project Structure

```
.
├── docker-compose.yml
├── service_1/              # Go service
│   ├── Dockerfile
│   └── main.go
├── service_2/              # Python service
│   ├── Dockerfile
│   └── app.py
├── nginx/
│   ├── Dockerfile
│   └── default.conf
└── README.md
```

---

## 🧪 Example Endpoints

* **Service 1:**

  * `GET /service1/ping` → `{ "status": "ok", "service": "1" }`
  * `GET /service1/hello` → `{ "message": "Hello from Service 1" }`
* **Service 2:**

  * `GET /service2/ping` → `{ "status": "ok", "service": "2" }`
  * `GET /service2/hello` → `{ "message": "Hello from Service 2" }`

---

## 🏁 To Stop

```bash
docker-compose down
```

---

