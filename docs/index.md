# 🚀 Welcome to **uxopian-ai**

**uxopian-ai** is a complete, standalone framework designed to accelerate and simplify the integration of powerful AI features into any enterprise application.

Built on a solid foundation of **Java 21 LTS** and **Spring 3.5**, it goes far beyond a simple library by providing a full suite of tools — from backend services to frontend components — to create sophisticated, reliable, and scalable AI solutions.

---

## ✨ The uxopian-ai Advantage: _More Than Just a Library_

While **uxopian-ai** uses the excellent **Langchain4j** library as its core for LLM interactions, it builds a complete enterprise-ready ecosystem around it. Here’s the added value:

✅ **Standalone Service, Not Just Code**
A pre-packaged, deployable service that saves you months of development and infrastructure setup.

✅ **Ready-to-Use UI Components**
Instantly integrate AI with web-components (IIFE compiled, scoped CSS), plus plug-and-play integration scripts.

✅ **Advanced Orchestration Engine**
The unique **Goal** system enables dynamic prompt selection based on context — no need to build this from scratch.

✅ **Complete Conversation Management**
Persistent conversations with cost tracking, response regeneration, and user feedback support.

✅ **Data-Driven Insights**
A comprehensive admin panel to monitor ROI, token usage, and adoption trends.

---

## 🔍 Key Features at a Glance

### ⚙️ Effortless & Scalable Integration

- **Standalone Service**: Deployable via Docker or as a Java 21 application.
- **Multi-Tenant Architecture**: Designed for internal deployments with clear logical separation and distinct tenant management.
- **Web-Component UI**: Lightweight, embeddable components for any web app.
- **Rich REST API**: Fully documented (Swagger) for seamless integration.

### 📊 Powerful Admin & Analytics

- **Granular Token Monitoring**: Visualize input and output token consumption globally, by specific users, or per conversation.
- **ROI & Efficiency Tracking**: specific metrics allow you to view the number of times a prompt is used and estimate the total time saved.
- **Usage Trends**: Analyze activity over time (requests per week), monitor LLM model distribution, and track the adoption of advanced features like multi-modal capabilities.

### 🧠 Intelligent Orchestration

- **Goal System**: Define context-aware workflows using filters and priorities.
  _Example: A "comparison" goal automatically picks a legal prompt for contracts, and a generic one for others._
- **Templating Engine**: Dynamic data injection, custom Java services, and conditional logic with Thymeleaf.
- **Template Helpers**: Add your own Java functions to enrich prompts.

### 🤖 Robust LLM Interaction

- **Broad Support**: Compatible with many LLM providers out-of-the-box.
- **Custom Connectors**: Add private or fine-tuned models easily.
- **Advanced Features**: Native support for **function calling**, multi-modal requests (text + image), and streaming/non-streaming responses.
- **MCP Server Client**: Acts as a client for Multi-Content Platform (MCP) servers.

### 💬 Complete Conversation Management

- **Persistent History**: Conversations and messages are stored with full context.
- **Feedback Loop**: Gather specific user feedback (Good/Bad/Neutral) on responses to improve prompt quality.
- **Rich UX**: Regenerate, copy, and manage conversation content easily.

---

## 👥 Who Is This For?

This documentation is tailored for **integrators and developers** looking to deploy, configure, and extend the **uxopian-ai** framework to deliver cutting-edge AI features faster.

---

## 🚀 Getting Started

Ready to dive in? Check out the [**Installation Guide**](/getting_started/installation_guide) to set up your first instance of **uxopian-ai**.
