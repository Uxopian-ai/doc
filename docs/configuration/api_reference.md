## Configuration & API

This section details how to configure the `uxopian-ai` service using `.yml` files and how to interact with it through its REST API.

### Configuration Management

The framework uses a standard Spring Boot configuration model, making it flexible and easy to manage for different environments.

#### Configuration Files and Profiles

Configuration is primarily defined in `src/main/resources/application.yml`. You can override any property using environment variables, which is the recommended approach for Docker deployments.

For managing multiple environments (e.g., development, production), you can use **Spring Profiles**. Define profile-specific properties in your `application.yml` like so:

```yaml
# Default properties
uxopian:
  llm:
    provider: openai
  opensearch:
    host: http://localhost:9200

---
# Properties for the 'dev' profile
spring:
  config:
    activate:
      on-profile: dev
uxopian:
  opensearch:
    host: http://dev-opensearch:9200
```

#### LLM Provider Configuration

You can select the default LLM provider and configure its credentials in your configuration files or via environment variables.

Example:

```yaml
uxopian:
  llm:
    provider: openai # Sets the default provider
    openai:
      api-key: ${OPENAI_API_KEY}
    azure:
      endpoint: https://your-azure-endpoint.openai.azure.com/
      api-key: ${AZURE_OPENAI_API_KEY}
    anthropic:
      api-key: ${ANTHROPIC_API_KEY}
```

The available providers are: `openai`, `azure`, `anthropic`, `bedrock`, `gemini`, `huggingface`, `mistral`, and `ollama`. Each has its own set of required properties.

#### OpenSearch and Qdrant Settings

These settings control the connection to your persistence and vector store services.

```yaml
uxopian:
  opensearch:
    host: ${OPENSEARCH_HOST:http://localhost:9200}
    index-prefix: ai # A prefix for all created indices
  qdrant:
    enabled: true
    host: ${QDRANT_URL:http://localhost:6333}
    api-key: ${QDRANT_API_KEY:}
```

> Disabling `qdrant` (`enabled: false`) will bypass vector search capabilities and RAG-based workflows.

### REST API Reference

All interactions with the `uxopian-ai` service are performed through its REST API. The API allows you to manage conversations, send messages, and configure entities like **Prompts** and **Goals**.

For a complete and interactive list of all available endpoints, their parameters, and response models, please refer to the official [**Swagger UI**](https://iris.demos.uxopian.com/ai/swagger-ui.html) documentation provided with the service.
