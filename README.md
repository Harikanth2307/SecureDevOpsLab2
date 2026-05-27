# 🔒 SecureDevOps Lab 2

> **Full-stack DevSecOps learning platform — Flask REST API + React/TypeScript frontend, containerised with Docker and deployed on Google Cloud**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GCP](https://img.shields.io/badge/GCP-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)

> ⚠️ **This application contains intentional security vulnerabilities. It is designed for DevSecOps training and security research only. DO NOT deploy with real user data or in production.**

---

## 📌 What This Project Does

SecureDevOps Lab 2 is a **complete full-stack application** built as a realistic DevSecOps training environment. It simulates a real e-learning platform with:

- A **React + TypeScript frontend** served via Nginx
- A **Flask REST API backend** with JWT-based authentication
- **Docker Compose** orchestration for multi-service deployment
- Deployment on **Google Cloud Platform (GCP)**
- Intentional **OWASP Top 10 vulnerabilities** for security testing and learning

This is the upgraded version of SecDevOps-back — now with a complete UI, containerised infrastructure, and cloud deployment.

---

## 🧩 System Architecture

```
Browser / Client
      │
      ▼
┌─────────────────────────────────────────┐
│         Docker Compose Network          │
│                                         │
│  ┌──────────────────────────────────┐   │
│  │  Frontend (React + TypeScript)   │   │
│  │  Served via Nginx  →  Port 80    │   │
│  └────────────────┬─────────────────┘   │
│                   │ API calls           │
│  ┌────────────────▼─────────────────┐   │
│  │  Backend (Flask REST API)        │   │
│  │  Port 4000                       │   │
│  │  SQLite Database (learning.db)   │   │
│  └──────────────────────────────────┘   │
│                                         │
└─────────────────────────────────────────┘
      │
      ▼
  Google Cloud Platform (GCP VM)
```

---

## 📁 Project Structure

```
SecureDevOpsLab2/
│
├── backend-flask/
│   ├── app.py                  # Flask REST API (routes, models, auth)
│   ├── Dockerfile              # Backend container definition
│   └── requirements.txt        # Python dependencies
│
├── frontend-react/
│   ├── src/                    # React + TypeScript source
│   ├── public/                 # Static assets
│   ├── Dockerfile              # Frontend container (Nginx)
│   └── package.json
│
└── docker-compose.yml          # Multi-service orchestration
```

---

## 🚀 Getting Started

### Prerequisites

- Docker & Docker Compose installed
- Git

### Run the Full Stack Locally

```bash
# Clone the repo
git clone https://github.com/Harikanth2307/SecureDevOpsLab2.git
cd SecureDevOpsLab2

# Build and start all services
docker-compose up --build
```

| Service | URL |
|---|---|
| Frontend (React) | http://localhost:80 |
| Backend (Flask API) | http://localhost:4000 |

### Run Services Individually

```bash
# Backend only
cd backend-flask
pip install -r requirements.txt
python app.py

# Frontend only
cd frontend-react
npm install
npm start
```

---

## 🐛 Security Vulnerabilities (OWASP Top 10)

This lab intentionally implements the following vulnerabilities for learning and testing:

| Vulnerability | Location | Description |
|---|---|---|
| **SQL Injection** | `/api/login` | Raw SQL string concatenation |
| **Broken Authentication** | All routes | Hardcoded JWT secret key |
| **Plaintext Passwords** | `/api/register` | No password hashing |
| **IDOR** | `/api/student-submissions/<id>` | No ownership check |
| **Stored XSS** | Course descriptions | No input sanitisation |
| **Insecure File Upload** | `/api/submit-assignment` | No file type validation |
| **Path Traversal** | `/api/download/<filename>` | No path sanitisation |
| **Command Injection** | `/api/export-grades` | `os.system()` with raw input |
| **Broken Access Control** | `/api/grade-submission` | No auth check |
| **Role Manipulation** | `/api/register` | Client-controlled role assignment |

---

## ☁️ Cloud Deployment (GCP)

The application is deployed on a **Google Cloud Platform VM** with Docker Compose managing both services on the same host.

```yaml
# docker-compose.yml — key config
frontend:
  ports: ["80:80"]           # Nginx serves React on port 80
  depends_on: [backend-flask]

backend-flask:
  ports: ["4000:4000"]       # Flask API on port 4000
  environment:
    - FLASK_ENV=development
```

To deploy on your own GCP instance:
1. SSH into your VM
2. Clone this repo
3. Run `docker-compose up --build -d`

---

## 🔧 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, TypeScript, HTML/CSS |
| Backend | Python, Flask, SQLAlchemy |
| Database | SQLite |
| Authentication | JWT (PyJWT) |
| Web Server | Nginx |
| Containerisation | Docker, Docker Compose |
| Cloud | Google Cloud Platform (GCP) |

---

## 👤 Author

**Hari Kanth Karne** — Cloud Engineer | Cybersecurity | AI | ML

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hari-kanth-karne-741083368)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Harikanth2307)

---

> Built for **DevSecOps education and security research**. Not intended for production use.
