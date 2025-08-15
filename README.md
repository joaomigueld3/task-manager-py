# Full-Stack Task Manager on Kubernetes

![Architecture Diagram](https://i.imgur.com/8QWv8dM.png)

A full-stack CRUD application for managing tasks. This project is built using a modern technology stack and follows best practices for containerization and orchestration, from local development to a cloud-native deployment scenario.

[![CI/CD Pipeline](https://github.com/YOUR_USERNAME/YOUR_REPO/actions/workflows/main.yml/badge.svg)](https://github.com/YOUR_USERNAME/YOUR_REPO/actions/workflows/main.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 🚀 Tech Stack

This project leverages a range of modern technologies to create a robust and scalable application:

| Category          | Technology                                       |
| ----------------- | ------------------------------------------------ |
| **Frontend** | React, Axios                                     |
| **Backend** | Python 3.9, FastAPI, SQLAlchemy, Pydantic        |
| **Database** | PostgreSQL                                       |
| **Containerization**| Docker, Docker Compose                           |
| **Orchestration** | Kubernetes (K8s)                                 |
| **Testing** | Pytest, HTTPX                                    |
| **CI/CD** | GitHub Actions (Example placeholder)             |


## ✨ Features

- **Create, Read, Update, Delete (CRUD)** operations for tasks.
- **RESTful API** backend with automated, interactive documentation (via Swagger UI).
- **Single Page Application (SPA)** frontend with a clean user interface.
- **Containerized** services for consistent development and production environments.
- **Kubernetes-ready** manifests for scalable deployment.
- **Automated API testing** to ensure reliability.

---

## 🏁 Getting Started

Follow these instructions to get the project up and running on your local machine.

### Prerequisites

You must have the following tools installed:
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/products/docker-desktop/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Local Development Setup

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/YOUR_REPO.git](https://github.com/YOUR_USERNAME/YOUR_REPO.git)
    cd fullstack-task-manager
    ```

2.  **Configure Environment Variables:**
    The backend API requires a `.env` file for configuration. You can create one by copying the example file.
    ```bash
    cp task-manager-api/.env.example task-manager-api/.env
    ```
    *No changes are needed in the `.env` file to run locally with Docker Compose.*

3.  **Launch the Application:**
    Use Docker Compose to build the images and start the containers for the frontend, backend, and database.
    ```bash
    docker-compose up --build -d
    ```

4.  **Access the Services:**
    - **Frontend Application:** [http://localhost:3000](http://localhost:3000)
    - **Backend API Docs (Swagger):** [http://localhost:8000/docs](http://localhost:8000/docs)
    - **PostgreSQL Database:** Connect on port `5432` (if needed)

### Running Automated Tests

To run the backend API tests, execute the following command:
```bash
docker-compose exec api pytest
