# 🎓 **Class 13 — Cloud Native, System Design & Docker (02 Feb 2026)**
Today's session explored **Cloud Native Architecture**, **System Design principles**, **Microservices vs Monolithic**, and hands-on **Docker fundamentals**.
~~------------------------------~~
## 🏗️ Architecture Fundamentals
We covered the traditional **3-Tier Architecture**:

**Presentation Tier (Client)** → **Logic Tier (Server)** → **Data Tier (Database)**

### Business Boundaries (E-commerce Example)
* **Add to Cart** — Shopping cart management
* **Checkout** — Order processing & validation
* **Shipment** — Delivery workflow

Each boundary represents a separate business capability that can be independently managed.
~~------------------------------~~
## 🧱 Monolithic vs Microservices Architecture
### Monolithic Architecture
All business logic lives in **one codebase**:
* Simple to develop initially
* **Drawbacks:** Slow team velocity, hard to scale, one bug affects everything

### Microservices Architecture
Each business logic is a **separate service**:
* Teams work independently
* Better scalability and resilience
* Each service can be deployed separately

**Key principle:** Services are **stateless**, orchestrators are **stateful**
~~------------------------------~~
## ⚖️ System Design Principles
### Scaling Strategies
* **Vertical Scaling** — Increase server power (RAM/CPU) - Limited & costly
* **Horizontal Scaling** — Add more servers with load balancer - Scalable & flexible

### Fault Tolerance vs Resilience
**These are NOT the same thing!**

**Fault Tolerance** — System keeps working **without showing failure to user**
* One server fails → Load balancer redirects to another server
* User never notices anything went wrong
* **Failure is masked** ✨

* **Resilience** — System **fails fast and recovers automatically**
* Services can auto-restart when they crash
* Uses **exponential backoff** retry strategy:
  * 1st retry: Wait 10 seconds
  * 2nd retry: Wait 20 seconds
  * 3rd retry: Wait 30 seconds
  * 4th retry: Wait 40 seconds
* **Circuit breaker** stops broken service chain (fail fast)
* **Failure is acknowledged and handled** 🔄

**📌 Critical:** Fault tolerance **without** resilience is dangerous! You need both working together.

### Circuit Breaker & Fallbacks
When a service (e.g., Checkout) fails repeatedly:

**Without Circuit Breaker:**
* Requests keep trying
* System waits and times out
* Entire microservice chain breaks
* Cascading failures occur

**With Circuit Breaker:**
* Circuit "opens" after max failures
* Stops sending requests to broken service
* Returns **fallback response** immediately:
  * "Checkout service temporarily unavailable"
  * User gets instant feedback instead of timeout
* Service can recover in background

**Question:** If circuit breaker falls and requests come to server, what happens?
* ❌ Timeout (bad UX)
* ✅ Fallback message (correct approach!)

### Consistency Models
* **Strong Consistency** — Real-time updates (e.g., Add to Cart - no delay acceptable)
* **Eventual Consistency** — Delay acceptable (e.g., Shipment tracking - 5-15 min delay OK)

**Trade-off:** Strongly consistent data = Locked data = Lower availability (client waits)
Eventual consistency = Higher availability (client doesn't wait)

### System Design Reality
**Architecture is never perfect** — It's a **tradeoff engine**:

* ⚖️ **Low cost** ↔ Higher maintenance
* ⚖️ **High scalability** ↔ Higher complexity  
* ⚖️ **Strong consistency** ↔ Reduced availability
* ⚖️ **Real-time updates** ↔ System performance

**Nothing is free.** Every decision has consequences. The question is: **How much downtime can your client bear?**

## 🎭 Orchestration Patterns
### Synchronous vs Asynchronous Communication
**Synchronous (Blocking)**
* Request → **wait** → response
* Caller must wait for response
* Like a **phone call** 📞
* Example: API calls between services

**Asynchronous (Non-blocking)**
* Fire event → **continue execution**
* Caller doesn't wait
* Like a **WhatsApp message** 💬
* Example: Event-driven architecture

### Orchestrator Architecture (Synchronous)
* Central controller manages workflow
* **Upstream server** — Initiates request & waits for response
* **Downstream server** — Receives request & returns response
* Direct service-to-service communication
* Like a **phone call** — immediate response expected

### Choreography Architecture (Asynchronous)
* **Event Broker** replaces orchestrator
* Services communicate via **topics**:
  * Checkout topic
  * Shipment topic
* **Producer** — Sends messages to topics
* **Consumer** — Receives messages from topics
* No direct dependency between services
* Like **WhatsApp messages** — no immediate response needed

### Commands vs Queries
* **Queries** — Read-only operations (Get cart items, order status)
* **Commands** — Write operations (Add to cart, place order)

**Read/Write Separation:**
* Read → Queries
* Write → Commands
~~------------------------------~~
## 🔄 Transactions & Rollback
**Transaction** — Group of steps executed together (all or nothing)

**Rollback** — If any step fails → revert everything

Example workflow:
1. Add to cart ✅
2. Checkout ✅
3. Payment ❌ **FAILS**
4. **Rollback:** Order cancelled → Cart restored

**Success only when all steps pass** ✅

**Transaction rollback** ensures data integrity across microservices.
## 🐳 Docker Fundamentals
Docker creates **containers** — lightweight isolated environments.

### Essential Commands
```bash
# Run a container
docker run hello-world

# Run with custom name
docker run --name myhelloworld hello-world

# List all containers
docker ps -a

# Stop/Start containers
docker stop test
docker start test

# Clean up unused images
docker image prune

# Run specific version
docker run python:latest
```

### Key Concepts
* **Docker Image** — Blueprint/template
* **Container** — Running instance of an image
* **Docker Hub** — Public image repository
* **Tag** — Version identifier (e.g., `latest`, `3.9`, `alpine`)

### Why Docker?
**Requirements to run code:**
1. Hardware (CPU/GPU, RAM, Network, Storage)
2. Operating System
3. Dependencies/Tools
4. Codebase

**Docker packages all of this into one container!** 📦

## 🏠 Homework Assignment
1️⃣ Study Docker commands: [Hands-on Command Journey](https://github.com/Ameen-Alam/CNC-Docker/blob/master/hands-on-command-journey.md)
2️⃣ **Containerize FastAPI Project** using Docker
3️⃣ Clone: [FastAPI OpenAI Agents SDK](https://github.com/Hamzah-syed/fastapi-openai-agents-sdk)
4️⃣ Create `Dockerfile` and build the image
5️⃣ Run the containerized application locally 🚀
