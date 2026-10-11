# Local LLM Server Using llama.cpp and Docker

## Overview

This project deploys a local Large Language Model
using the official llama.cpp Docker server image.

The deployment uses CPU inference and does not require
a dedicated NVIDIA GPU.

## Architecture

Client
  |
  v
llama.cpp HTTP Server
  |
  v
GGUF Model
  |
  v
CPU Inference

## Prerequisites

- Ubuntu Linux
- Docker Engine
- Docker Compose
- Sufficient RAM and disk space
- Internet access to download the image and model

## Project Structure

.
├── docker-compose.yml
├── README.md
├── .gitignore
└── models/

## Deployment

1. Download or clone this repository.
2. Download a compatible GGUF model into models/.
3. Start the service:

   docker compose pull
   docker compose up -d

4. Check container status:

   docker compose ps

5. Check server health:

   curl http://127.0.0.1:8085/health

6. Open the web interface:

   http://localhost:8085

## API Test

curl http://127.0.0.1:8085/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Explain Docker in simple terms."
      }
    ],
    "max_tokens": 150
  }'

## Stop the Service

docker compose down

## Learning Outcomes

- Local LLM inference
- GGUF model format
- Docker image deployment
- Docker Compose
- Persistent model storage
- REST API testing
- Container troubleshooting
- CPU resource management
