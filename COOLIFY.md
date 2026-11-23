# Deploying on Coolify (Self-Hosted)

This guide explains how to deploy this project on your self-hosted **Coolify** instance in under 3 minutes.

---

## 🚀 Quick Setup (1-Click Docker Compose)

1. Open your **Coolify Dashboard**.
2. Click **+ Create New Resource** $\rightarrow$ **Public/Private Repository** (or GitHub App).
3. Select your repository: `ix360/openconstructionerp` (or your chosen repository name).
4. Set **Build Pack** to:
   * **Docker Compose** (Coolify automatically detects the root `docker-compose.yml`).
5. In **Environment Variables** (optional, defaults are already provided):
   * `HOST_PORT`: Host port mapping (default is `8088` to avoid port `8080` collisions on VPS hosts).
   * `POSTGRES_PASSWORD`: A secure database password (e.g. generated via password manager).
   * `JWT_SECRET`: A secure random secret string (e.g. `openssl rand -hex 32`).
   * `ALLOWED_ORIGINS`: Set to your domain (e.g. `https://erp.yourdomain.com`).
6. In **Domains**:
   * Add your custom domain (e.g. `https://erp.yourdomain.com`). Coolify will automatically configure Traefik with free Let's Encrypt SSL.
   * Ensure the destination internal port is set to **`8080`**.
7. Click **Deploy**.

---

## 📦 What Coolify Runs

* **App Service:** A unified Docker container running the compiled React frontend + FastAPI backend on port `8080`.
* **PostgreSQL 16:** Database container with persistent storage volume (`pg_data`).
* **Storage Volume:** App data volume (`app_data`) persisting uploads, BIM files, and project documents.

---

## 🔑 Initial Login

Once deployed, access your URL and use the initialized credentials:
* **Email:** `demo@openconstructionerp.com`
* **Password:** `DemoPass1234!`
*(Or use the 1-click **Try demo** button to explore).*
