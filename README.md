# 🎓 **Class 19 — Model Context Protocol (MCP) & Agent Orchestration (13 Feb 2026)**

Today's session focused on **MCP Server Development**, **JSON-RPC Protocol**, and **advanced agent orchestration concepts**.

~~------------------------------~~

## 🏗️ Monorepo vs Microservices Architecture

Understanding different software architecture patterns for scalable applications.

### 📦 Monorepo

* Single repository containing multiple projects
* Shared dependencies and tooling
* Easier code sharing and refactoring
* Examples: Google, Meta use monorepos

### 🏛️ Monolith

* All business logic in single backend server
* Frontend is separate
* Simple deployment, harder to scale
* Good for small to medium apps

### 🧩 Microservices

* Each strong business boundary = separate service
* Independent deployment and scaling
* Loose coupling, high cohesion
* Complex orchestration, better fault isolation

~~------------------------------~~

## 🔌 Model Context Protocol (MCP)

MCP is the **USB-C of AI applications** — one protocol connecting any AI host to any external service.

### 💡 Why MCP?

* **Solves integration explosion**: Write once, use everywhere
* Built for AI agents, not traditional APIs
* Connect to databases, file systems, trackers, knowledge bases
* Works with Claude, ChatGPT, Cursor, VS Code, custom agents

### 🆚 MCP Server vs MCP Client

* **MCP Server**: Provides tools/resources to AI agents
* **MCP Client**: AI application consuming MCP services
* **Monitoring**: Track usage, save logs (e.g., Logfire)
* **Security**: OAuth2 verification for access control
* **Monetization**: Can be sold or kept internal

📕 **Panaversity MCP Guide**
[https://github.com/panaversity/learn-agentic-ai/tree/main/03_ai_protocols/01_mcp](https://github.com/panaversity/learn-agentic-ai/tree/main/03_ai_protocols/01_mcp)

📕 **Agent Factory: MCP Fundamentals**
[https://agentfactory.panaversity.org/docs/Building-Custom-Agents/mcp-fundamentals](https://agentfactory.panaversity.org/docs/Building-Custom-Agents/mcp-fundamentals)

📕 **Agent Factory: Advanced MCP Development**
[https://agentfactory.panaversity.org/docs/Building-Custom-Agents/custom-mcp-servers](https://agentfactory.panaversity.org/docs/Building-Custom-Agents/custom-mcp-servers)

~~------------------------------~~

## 📡 JSON-RPC 2.0 Protocol

JSON-RPC is a lightweight protocol for remote procedure calls — the foundation of MCP.

### ⭐ Key Features

* **Bi-directional communication** support
* **Single directional communication** support
* Stateless but enables stateful workflows via session IDs
* Standard error handling with codes

### 🔑 Core Concepts

**Request Object**

```json
{"jsonrpc": "2.0", "method": "tools/call", "params": {...}, "id": 1}
```

* `id`: Server responds only if present (without id = handshake)
* `method`: Function name to invoke
* `params`: Array or Object with parameters

**Notification**
Request without `id` — server won't respond

**Response Object**
Contains `result` OR `error`, plus matching `id`

### 🚀 Why JSON-RPC for MCP (not REST)?

* **Procedural operations** beyond CRUD
* **Multiplexing**: Multiple calls on single connection
* **Streaming & notifications** built-in
* **Explicit method names**: `{"method": "tools/call"}` vs REST endpoints
* **Stateful workflows** via session/context IDs
* **Standard error handling**: Structured error responses
* **Ecosystem alignment**: Used by LSP, Debug Adapter Protocol

📕 **JSON-RPC Detailed Guide**
[https://github.com/panaversity/learn-agentic-ai/blob/main/03_ai_protocols/01_mcp/03_json_rpc/readme.md](https://github.com/panaversity/learn-agentic-ai/blob/main/03_ai_protocols/01_mcp/03_json_rpc/readme.md)

📕 **JSON-RPC Playground**
[https://jsonrpc-playground.onrender.com/](https://jsonrpc-playground.onrender.com/)

~~------------------------------~~

## 🛠️ Building Your First MCP Server

### 📋 Step-by-Step Implementation

**Step 1:** Initialize project

```
uv init .
```

**Step 2:** Install MCP package

```
uv add "mcp[cli]"
```

**Step 3:** Create MCP server in `main.py` file

```python
from mcp.server.fastmcp import FastMCP

# Initialize FastMCP server
mcp = FastMCP(
    name="hello-server",
    stateless_http=True
)

mcp_app = mcp.streamable_http_app()
```

**Step 4:** Add Greeting tool

```python
@mcp.tool()
def hello(name: str) -> str:
    return f"Hello, {name}"
```

**Step 5:** Add another tool for weather

```python
@mcp.tool()
def get_weather(city: str) -> str:
    return f"The weather in {city} is sunny."
```

**Step 6:** Start the server

```
uv run uvicorn main:mcp_app --reload
```

**Step 7:** Test it on developer tool (Optional)

```bash
mcp dev main.py
# OR
npx -y @modelcontextprotocol/inspector
```

### ☁️ Deploy to Hugging Face

**CI/CD Deployment Guide**
[https://spiffy-palladium-3c4.notion.site/Deployment-2ffda4c66411802d9548c398a1fa133e?pvs=74](https://spiffy-palladium-3c4.notion.site/Deployment-2ffda4c66411802d9548c398a1fa133e?pvs=74)

⚠️ **Important Change:**
Dockerfile run command change from:

```
main:app
```

to

```
main:mcp_app
```

📕 **Hello MCP Server Example**
[https://github.com/panaversity/learn-agentic-ai/tree/main/03_ai_protocols/01_mcp/04_fundamental_%20primitives/01_hello_mcp_server/hello-mcp](https://github.com/panaversity/learn-agentic-ai/tree/main/03_ai_protocols/01_mcp/04_fundamental_%20primitives/01_hello_mcp_server/hello-mcp)

~~------------------------------~~

## 🔧 Dependency Injection in FastAPI

### 💡 What is Dependency Injection?

* Provide dependencies to functions from outside
* Avoid hardcoding, improve testability
* Reuse database connections, auth logic, configs
* FastAPI has built-in DI system with `Depends()`

📕 **Dependency Injection Guide**
[https://agentfactory.panaversity.org/docs/Building-Custom-Agents/fastapi-for-agents/dependency-injection](https://agentfactory.panaversity.org/docs/Building-Custom-Agents/fastapi-for-agents/dependency-injection)

~~------------------------------~~

## 📚 Homework

* Search **GitOps** for more CI/CD tools
* Deep dive: **What is Dependency Injection?**
* Build your own MCP server with at least **3 custom tools**
* Deploy your MCP server to **Hugging Face** and share the link
* Research **stateless vs stateful** in context of MCP servers

---

