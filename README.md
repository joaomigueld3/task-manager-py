# Task Manager - Aplicação Full Stack

![Python](https://img.shields.io/badge/Python-3.9-3776AB?logo=python) ![FastAPI](https://img.shields.io/badge/FastAPI-0.95-009688?logo=fastapi) ![React](https://img.shields.io/badge/React-18-61DAFB?logo=react) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13-4169E1?logo=postgresql) ![Docker](https://img.shields.io/badge/Docker-20.10-2496ED?logo=docker) ![Kubernetes](https://img.shields.io/badge/Kubernetes-1.27-326CE5?logo=kubernetes)

Projeto de portfólio que implementa um CRUD (Create, Read, Update, Delete) completo de um gerenciador de tarefas. O objetivo é demonstrar habilidades em todo o ciclo de vida de uma aplicação moderna, desde o desenvolvimento local com Docker até o deploy em um ambiente orquestrado com Kubernetes.

## 🏛️ Arquitetura Geral

A aplicação é dividida em três serviços principais que são executados em contêineres Docker distintos:

-   **Frontend**: Uma Single Page Application (SPA) construída com React, responsável pela interface do usuário.
-   **Backend**: Uma API RESTful desenvolvida em Python com FastAPI, que gerencia a lógica de negócio e a comunicação com o banco de dados.
-   **Database**: Uma instância do PostgreSQL para persistência dos dados.

![Arquitetura da Aplicação](https://i.imgur.com/8QWv8dM.png)
*(Recomendação: Crie seu próprio diagrama e suba a imagem para o repositório)*

## ✨ Stack Tecnológica

| Camada | Tecnologia | Propósito |
| :--- | :--- | :--- |
| **Frontend** | React, Axios | Interface do usuário reativa e comunicação com a API. |
| **Backend** | Python, FastAPI, SQLAlchemy | API de alta performance, validação de dados e ORM. |
| **Banco de Dados** | PostgreSQL | Armazenamento relacional dos dados. |
| **Testes** | Pytest, HTTPX | Testes unitários e de integração para a API. |
| **DevOps** | Docker, Docker Compose | Conteinerização e orquestração do ambiente local. |
| **Infraestrutura** | Kubernetes, NGINX | Orquestração de contêineres em produção e web server/proxy. |

## 🚀 Features

-   [x] **Criar** novas tarefas.
-   [x] **Listar** todas as tarefas existentes.
-   [x] **Atualizar** o título, descrição e status de uma tarefa.
-   [x] **Deletar** uma tarefa.
-   [x] Documentação da API gerada automaticamente via Swagger UI.
-   [x] Ambiente de desenvolvimento totalmente conteinerizado.
-   [x] Manifestos prontos para deploy em cluster Kubernetes.

## ⚙️ Como Executar Localmente

Você precisará ter o Git, Docker e Docker Compose instalados na sua máquina.

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    cd seu-repositorio
    ```

2.  **Crie o arquivo de variáveis de ambiente para o backend:**
    Navegue até a pasta `backend/` e crie um arquivo `.env` a partir do exemplo:
    ```bash
    cp backend/.env.example backend/.env
    ```
    *(Os valores padrão já devem funcionar com o `docker-compose.yml`)*

3.  **Suba os contêineres:**
    Na raiz do projeto, execute o comando:
    ```bash
    docker-compose up --build
    ```

4.  **Acesse as aplicações:**
    -   **Frontend (React)**: [http://localhost:3000](http://localhost:3000)
    -   **Backend API (FastAPI)**: [http://localhost:8000](http://localhost:8000)
    -   **Documentação da API (Swagger)**: [http://localhost:8000/docs](http://localhost:8000/docs)

## 🧪 Executando os Testes

Os testes automatizados da API foram escritos com Pytest. Para executá-los, com os contêineres rodando, abra outro terminal e execute:

```bash
docker-compose exec backend pytest
```

## 🚢 Deploy com Kubernetes

Os manifestos para o deploy estão na pasta `/k8s`.

**Pré-requisitos:**
* Um cluster Kubernetes ativo (Minikube, k3d, Docker Desktop K8s).
* `kubectl` configurado para acessar o cluster.
* As imagens Docker da aplicação (`backend` e `frontend`) enviadas para um registry (ex: Docker Hub).

1.  **Atualize os nomes das imagens:**
    Nos arquivos `k8s/api-deployment.yml` e `k8s/frontend-deployment.yml`, altere a linha `image: ...` para o nome da sua imagem no registry (ex: `seuusuario/task-manager-api:latest`).

2.  **Aplique os manifestos:**
    ```bash
    kubectl apply -f k8s/
    ```

3.  **Acesse o serviço:**
    Se estiver usando um LoadBalancer na nuvem, ele terá um IP externo. Com Minikube, você pode expor o serviço com:
    ```bash
    minikube service frontend-service
    ```

## 🔮 Próximos Passos e Melhorias

Este projeto serve como uma base sólida. Algumas melhorias possíveis são:
-   [ ] Implementar um pipeline de **CI/CD com GitHub Actions**.
-   [ ] Adicionar **autenticação e autorização** (JWT) na API.
-   [ ] Melhorar o **gerenciamento de estado** no frontend (Context API ou Zustand).
-   [ ] Adicionar **logging e monitoramento** (Prometheus/Grafana).
-   [ ] Gerenciar os manifestos Kubernetes com **Helm**.

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
