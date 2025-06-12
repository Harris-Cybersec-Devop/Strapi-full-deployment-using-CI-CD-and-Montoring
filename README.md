🚀 Strapi Deployment with Docker, GitHub Actions, Ansible, and Minikube
This project is a containerized Strapi CMS application with automated CI/CD using GitHub Actions and Ansible. The app runs on a local Kubernetes cluster via Minikube and is accessible at http://localhost:8080.

🧱 Stack
Strapi (Headless CMS)

Docker (Containerization)

GitHub Actions (CI: Build & Push)

Docker Hub (Container Registry)

Ansible (CD: Deployment automation)

Minikube + Kubernetes (Local Cluster)

Prometheus + Grafana (Monitoring - coming soon)

📦 Project Structure
bash
Copy
Edit
├── Dockerfile               # Container image for Strapi
├── .github/workflows/ci.yml# GitHub Actions CI pipeline
├── ansible/
│   ├── playbook.yml         # CD playbook for Kubernetes deployment
│   └── inventory.ini
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
├── README.md
└── ...
⚙️ CI/CD Workflow
🔄 Continuous Integration (GitHub Actions)
Trigger: Code push to main

Steps:

Build Docker image

Push image to Docker Hub

🚀 Continuous Deployment (Ansible)
Trigger: Manual run

Steps:

Pull Docker image from Docker Hub

Start Minikube

Deploy app to Kubernetes

Expose service on localhost:8080

🛠️ Usage
1. Create Strapi App (one-time)
bash
Copy
Edit
npx create-strapi@latest my-project
cd my-project
2. Build & Run Locally (optional)
bash
Copy
Edit
docker build -t my-strapi-app .
docker run -p 1337:1337 my-strapi-app
3. Trigger CI (Push to GitHub)
bash
Copy
Edit
git push origin main
4. Run CD via Ansible
bash
Copy
Edit
cd ansible
ansible-playbook -i inventory.ini playbook.yml
📍 Access the App
Once deployed via Ansible and Kubernetes:

📌 URL: http://localhost:8080
---

## 🚀 Strapi Deployment with Docker, GitHub Actions, Ansible, Minikube, and Monitoring

This project is a containerized Strapi CMS application with full CI/CD automation and monitoring support. It uses GitHub Actions for CI, Ansible for CD to a local Kubernetes cluster via Minikube, and Prometheus + Grafana for monitoring.

---

### 🧱 Stack

* **Strapi** (Headless CMS)
* **Docker** (Containerization)
* **GitHub Actions** (CI: Build & Push)
* **Docker Hub** (Container Registry)
* **Ansible** (CD: Deploy to Kubernetes)
* **Minikube** (Local Kubernetes Cluster)
* **Prometheus + Grafana** (Monitoring)

---

### 📦 Project Structure

```
├── Dockerfile
├── .github/workflows/ci.yml
├── ansible/
│   ├── playbook.yml
│   └── inventory.ini
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
├── monitoring/
│   ├── prometheus.yml
│   ├── docker-compose.yml
│   └── grafana/
│       └── dashboards/
├── README.md
└── ...
```

---

### ⚙️ CI/CD Workflow

#### 🔄 Continuous Integration (GitHub Actions)

* **Trigger:** Code push to `main`
* **Steps:**

  * Build Docker image
  * Push image to Docker Hub

#### 🚀 Continuous Deployment (Ansible)

* **Steps:**

  * Start Minikube
  * Pull latest Docker image
  * Deploy app to Kubernetes
  * Expose service on `localhost:8080`

---

### 📈 Monitoring Setup (Prometheus + Grafana)

#### ✅ How to Start

Navigate to the monitoring directory and launch both services with Docker:

```bash
cd monitoring
docker-compose up -d
```

#### 🔧 Prometheus

* **Job Targets:** Strapi Pod metrics (if exported via middleware or a sidecar)
* **Config:** `monitoring/prometheus.yml`

#### 📊 Grafana

* **URL:** `http://localhost:3000`
* **Login:** `admin` / `admin`
* **Add Prometheus as a Data Source**
* **Import Dashboards** from `monitoring/grafana/dashboards/`

> You can use a Node Exporter or custom middleware in Strapi to expose metrics.

---

### 🛠️ Usage

#### 1. Create Strapi App (initial setup)

```bash
npx create-strapi@latest my-project
cd my-project
```

#### 2. Build & Test Locally

```bash
docker build -t my-strapi-app .
docker run -p 1337:1337 my-strapi-app
```

#### 3. CI/CD Deployment

```bash
git push origin main
cd ansible
ansible-playbook -i inventory.ini playbook.yml
```

---

### 📍 Access URLs

| Service    | URL                                            |
| ---------- | ---------------------------------------------- |
| Strapi App | [http://localhost:8080](http://localhost:8080) |
| Grafana    | [http://localhost:3000](http://localhost:3000) |
| Prometheus | [http://localhost:9090](http://localhost:9090) |

---


