# **Core Concepts**

This section explains the primary entities and concepts that form the uxopian-ai framework. Understanding these concepts is essential for effective configuration and interaction.

## **Providers**

A **Provider** is a connector to an external Large Language Model (LLM) service. The framework uses providers to abstract the specific implementation details of each LLM service, offering a unified interface.

* **Examples:** openai, azure, anthropic, mistral.  
* **Configuration:** The active providers and their API keys are configured in your .yml files.  
* **Extensibility:** You can add custom providers by implementing the ModelProvider Java interface.

## **Models**

A **Model** refers to a specific language model available through a provider. Each provider supports one or more models with different capabilities and costs.

* **Examples:** gpt-4o (from OpenAI), claude-3-5-sonnet-20240620 (from Anthropic).  
* **Configuration:** You can set a default model for the entire framework and override it for specific prompts or API calls.

## **Conversations**

A **Conversation** is a container that groups a sequence of exchanges between a user and the AI. It maintains the context and history of the interaction.

* **Persistence:** Conversations and their associated messages are stored in OpenSearch.  
* **Context:** The framework automatically retrieves recent messages from the current conversation to provide context for new requests, enabling stateful interactions.

## **Messages**

A **Message** represents a single turn in a conversation. It can be a user's query or the AI's response. When sending a message, you can provide one of the following (processed in order of priority):

1. goalName: To execute a high-level task.  
2. promptId: To use a specific, pre-defined prompt.  
3. content: A simple, direct text query.  
* **Persistence:** All messages are stored in OpenSearch, linked to their parent conversation.

## **Prompts**

A **Prompt** is a reusable, templated instruction sent to a model to guide its response. Prompts are the core building blocks for interacting with LLMs.

* **Templating:** They use the **Thymeleaf** engine, allowing for dynamic content using variables (e.g., ${payload.documentId}) and advanced logic.  
* **Storage:** Prompts are stored and managed in OpenSearch. They can be created and updated via the REST API.

## **Goals**

A **Goal** is a high-level, reusable task that orchestrates which Prompt to use based on a given context. A goal is essentially a mapping between a specific situation (defined by a filter) and a specific prompt.

* **Example Use Case:** A Goal named "compare" could use the detailedComparison prompt if the document type is a 'contract', but use the genericComparison prompt otherwise.  
* **Filtering:** The filter logic uses Spring Expression Language (SpEL) to evaluate the context sent in the API call's payload.  
* **Storage:** Like prompts, goals are stored and managed in OpenSearch.

