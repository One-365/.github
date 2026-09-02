# One 365 🚀
**Enterprise HR Multi-Agent System**

Welcome to the official repository for **One 365**, a next-generation Human Resource Management system powered by Artificial Intelligence and a Multi-Agent Architecture.

## 🏗️ Architecture & Tech Stack

This project is built using a modern, scalable microservices architecture to ensure high security and performance for enterprise clients.

### 💻 Frontend
* **Framework:** React (via Vite) - Lightweight, extremely fast, and optimized for Single Page Applications (SPA).

### ⚙️ Backend (Microservices)
* **Core HR Service:** Spring Boot (Java) - Handles enterprise business logic, employee profiles, payroll, leaves, and EPF/ETF management.
* **AI & Agent Service:** FastAPI (Python) - Manages the Multi-Agent system (Recruitment Agent, Support Agent, Performance Tracking) and interacts seamlessly with ML/NLP models.

### 🗄️ Data & Storage
* **Primary Database:** PostgreSQL(Neon db) - Reliable relational data management.
* **Vector Database:** Pinecone / Weaviate - Essential for our RAG (Retrieval-Augmented Generation) engine to scan CVs and local labor laws.
* **Caching:** Redis - High-speed caching and AI 24/7 chat session management.
* **Database Migrations:** Flyway - Ensures strict schema synchronization across the development team.

### 🔄 Microservices Communication
* **Event Streaming:** Apache Kafka - Asynchronous communication (e.g., real-time burnout alerts from the AI layer to the HR dashboard).
* **Internal APIs:** gRPC - High-performance, low-latency synchronous communication between Core and AI services.

### 🔒 Security & DevOps
* **Identity & Access Management (IAM)::** Keycloak - Enterprise-grade security and role-based access control.
* **Containerization:** Docker & Docker Compose - Guarantees exact environment replication for all developers.
* **Orchestration:** Kubernetes (K8s) - Highly scalable cloud deployment.
* **Cloud Infrastructure:** AWS / Azure.

---

## 🛠️ Local Development Setup

To ensure all developers are perfectly synced without data conflicts, we use **Flyway** for database migrations and **Docker Compose** for local environments. **Do not create tables manually.**

### Prerequisites
* Docker & Docker Compose
* Java 17+
* Python 3.10+
* Node.js & npm

### Getting Started

```bash
# 1. Clone the repository
git clone [https://github.com/one365-org/one-365.git](https://github.com/one365-org/one-365.git)
cd one-365

# 2. Start the database and infrastructure services (Postgres, Redis, Kafka, Keycloak)
docker-compose up -d

# 3. Start the Core Backend (Spring Boot) - This will auto-run Flyway migrations
cd core-service
./mvnw spring-boot:run

# 4. Start the AI Backend (FastAPI)
cd ai-service
pip install -r requirements.txt
uvicorn main:app --reload

# 5. Start the Frontend (React/Vite)
cd frontend
npm install
npm run dev
