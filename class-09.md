@everyone

# 🎓 **Class 09 — Qwen CLI & OpenAI ChatKit (05 Dec 2025)**

Today we set up the **Qwen model with Claude Code**, explored the **RAG system pipeline**, and took an overview of **OpenAI ChatKit**.
~~------------------------------~~

## 🔧 Installing Qwen

Install Qwen CLI:

```bash
npm install -g @qwen-code/qwen-code
```

Run & authenticate:

```bash
qwen
```

Set up **Qwen with Claude Code** using these guides:
- [PowerShell (Windows)](https://github.com/DanielHashmi/Q4_learning/blob/main/spec-driven-development/tutorials/How%20to%20Use%20Claude%20Code%20with%20Qwen%20models%20for%20Free%20on%20Windows.md)
- [WSL / Linux / macOS](https://github.com/DanielHashmi/Q4_learning/blob/main/spec-driven-development/tutorials/How%20to%20Use%20Claude%20Code%20with%20Qwen%20models%20for%20Free%20on%20Linux%20and%20macOS%20%28sh%20and%20bash%29.md)

~~------------------------------~~

## 🧠 RAG System Pipeline

* Documents are broken into **chunks**
* Chunks are sent to an **embedding model**
* Generated **vectors** are stored in a **vector database** (with text as metadata)

When the user asks a question:

* User prompt → converted into **vectors**
* **Similar vectors** are searched in the database
* Related **text is fetched from metadata**
* This context is added to the **agent prompt**
* Agent now answers with **higher accuracy**

~~------------------------------~~

## 🏠 Homework Assignment

Create an **agent using OpenAI Agents SDK**, integrate it into a **React/Next.js app using ChatKit**.
⚠️ Everything must be done using **Spec-Driven Development** — **no manual code**.

