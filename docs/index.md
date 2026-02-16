# Welcome to **uxopian-ai**

**uxopian-ai** is a complete, standalone framework designed to accelerate and simplify the integration of powerful AI features into any enterprise application.

Built on a solid foundation of **Java 21 LTS** and **Spring 3.5**, it goes far beyond a simple library by providing a full suite of tools — from backend services to frontend components — to create sophisticated, reliable, and scalable AI solutions.

---

## The uxopian-ai Advantage: _More Than Just a Library_

While **uxopian-ai** uses the excellent **Langchain4j** library as its core for LLM interactions, it builds a complete enterprise-ready ecosystem around it. Here's the added value:

- **Standalone Service, Not Just Code:** A pre-packaged, deployable service that saves you months of development and infrastructure setup.
- **Ready-to-Use UI Components:** Instantly integrate AI with web-components (IIFE compiled, scoped CSS), plus plug-and-play integration scripts.
- **Advanced Orchestration Engine:** The unique **Goal** system enables dynamic prompt selection based on context — no need to build this from scratch.
- **Complete Conversation Management:** Persistent conversations with cost tracking, response regeneration, and user feedback support.
- **Data-Driven Insights:** A comprehensive admin panel to monitor ROI, token usage, and adoption trends.

---

## Key Features at a Glance

### Effortless & Scalable Integration

- **Standalone Service**: Deployable via Docker or as a Java 21 application.
- **Multi-Tenant Architecture**: Designed for internal deployments with clear logical separation and distinct tenant management.
- **Web-Component UI**: Lightweight, embeddable components for any web app.
- **Rich REST API**: Fully documented (Swagger) for seamless integration.

### Powerful Admin & Analytics

- **Granular Token Monitoring**: Visualize input and output token consumption globally, by specific users, or per conversation.
- **ROI & Efficiency Tracking**: Specific metrics allow you to view the number of times a prompt is used and estimate the total time saved.
- **Usage Trends**: Analyze activity over time (requests per week), monitor LLM model distribution, and track the adoption of advanced features like multi-modal capabilities.

### Intelligent Orchestration

- **Goal System**: Define context-aware workflows using filters and priorities.
  _Example: A "comparison" goal automatically picks a legal prompt for contracts, and a generic one for others._
- **Templating Engine**: Dynamic data injection, custom Java services, and conditional logic with Thymeleaf.
- **Template Helpers**: Add your own Java functions to enrich prompts.

### Robust LLM Interaction

- **Broad Support**: Compatible with many LLM providers out-of-the-box.
- **Custom Connectors**: Add private or fine-tuned models easily.
- **Advanced Features**: Native support for **function calling**, multi-modal requests (text + image), and streaming/non-streaming responses.
- **MCP Server Client**: Acts as a client for Model Context Protocol (MCP) servers.

### Complete Conversation Management

- **Persistent History**: Conversations and messages are stored with full context.
- **Feedback Loop**: Gather specific user feedback (Good/Bad/Neutral) on responses to improve prompt quality.
- **Rich UX**: Regenerate, copy, and manage conversation content easily.

---

## Reading Paths

Choose the path that matches your role:

### New to uxopian-ai?

1. [Quick Start](getting_started/quickstart.md) — Your first AI exchange in 5 minutes.
2. [Core Concepts](understanding/concepts.md) — Understand Prompts, Goals, and Conversations.
3. [Architecture Overview](understanding/architecture.md) — See how the components fit together.

### Operator / DevOps?

1. [Deploy with Docker](getting_started/installation_guide.md) — Set up the full stack.
2. [Configuration Files](reference/config_files.md) — YAML reference for all config files.
3. [Environment Variables](reference/env_variables.md) — Quick reference for Docker deployments.
4. [Backup and Recovery](how_to/backup_recovery.md) — Protect your data.

### Integrator?

1. [Architecture Overview](understanding/architecture.md) — Understand the BFF pattern.
2. [Embedding in a Web Page](how_to/integrate_web_page.md) — Add AI to any web app.
3. [Integrating with ARender](how_to/integrate_arender.md) — Add AI buttons in ARender.
4. [Integrating with FlowerDocs](how_to/integrate_flowerdocs.md) — Add AI features in FlowerDocs.

### Java Developer?

1. [Core Concepts](understanding/concepts.md) — Understand the domain model.
2. [The Templating Engine](understanding/templating.md) — Master dynamic prompt authoring.
3. [Creating Custom Helpers](extending/custom_helpers.md) — Inject your own data into prompts.
4. [Creating Custom Tools](extending/custom_tools.md) — Give the LLM the ability to take actions.
