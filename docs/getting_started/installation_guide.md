## Installation Guide

This guide provides instructions for deploying the `uxopian-ai` service. We will cover the recommended Docker-based deployment and the manual Java application setup.

### Docker Deployment (Recommended)

Deploying with Docker is the recommended method as it provides a consistent and isolated environment.

#### Step 1: Pull the Docker Image

Pull the official `uxopian-ai` image from the Arondor Artifactory:

```bash
docker pull artifactory.arondor.cloud:5001/uxopian-ai/ai-standalone
```

#### Step 2: Understand Configuration

The service is configured through a set of `.yml` files (`application.yml`, `opensearch.yml`, `llm-clients-config.yml`, etc.). You can override any configuration parameter by setting an environment variable when running the container.

For example, the OpenSearch host is defined in `opensearch.yml` as:

```yaml
host: ${OPENSEARCH_HOST:localhost}
```

This means you can set the `OPENSEARCH_HOST` environment variable to specify your server's address.

**Key Environment Variables to Configure:**

* **OpenSearch Connection:**

  * `OPENSEARCH_HOST`: The hostname of your OpenSearch server.
  * `OPENSEARCH_PORT`: The port for your OpenSearch instance (default: 9200).

* **LLM Provider API Keys:**

  * `OPENAI_API_KEY`: Your API key for OpenAI.
  * `ANTHROPIC_API_KEY`: Your API key for Anthropic.
    *(See `llm-clients-config.yml` for all provider variables)*

* **Default LLM:**

  * `LLM_DEFAULT_PROVIDER`: The default provider to use (e.g., `openai`).
  * `LLM_DEFAULT_MODEL`: The default model to use (e.g., `gpt-4o`).

* **Server Port:**

  * `UXOPIAN_AI_PORT`: The port on which the service will run inside the container (default: 8080).

#### Step 3: Run the Container

Run the Docker container, mapping the port and passing the necessary environment variables.

**Example Command:**

This example runs the service on port 8080 and connects it to an OpenSearch instance. You would typically also provide an API key for at least one LLM provider.

```bash
docker run --rm \
  -p 8080:8080 \
  -e OPENSEARCH_HOST="your_opensearch_host" \
  -e OPENSEARCH_PORT="9200" \
  -e OPENAI_API_KEY="your_openai_api_key" \
  --name uxopian-ai \
  artifactory.arondor.cloud:5001/uxopian-ai/ai-standalone
```

---

### Java Application Deployment

You can also run the service directly as a Java application.

#### Step 1: Download the Application Package

Download the installation ZIP file from the Arondor Artifactory:

```
https://artifactory.arondor.cloud/artifactory/arondor-snapshot/com/uxopian/ai-standalone/2025.0.0-SNAPSHOT/ai-standalone-2025.0.0.zip
```

#### Step 2: Configure the Service

* Unzip the package.
* Navigate to the `config` directory.
* Edit the `.yml` files (e.g., `opensearch.yml`, `llm-clients-config.yml`) to match your environment. You must at least configure your OpenSearch connection and provide the necessary API keys for the LLM providers you intend to use.

#### Step 3: Run the Application

From the root of the unzipped directory, start the service using the Java 21 runtime:

```bash
java -jar ai-standalone-2025.0.0.jar
```

---

### Client-Side Integration

Once the `uxopian-ai` service is running, you must configure your client application to communicate with it.

#### ARender Integration

* **Download the Integration Package:**
  From the Arondor Artifactory, download the latest version of `arender-iris-2025.0.0-SNAPSHOT.zip`.

* **Deploy Files:**
  During your ARender deployment, place the files from the ZIP archive next to the `arondor-arender-hmi-spring-boot-[current_version].jar`. The front-end configurations will be loaded automatically.

* **Configure the Endpoint:**
  Open the `arender-custom-client.properties` file and locate the following line:

  ```properties
  uxopian.ai.host=http://localhost:8080/ai
  ```

  Change the URL to match the address of your running `uxopian-ai` service.

#### FlowerDocs Integration

* **Download the Integration Package:**
  From the Arondor Artifactory, download the latest version of `flowerdocs-iris-2025.0.0-SNAPSHOT.zip`.

* **Deploy Files:**
  Unzip the package and integrate the configuration files into the scope of your target FlowerDocs instance.

* **Configure the Endpoint:**
  Open the file located at `./conf/Script/consts/consts` and find the following line:

  ```javascript
  const UXO_AI_ENDPOINT = "https://iris.demos.uxopian.com/ai";
  ```

  Modify this constant to point to the URL of your `uxopian-ai` service.

---
