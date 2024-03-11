# Full-Stack DSPy Application with FastAPI and Streamlit

## Introduction

This project is a full-stack application designed to leverage natural language processing capabilities entirely locally and to integrate with the [DSPy](https://github.com/stanfordnlp/dspy) framework developed by StanfordNLP. It features a [FastAPI](https://github.com/tiangolo/fastapi) backend for processing and a [Streamlit](https://streamlit.io) frontend for interactive user interfaces. This implementation is fully local, integrating cutting-edge technologies such as [Ollama](https://github.com/ollama/ollama) for language and embedding models, [Chroma DB](https://github.com/chroma-core/chroma) for vector storage, and [Arize Phoenix](https://github.com/Arize-ai/phoenix) for observability. This setup ensures all operations, from processing to data storage, are executed on the local machine, enhancing privacy, data security, and ease of use.

## Features

- **Fully Local Execution**: Ensures privacy and security by running all processes on your local machine without external dependencies.
- **Ollama Integration**: Leverages the powerful Ollama for language and embedding models.
- **Chroma DB Vector Storage**: Utilizes Chroma DB for efficient, scalable vector storage, enabling quick and precise information retrieval.
- **Arize Phoenix Observability**: Integrates Arize Phoenix for real-time monitoring and analytics, aiding in performance improvement and system health tracking.
- **FastAPI Backend**: Offers robust and scalable API endpoints for interacting with the NLP models and performing various queries and compilations.
- **Streamlit Frontend**: Provides an intuitive and interactive UI for users to easily interact with the backend services, improving the overall user experience.

## Architecture

This full-stack application combines the DSPy Framework with Ollama, Arize Phoenix, and Chroma DB in a cohesive ecosystem. Here's a brief overview of the system components:

- **DSPy Framework**: Serves as the core for language model interactions, offering advanced NLP capabilities.
- **Ollama**: Acts as the backend engine for language understanding and generation.
- **Chroma DB**: Provides efficient vector storage solutions, essential for NLP tasks like semantic search.
- **Arize Phoenix**: Enhances visibility into the application's performance and health.
- **FastAPI**: Facilitates the backend logic, handling API requests and responses.
- **Streamlit**: Creates the frontend interface, enabling users to engage with the backend services visually.


## Installation

### Prerequisites

- Docker and Docker-Compose
- Git (optional, for cloning the repository)
- Ollama,  follow the [readme](https://github.com/ollama/ollama) to set up and run a local Ollama instance.

### Clone the Repository

First, clone the repository to your local machine (skip this step if you have the project files already).

```bash
git clone https://github.com/diicellman/dspy-rag-fastapi.git
cd dspy-rag-fastapi
```
### Getting Started with Local Development

#### Backend setup
First, navigate to the backend directory:
```bash
cd backend/
```

Second, setup the environment:

```bash
poetry config virtualenvs.in-project true
poetry install
poetry shell
```
Specify your environment variables in an .env file in backend directory.
Example .env file:
```yml
ENVIRONMENT=<your_environment_value>
INSTRUMENT_DSPY=<true or false>
COLLECTOR_ENDPOINT=<your_arize_phoenix_endpoint>
OLLAMA_BASE_URL=<your_ollama_instance_endpoint>
```
Third, run this command to create embeddings of data located in data/example folder:
```bash
python app/utils/load.py
```

Then run this command to start the FastAPI server:
```bash
python main.py
```

#### Frontend setup
First, navigate to the frontend directory:
```bash
cd frontend/
```

Second, setup the environment:

```bash
poetry config virtualenvs.in-project true
poetry install
poetry shell
```
Specify your environment variables in an .env file in backend directory.
Example .env file:
```yml
FASTAPI_BACKEND_URL = <your_fastapi_address>
```

Then run this command to start the Streamlit application:
```bash
streamlit run about.py
```

### Getting Started with Docker-Compose
This project now supports Docker Compose for easier setup and deployment, including backend services and Arize Phoenix for query tracing. 

1. Configure your environment variables in the .env file or modify the compose file directly.
2. Ensure that Docker is installed and running.
3. Run the command `docker-compose -f compose.yml up` to spin up services for the backend, and Phoenix.
4. Backend docs can be viewed using the [OpenAPI](http://0.0.0.0:8000/docs).
5. Frontend can be viewed using [Streamlit](http://0.0.0.0:8501)
6. Traces can be viewed using the [Phoenix UI](http://0.0.0.0:6006).
7. When you're finished, run `docker compose down` to spin down the services.

## Usage

The FastAPI and Streamlit integration allows for seamless interaction between the user and the NLP backend. Utilize the FastAPI endpoints for NLP tasks and visualize results and interact with the system through the Streamlit frontend.


## Contributing

Contributions are welcome! Please feel free to submit pull requests or create issues for bugs, questions, and suggestions.

