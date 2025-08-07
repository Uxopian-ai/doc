# Configuration & API

This section details how to configure the `uxopian-ai` service using `.yml` files and how to interact with it through its REST API.

---

## ⚙️ Configuration Management

The framework uses a standard **Spring Boot configuration model**, making it flexible and easy to manage across different environments.

### 📁 Configuration Files and Profiles

Configuration is primarily defined in:

```bash
src/main/resources/application.yml
```

You can override any property using **environment variables**, which is the recommended approach for Docker deployments.

To manage multiple environments (e.g., development, production), use **Spring Profiles**:

```yaml
# Default properties
uxopian:
  llm:
    provider: openai
  opensearch:
    host: http://localhost:9200

---
spring:
  config:
    activate:
      on-profile: dev
uxopian:
  opensearch:
    host: http://dev-opensearch:9200
```

### 🤖 LLM Provider Configuration

You can select the default LLM provider and configure its credentials in your configuration files or via environment variables:

```yaml
uxopian:
  llm:
    provider: openai
    openai:
      api-key: ${OPENAI_API_KEY}
    azure:
      endpoint: https://your-azure-endpoint.openai.azure.com/
      api-key: ${AZURE_OPENAI_API_KEY}
    anthropic:
      api-key: ${ANTHROPIC_API_KEY}
```

✅ Supported providers:

- `openai`
- `azure`
- `anthropic`
- `bedrock`
- `gemini`
- `huggingface`
- `mistral`
- `ollama`

Each provider may have specific required fields.

### 🔗 OpenSearch and Qdrant Settings

These settings define your persistence and vector storage layers:

```yaml
uxopian:
  opensearch:
    host: ${OPENSEARCH_HOST:http://localhost:9200}
    index-prefix: ai
  qdrant:
    enabled: true
    host: ${QDRANT_URL:http://localhost:6333}
    api-key: ${QDRANT_API_KEY:}
```

> Disabling `qdrant` (`enabled: false`) disables vector search and RAG-based features.

---

## 🧩 Entities Bootstrapped from YAML

At startup, `uxopian-ai` can automatically load Prompts and Goals from YAML files via `spring.config.import`. These imports are **merged** into OpenSearch using a strategy defined by the application:

```yaml
spring:
  config:
    import:
      - "optional:classpath:prompts.yml"
      - "optional:classpath:goals.yml"
```

### Merge Strategy Configuration

Each YAML import uses one of the following strategies:

| Strategy          | Prompts (by `id`)                           | Goals (by `name`)                         |
| ----------------- | ------------------------------------------- | ----------------------------------------- |
| `Override`        | Deletes all prompts, then recreates them    | Deletes all goals, then recreates them    |
| `Merge`           | Merges missing values into existing prompts | Merges missing values into existing goals |
| `CreateIfMissing` | Adds only new prompts                       | Adds only new goals                       |

---

## 🧪 REST API Reference

All interactions with `uxopian-ai` go through its REST API, including:

- Managing conversations and messages
- CRUD operations on Prompts and Goals
- Sending dynamic LLM requests

For full documentation and testing:

👉 Visit the [**Swagger UI**](https://iris.demos.uxopian.com/ai/swagger-ui.html)

> The Swagger UI includes all routes, schemas, and live testing tools.

---

## ✅ Best Practices

- 📌 Use environment variables for secrets and deployment-specific overrides
- 📂 Version control your YAML configuration and backups
- 🔁 Use the Merge/CreateIfMissing strategy during CI/CD deployments to preserve custom data
- 🧪 Use Swagger UI to validate and explore all available endpoints interactively
