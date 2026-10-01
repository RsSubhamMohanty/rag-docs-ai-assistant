# 🚀 RAG Internal Documentation Assistant

A production-style **Retrieval-Augmented Generation (RAG)** application for answering questions from internal technical documentation with **document sources and citations**.

The project combines **AI + DevOps + Cloud-Native technologies**, including FastAPI, ChromaDB, Docker, Kubernetes, Helm, GitHub Actions, Prometheus, and Grafana.

---

## 🧠 Overview

The application allows users to ask questions about internal technical documentation and generates grounded answers using retrieved document context.

### Architecture

```text
User
  │
  ▼
Streamlit UI
  │
  ▼
FastAPI Backend
  │
  ├── API Key Authentication
  ├── Rate Limiting
  └── Prometheus Metrics
  │
  ▼
Sentence Transformers
  │
  ▼
ChromaDB
  │
  ▼
Top-K Retrieval
  │
  ▼
Context Assembly
  │
  ▼
Groq LLM
  │
  ▼
Answer + Document Sources

  ## ✨ Key Features

  🔎 RAG-based question answering
  📚 Document retrieval using ChromaDB
  🤖 Groq LLM-powered responses
  📌 Source/citation display for retrieved documents
  🔐 API key authentication
  🚦 Request rate limiting
  ❤️ Health and readiness endpoints
  📊 Prometheus application metrics
  📈 Grafana monitoring dashboard
  🐳 Docker & Docker Compose support
  ☸️ Kubernetes deployment
  ⛵ Helm-based Kubernetes packaging
  🔄 Automated document ingestion using Kubernetes Job
  🚀 GitHub Actions CI/CD pipeline
  🔒 Dependency security auditing with pip-audit

## 🛠️ Tech Stack

 Category	                                       Technologies 

Backend	                                            Python, FastAPI
Frontend	                                    Streamlit
AI / RAG	                                           Sentence Transformers, Groq
Vector Database	                           ChromaDB
Containerization	                           Docker, Docker Compose
Orchestration	                           Kubernetes
Packaging	                                   Helm
CI/CD	                                          GitHub Actions
Monitoring	                                  Prometheus, Grafana
Testing	                                          Pytest
Code Quality	                                  Ruff
Security	                                         API Key Auth, Rate Limiting, pip-audit

## 📊 Observability

The FastAPI service exposes Prometheus metrics through:

         /metrics
The application tracks:

API request count
Request rate
Request latency
Error count
Prompt tokens
Completion tokens
Total tokens
API health

A Grafana dashboard visualizes the application metrics, while Prometheus monitors the Kubernetes API service.

The Prometheus target is configured through a Kubernetes ServiceMonitor.

## ☸️ Kubernetes Deployment

The application is deployed in the:

      rag-assistant

namespace.

Kubernetes components include:

FastAPI API Deployment
Streamlit UI Deployment
API Service
Streamlit Service
ChromaDB PersistentVolumeClaim
Document Ingestion Job
ConfigMap
Kubernetes Secrets
Prometheus ServiceMonitor

Example:

      kubectl get pods -n rag-assistant
      kubectl get services -n rag-assistant

## 🐳 Docker

The application is containerized using Docker.

Run the complete application with Docker Compose:

     docker compose up -d

Check running containers:

     docker ps

Application UI:

       http://localhost:8501

API:

       http://localhost:8000

## 🔄 CI/CD Pipeline

GitHub Actions automates the project workflow:

Push to GitHub
      │
      ▼
Install Dependencies
      │
      ▼
Ruff Lint
      │
      ▼
pip-audit Security Scan
      │
      ▼
Run Tests
      │
      ▼
Build Docker Image
      │
      ▼
Publish Image to GHCR

The pipeline validates code quality, runs automated tests, performs dependency security checks, and publishes the container image to GitHub Container Registry.

## 🧪 Testing

The project includes automated tests for the application.

Current validation:

    27 tests passed
    Ruff checks passed

Run tests:

   pytest -q

Run linting:

   ruff check .

## 📁 Project Structure

rag-docs-ai-assistant/
│
├── .github/
│   └── workflows/           # GitHub Actions CI/CD
│
├── app/                     # FastAPI backend & RAG logic
│
├── documents/               # Internal documentation
│
├── ingestion/               # Document ingestion pipeline
│
├── k8s/                     # Kubernetes manifests
│
├── helm/
│   └── rag-assistant/       # Helm chart
│
├── tests/                   # Automated tests
│
├── ui/                      # Streamlit frontend
│
├── Dockerfile
├── docker-compose.yml
├── grafana-persistence.yaml
├── requirements.txt
├── pyproject.toml
├── SECURITY.md
└── README.md

## 🔐 Security

Sensitive credentials are kept outside the repository.

    .env is excluded from Git
    Kubernetes credentials are stored using Secrets
    Local Helm secret values are ignored
    .env.example is provided as a configuration template
    The RAG query endpoint uses API key authentication
    Rate limiting is implemented to control requests

Never commit API keys, passwords, or other secrets to GitHub

## 📸 Project Evidence

The project demonstrates:

## RAG application architecture
## Docker containers running successfully
## Kubernetes workloads running successfully
## GitHub Actions CI/CD pipeline
## Prometheus target showing the API as UP
## Grafana monitoring dashboard
## Streamlit RAG interface returning answers with document sources

## 🎯 Project Outcome

This project demonstrates an end-to-end AI + DevOps + Cloud-Native workflow:

         Build → Containerize → Test → Deploy → Monitor

It combines a functional RAG application with automated CI/CD, Kubernetes orchestration, persistent storage, authentication, rate limiting, and production-style observability using Prometheus and Grafana.