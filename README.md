<<<<<<< HEAD
=======
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2E3192,100:1BFFFF&height=200&section=header&text=Fast%20Blog%20API&fontSize=55&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=A%20production-style%20FastAPI%20blog%20platform%20on%20Kubernetes&descAlignY=55&descSize=18" width="100%"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1000&color=1BFFFF&center=true&vCenter=true&width=600&lines=Code+%E2%86%92+GitHub+%E2%86%92+Jenkins+%E2%86%92+Docker;Artifact+Registry+%E2%86%92+GKE+%E2%86%92+HTTPS;Self-Healing+%E2%80%A2+Multi-Replica+%E2%80%A2+Production-Ready" alt="Typing SVG" />

<br/>

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://www.jenkins.io/)
[![GKE](https://img.shields.io/badge/GKE-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)](https://cloud.google.com/kubernetes-engine)

<br/>

![Stars](https://img.shields.io/github/stars/Sujay14/blog-docker?style=social)
![Forks](https://img.shields.io/github/forks/Sujay14/blog-docker?style=social)
![Last Commit](https://img.shields.io/github/last-commit/Sujay14/blog-docker?color=1BFFFF&label=last%20commit&style=flat-square)
![Repo Size](https://img.shields.io/github/repo-size/Sujay14/blog-docker?color=blueviolet&style=flat-square)

</div>

<br/>

## ✨ Overview

**Fast Blog API** is a full-stack blog application built with **FastAPI** and **PostgreSQL**, containerized with **Docker**, and deployed through a **Jenkins CI/CD pipeline** to **Google Kubernetes Engine (GKE)**.

It traces the complete journey from source code to a cloud-hosted, self-healing application — an end-to-end DevOps build, not just a coding exercise.

<br/>

## 📑 Table of Contents

<div align="center">

[Highlights](#-highlights) • [Architecture](#️-architecture) • [Tech Stack](#-tech-stack) • [CI/CD Pipeline](#-cicd-pipeline) • [Kubernetes](#️-kubernetes) • [Config & Security](#-configuration--security) • [Structure](#-project-structure) • [Getting Started](#-getting-started) • [API Docs](#-api-documentation) • [Takeaways](#-devops-takeaways) • [Author](#-author)

</div>

<br/>

## 🎯 Highlights

<div align="center">

| | | |
|:---:|:---|:---|
| 🔐 | **Auth** | JWT authentication and authorization |
| 📝 | **Blog CRUD** | Create, update, and delete blog posts |
| 👤 | **Profiles** | User profiles and password reset |
| 🖼️ | **Media** | Profile picture uploads via AWS S3 |
| 🗄️ | **Database** | PostgreSQL with SQLAlchemy ORM |
| 🔄 | **Migrations** | Alembic-managed schema changes |
| 🐳 | **Containerized** | Fully Dockerized application |
| 🔧 | **CI/CD** | Automated Jenkins pipeline |
| 📦 | **Registry** | Google Artifact Registry |
| ☸️ | **Orchestration** | Kubernetes deployment on GKE |
| 🔁 | **Resilience** | Multi-replica, self-healing pods |
| 🌐 | **Networking** | Service + Ingress routing |
| 🔒 | **HTTPS** | Google-managed SSL certificate |
| 📊 | **Observability** | New Relic APM monitoring |

</div>

<br/>

## 🏗️ Architecture

<div align="center">

```mermaid
flowchart TD
    A[👨‍💻 Developer Push] --> B[🐙 GitHub]
    B --> C[🔧 Jenkins CI/CD]
    C --> D[🐳 Docker Build]
    D --> E[📦 Artifact Registry]
    E --> F[☸️ GKE Cluster]
    F --> G1[Pod 1 · FastAPI]
    F --> G2[Pod 2 · FastAPI]
    F --> G3[Pod 3 · FastAPI]
    G1 & G2 & G3 --> H[Service]
    H --> I[Ingress + HTTPS]
    I --> J[🌐 Users]
    F --> K[(🗄️ PostgreSQL)]
    F --> L[☁️ AWS S3]
```

</div>

<br/>

## 🧰 Tech Stack

<div align="center">

<img src="https://skillicons.dev/icons?i=python,fastapi,postgres,docker,jenkins,kubernetes,gcp,aws" />

</div>

<br/>

| Layer | Technologies |
|---|---|
| **Backend** | Python, FastAPI, Pydantic, SQLAlchemy |
| **Database** | PostgreSQL, SQL |
| **Authentication** | JWT, OAuth2 Bearer |
| **Storage** | AWS S3 |
| **Migrations** | Alembic |
| **Templates** | Jinja2 |
| **Containerization** | Docker |
| **CI/CD** | Jenkins |
| **Registry** | Google Artifact Registry |
| **Orchestration** | Kubernetes, GKE |
| **Networking** | Service, Ingress, DNS, HTTP/HTTPS |
| **Monitoring** | New Relic APM |
| **Cloud** | Google Cloud, AWS |

<br/>

## 🔄 CI/CD Pipeline

```
1. Developer pushes code
2. Jenkins checks out the repository
3. Docker image is built
4. Image is pushed to Artifact Registry
5. Jenkins applies Kubernetes manifests
6. GKE pulls the new image
7. Deployment rolls out updated Pods
8. Ingress exposes the application over HTTPS
```

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/ingress.yaml
```

<br/>

## ☸️ Kubernetes

The application runs behind a Kubernetes Service with multiple replicas:

```
                 Ingress
                    │
                    ▼
               Service :80
                    │
          ┌─────────┼─────────┐
          ▼         ▼         ▼
        Pod 1     Pod 2     Pod 3
        :8080     :8080     :8080
```

### 🔁 Self-Healing in Action

```
3 replicas desired

Pod 1 ✅
Pod 2 ❌  → Kubernetes recreates it automatically
Pod 3 ✅

Result → 3 healthy replicas maintained
```

This demonstrates declarative configuration, replica management, service discovery, and self-healing — core Kubernetes primitives in practice.

<br/>

## 🔐 Configuration & Security

Sensitive values are supplied through environment variables rather than committed to source control:

```env
DATABASE_URL=your_database_url
SECRET_KEY=your_secret_key

S3_BUCKET_NAME=your_bucket
S3_REGION=your_region
S3_ACCESS_KEY_ID=your_access_key
S3_SECRET_ACCESS_KEY=your_secret_key
```

> ⚠️ **Never commit real credentials, API keys, database passwords, or secret keys.**

<br/>

## 📁 Project Structure

```
blog-docker/
├── alembic/              # Database migrations
├── k8s/                  # Kubernetes manifests
├── routers/               # Application routes
├── static/                 # Static assets
├── templates/               # Jinja2 templates
├── tests/                  # Tests
├── auth.py                 # Authentication
├── config.py                # Configuration
├── database.py               # Database setup
├── email_utils.py             # Email utilities
├── image_utils.py             # Image/S3 utilities
├── main.py                  # FastAPI entry point
├── models.py                 # Database models
├── schemas.py                # Pydantic schemas
├── Dockerfile                # Docker image definition
├── Jenkinsfile                # CI/CD pipeline
├── alembic.ini                # Alembic configuration
├── pyproject.toml              # Python configuration
└── uv.lock                  # Dependency lock file
```

<br/>

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Sujay14/blog-docker.git
cd blog-docker
```

### 2. Install dependencies

```bash
uv sync
```

### 3. Configure environment

Create a `.env` file with the required database, authentication, AWS S3, and email settings (see [Configuration & Security](#-configuration--security)).

### 4. Run migrations

```bash
uv run alembic upgrade head
```

### 5. Start the application

```bash
uv run uvicorn main:app --reload
```

App → **http://localhost:8000**
Swagger → **http://localhost:8000/docs**

### 🐳 Run with Docker

```bash
docker build -t fastapi-blog .
docker run -p 8080:8080 --env-file .env fastapi-blog
```

> The containerized application listens on port `8080`.

<br/>

## 📚 API Documentation

FastAPI provides interactive API documentation out of the box:

- **Swagger UI** → `/docs`
- **ReDoc** → `/redoc`

<br/>

## 🧠 DevOps Takeaways

Building and shipping this project was as much a DevOps learning exercise as a coding one. Key takeaways:

- Containerization workflows with Docker
- CI/CD automation with Jenkins
- Container image lifecycle management
- Working with Google Artifact Registry
- Kubernetes Deployments, Pods, and Services
- Ingress configuration and routing
- End-to-end GKE deployment workflows
- Replica-based self-healing in practice
- DNS and HTTPS setup for production apps
- Cloud-native application architecture
- Application monitoring with New Relic

<br/>

## 👨‍💻 Author

<div align="center">

**Sujay E**
*Junior DevOps / Cloud Engineer*

Interested in cloud infrastructure, containerization, CI/CD automation, Kubernetes, and reliable application delivery.

[![GitHub](https://img.shields.io/badge/GitHub-Sujay14-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Sujay14)
[![Repository](https://img.shields.io/badge/Repo-blog--docker-blue?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Sujay14/blog-docker)

<br/>
>>>>>>> 2a0c963 (readme update)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2E3192,100:1BFFFF&height=100&section=footer" width="100%"/>

*⭐ Built with FastAPI, Docker, Kubernetes & a suspicious number of `kubectl` commands.*

</div>
