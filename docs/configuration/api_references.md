# **🧪 REST API & Swagger**

All interactions with uxopian-ai go through its REST API. This page provides an overview of the endpoints and how to access the interactive documentation.

## **📘 Interactive Documentation (Swagger UI)**

The service exposes a full **OpenAPI 3.1.0** specification. We highly recommend using the built-in Swagger UI for exploring the API, inspecting schemas, and testing requests in real-time.

### **Accessing Swagger UI**

Depending on your environment, the Swagger UI is available at:

- **Local / Docker**: [http://localhost:${UXOPIAN_AI_PORT}/swagger-ui.html](http://localhost:${UXOPIAN_AI_PORT}/swagger-ui.html) (Default port is 8080)

**Note:** If a custom CONTEXT_PATH is configured in application.yml, append it to the base URL (e.g., [http://localhost:8080/ai/swagger-ui.html](http://localhost:8080/ai/swagger-ui.html)).

## **🔌 API Overview**

### **🗣️ Conversations**

Manage the lifecycle of chat sessions.

- POST /api/v1/conversations: Create a new conversation.
- GET /api/v1/conversations: List user conversations (paginated).
- GET /api/v1/conversations/{id}: Retrieve full details of a specific conversation.
- DELETE /api/v1/conversations/{id}: Delete a conversation.

### **📨 Requests (Chat)**

Send messages and interact with the LLM.

- POST /api/v1/requests: Send a message and get a synchronous response.
- POST /api/v1/requests/stream: Send a message and receive the response as a **Server-Sent Events (SSE)** stream (recommended for UI).
- POST /api/v1/requests/retry: Regenerate the last answer.

### **🔧 Administration**

Endpoints restricted to users with the admin role.

- GET /api/v1/admin/stats/global: Retrieve global system statistics.
- POST /api/v1/admin/prompts: Create or update a prompt definition.
- GET /api/v1/admin/goals: Manage orchestration goals.

## **🔐 Authentication**

As detailed in the **User Guide**, the API expects authentication via headers injected by your Gateway or BFF.

| Header          | Required | Description                          |
| --------------- | -------- | ------------------------------------ |
| X-User-Id       | Yes      | Unique User ID.                      |
| X-User-TenantId | Yes      | Tenant isolation key.                |
| X-User-Roles    | No       | Comma-separated roles (e.g., admin). |
