@everyone

# 🎓 **Class 10 — FastAPI: Zero to Database (12 Dec 2025)**
Today we built a full **FastAPI project**, going from setup → CRUD → database.
~~------------------------------~~

## 🔧 Project Setup with `uv`
`uv` gives fast installs and clean environments.

### ⭐ Key Points
* `uv init` creates project structure
* `uv venv` adds virtual environment
* `uv add` manages all dependencies
* FastAPI dev server runs instantly
~~------------------------------~~

## ⚡ FastAPI Essentials
FastAPI builds APIs with automatic JSON, docs, and validation.

### ⭐ Key Points
* Endpoints return JSON without extra work
* Dynamic routes supported using path params
* Built-in error handling for missing values & wrong types
* Pydantic validation ensures clean, safe data
* Auto-generated docs at `/docs`
~~------------------------------~~

## 🧩 Student CRUD System
We created full CRUD, starting simple then upgrading.

### ⭐ Key Points
* In-memory list used for demo data
* Added list, detail, create, update, delete routes
* Useful for learning, but resets on restart
~~------------------------------~~

## 🗄️ SQLModel + Database
SQLModel merges **Pydantic** + **SQLAlchemy** in one model.

### ⭐ Key Points
* One class acts as model + database table
* Auto ID generation handled by SQLModel
* SQLite added for local persistent storage
* Tables auto-created at startup
* All CRUD switched from memory → database
~~------------------------------~~

## ☁️ Optional: Neon PostgreSQLUsed for cloud-based, production-friendly storage.

### ⭐ Key Points
* Only database URL changed
* `.env` holds connection string
* PostgreSQL driver installed
* Data now survives restarts + available anywhere

📕 Full Tutorial Document: [FastAPI Tutorial From Zero to Database](https://www.notion.so/FastAPI-Tutorial-From-Zero-to-Database-2c7da4c66411806c86f1dd8aafe23e38)
