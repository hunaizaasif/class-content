# 🎓 **Class 08 — Claude Code & Spec-Kit Plus (28 Nov 2025)**

Today’s session explored **Claude Code** and took an overview of **Spec-Kit Plus**, a structured workflow for agent-driven development.
~~------------------------------~~

## 🔧 Installing Claude Code
We installed Claude Code using the [official guide](https://ai-native.panaversity.org/docs/AI-Tool-Landscape/claude-code-features-and-workflows/installation-and-authentication):
```bash
npm install -g @anthropic-ai/claude-code
```
If you don’t have a Claude subscription, you can set up the [**free Claude Code (via Gemini)**](https://ai-native.panaversity.org/docs/AI-Tool-Landscape/claude-code-features-and-workflows/free-claude-setup):
~~------------------------------~~

## 📦 Spec-Kit Plus Overview

Spec-Kit Plus provides a structured Spec-Driven Development workflow.

📕 [Learning resource](https://ai-native.panaversity.org/docs/SDD-RI-Fundamentals/spec-kit-plus-hands-on/spec-kit-plus-foundation)

Install Specify CLI:
```bash
pip install specifyplus
```
Create a project:
```bash
specifyplus init <PROJECT_NAME>
```
Select **Claude** as the coding agent.
~~------------------------------~~

## 🤖 Spec-Kit Plus Slash Commands

### 🧱 Core

* `/sp.constitution` — Set project principles
* `/sp.specify` — Define requirements
* `/sp.plan` — Generate tech plan
* `/sp.tasks` — Create task lists
* `/sp.implement` — Build features

### 🔍 Optional

* `/sp.clarify` — Improve requirements
* `/sp.analyze` — Consistency check
* `/sp.checklist` — Quality validation  
  ~~------------------------------~~

## 🏠 Homework Assignment

1️⃣ Install Claude Code (or connect free via Gemini)
2️⃣ Create a [**Docusaurus**](https://docusaurus.io/) project using SDD
3️⃣ Add **new chapter** with SDD commands
4️⃣ Build & push to GitHub using Claude Code
5️⃣ Deploy to **GitHub Pages** 🚀
