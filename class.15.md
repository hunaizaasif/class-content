# 🎓 Class 15 — Docker: From Zero to Hero (16 Jan 2026)
Today's session covered Docker fundamentals through building a real Pizza Delivery API, exploring containerization concepts, and deploying to production.
~~------------------------------~~
## 🐳 **What is Docker?**
Docker solves the "works on my machine" problem by packaging your application with all its dependencies.

**Core Concepts:**
• **Dockerfile** — Instructions for building your image
• **Docker Image** — The blueprint/recipe (like a pizza recipe)
• **Container** — Running instances from the image (10 pizzas from same recipe)
• **Isolation** — Each container is independent (add cheese to one pizza, doesn't affect others)
~~------------------------------~~
## 💿 **Installing Docker**

**Mac:**
Download from https://www.docker.com/products/docker-desktop

**Windows:**
```bash
wsl --install
# Then download Docker Desktop
```

**Linux:**
```bash
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```

**Verify:**
```bash
docker --version
docker run hello-world
```
~~------------------------------~~
## 🍕 **Building the Pizza Delivery API**
**Install UV (Modern Python Package Manager):**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Create Project:**
```bash
uv init pizza-delivery-api
cd pizza-delivery-api
uv add fastapi uvicorn pydantic
```

**Create main.py** with FastAPI endpoints:
• `/health` — Health check
• `/orders` — Create & list orders
• `/menu` — Pizza menu
~~------------------------------~~
## 📦 **Your First Dockerfile**
Create `Dockerfile`:
```dockerfile
FROM python:3.12-alpine
WORKDIR /app

# Install UV
COPY --from=ghcr.io/astral-sh/uv:latest /uv /usr/local/bin/uv

# Copy dependencies
COPY pyproject.toml uv.lock ./
RUN uv sync --frozen --no-dev

# Copy app code
COPY main.py .

EXPOSE 8000
CMD ["uv", "run", "main.py"]
```

**Build & Run:**
```bash
docker build -t pizza-api:v1 .
docker run -p 8000:8000 pizza-api:v1
```


## 🎯 **Production-Ready Dockerfile**

**Multi-stage build for optimization:**
• Stage 1: Builder (install dependencies)
• Stage 2: Runtime (minimal image)

**Result:** 1.1GB → 115MB (90% reduction!)

**Key improvements:**
✅ Alpine Linux (smaller base image)
✅ Non-root user (security)
✅ Health checks (monitoring)
✅ Layer caching (faster builds)
~~------------------------------~~
## 🚀 **Docker Hub & Deployment**

**Login to Docker Hub:**
```bash
docker login
```

**Push to Registry:**
```bash
docker tag pizza-api:v1 YOUR_USERNAME/pizza-api:v1
docker push YOUR_USERNAME/pizza-api:v1
```

**Registry Types:**
• **Public** — Anyone can pull (free on Docker Hub)
• **Private** — Requires authentication (paid plans)

**Deploy to Cloud (AWS, Azure, DigitalOcean):**
```bash
ssh root@your-server
curl -fsSL https://get.docker.com | sh
docker run -d -p 80:8000 YOUR_USERNAME/pizza-api:v1
```

**For Next.js SSR apps:** Use containerization for consistent deployments across cloud providers!
~~------------------------------~~
## 🔍 **Essential Docker Commands**

**Images:**
```bash
docker images              # List images
docker build -t name .     # Build image
docker rmi image-name      # Remove image
```

**Containers:**
```bash
docker ps                  # Running containers
docker logs container      # View logs
docker exec -it container sh  # Enter shell
docker stop container      # Stop gracefully
```
~~------------------------------~~
## 🏠 **Homework Assignment**

1️⃣ Install Docker on your machine
2️⃣ Build the Pizza Delivery API with UV
3️⃣ Create a production Dockerfile (multi-stage)
4️⃣ Push image to Docker Hub (public registry)
5️⃣ Deploy container to a cloud server
6️⃣ **Bonus:** Create docker-compose.yml with PostgreSQL

📚 **Complete Guide:** https://spiffy-palladium-3c4.notion.site/THE-ULTIMATE-PIZZA-DELIVERY-API-Docker-From-ZERO-to-HERO
~~------------------------------~~
