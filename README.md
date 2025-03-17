# 🚀 Running n8n with Docker

## 📌 Overview

[n8n](https://n8n.io/) is a flexible workflow automation tool that can be run locally or on cloud servers. This guide explains how to run `n8n` using `Docker` with `docker-compose.yml`.

---

## 🏗️ Requirements

- **Docker** installed on your system. [Download Docker](https://docs.docker.com/get-docker/)
- **Docker Compose** installed. [Download Docker Compose](https://docs.docker.com/compose/install/)

---

## 📄 Setting up `docker-compose.yml`

Create a `docker-compose.yml` file in a new directory with the following content:

```yaml
version: '3.8'

services:
  n8n:
    image: n8nio/n8n:latest
    restart: always
    ports:
      - "5678:5678"
    environment:
      - N8N_DEFAULT_USER_NAME=${N8N_USER}
      - N8N_DEFAULT_USER_PASSWORD=${N8N_PASS}
    volumes:
      - ./n8n_data:/home/node/.n8n  
volumes:
  n8n_data:
```

---

## 🔑 Setting Up Environment Variables

Create a `.env` file in the same directory and add the following credentials:

```env
N8N_USER=your-username
N8N_PASS=your-secure-password
```

🔒 **Note:** Make sure to use a strong password to secure access to n8n.

---

## 🚀 Running n8n

Once the files are set up, start `n8n` with the following command:

```bash
docker-compose up -d
```

📌 To check if `n8n` is running, open your browser and go to:
```
http://localhost:5678
```

---

## 🔧 Possible Enhancements

### ✅ **Use a PostgreSQL database** instead of the default storage.
### ✅ **Enable SSL** for security in a production environment.
### ✅ **Use `docker secrets`** instead of environment variables for credentials security.

---

## 🛠️ Additional Commands

📌 **Stop the container:**
```bash
docker-compose down
```

📌 **Restart the service after modifications:**
```bash
docker-compose up -d --build
```

📌 **Check logs:**
```bash
docker-compose logs -f
```

---

## 📢 Have Suggestions?

If you have any improvements or feedback, feel free to share! 😊

#n8n #docker #automation #workflowautomation #devops

