@everyone
# 🎓 **Class 11 — Reusable AI & Databases (19 Dec 2025)**
Today’s session focused on **Reusable AI concepts**, and strengthening our **database fundamentals**.
~~------------------------------~~

## 🤖 Reusable AI
Reusable AI means building AI logic once and using it across multiple projects, workflows, or tasks.

* Reduces repeated prompts and logic
* Makes AI behavior consistent
* Saves time and improves reliability
* Core idea behind agents, subagents, and skills
~~------------------------------~~

## 🧠 Subagents & Skills (Claude Code)
Claude Code supports modular AI workflows.

### ⭐ Subagents
* Specialized AI units for specific tasks
* Can be orchestrated together
* Each subagent has a clear responsibility

### ⭐ Skills
* Reusable AI capabilities
* Encapsulate logic like validation, formatting, analysis
* Can be reused across subagents and projects

📕 Subagents & Orchestration: [Panaversity Official Book](https://ai-native.panaversity.org/docs/AI-Tool-Landscape/claude-code-features-and-workflows/subagents-and-orchestration), [Claude Code Docs](https://code.claude.com/docs/en/sub-agents)
📕 Agent Skills: [Panaversity Official Book](https://ai-native.panaversity.org/docs/AI-Tool-Landscape/claude-code-features-and-workflows/agent-skills), [Claude Code Docs](https://code.claude.com/docs/en/skills)
~~------------------------------~~

## 🗄️ PostgreSQL
PostgreSQL is a powerful, open-source relational database.

* Production-ready and highly reliable
* Supports large-scale data
* Strong typing and constraints
* Used widely in real-world systems

📕 [PostgreSQL Documentation](https://www.postgresql.org/docs/)
~~------------------------------~~

## ☁️ Neon DB
Neon provides cloud PostgreSQL with modern features.

* Fully managed PostgreSQL
* Free tier available
* Serverless & scalable
* Perfect for FastAPI projects

📕 [Neon DB Python Docs](https://neon.com/docs/guides/python)
~~------------------------------~~

## 📦 SQLModel
SQLModel connects validation and database logic.

* Combines Pydantic + SQLAlchemy
* One model = validation + table
* Cleaner and beginner-friendly
* Database tye conversion: string to varchar

📕 [Documentation](https://sqlmodel.tiangolo.com/)
~~------------------------------~~

## 📝 SQLite
SQLite is a lightweight local database.

* Stored as a single file
* Easy setup, no server needed
* Ideal for small apps and testing

### ⚠️ Cons
* Not ideal for high traffic
* Limited concurrency
* Not suitable for large production systems
📕 [SQLite GitHub Repository](https://github.com/sqlite/sqlite)
~~------------------------------~~

## 🔁 SQLite → Neon DB
Migration is simple.

* Only database URL changes
* Environment variable updated
* Restart FastAPI server
* App works the same, now on cloud DB

📕 Full Tutorial Document: [FastAPI Tutorial From Zero to Database](https://www.notion.so/FastAPI-Tutorial-From-Zero-to-Database-2c7da4c66411806c86f1dd8aafe23e38)
