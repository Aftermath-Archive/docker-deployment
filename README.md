# Aftermath Archive - Deployment Guide

This repository provides Docker-based deployment configurations for the Aftermath Archive application, including both a standalone setup, and a setup with MongoDB included.

## Repository Structure

```
/                      # Base deployment setup (assumes external MongoDB)
/docker-with-mongodb   # Deployment setup that includes MongoDB as a service
```

## Which Setup Should You Use?

| Setup                   | Use Case                                                            |
| ----------------------- | ------------------------------------------------------------------- |
| `/` (Standard Setup)    | If you **already have a MongoDB database** hosted separately.       |
| `/docker-with-mongodb/` | If you want a **self-contained deployment** with MongoDB in Docker. |

### Standard Docker Deployment

**This setup assumes that you have an existing MongoDB database**, either:

-   Self-hosted on a separate server or cloud provider.
-   Using MongoDB Atlas or another managed database service.

#### Setup

1. Clone this repo:
    ```
    https://github.com/Aftermath-Archive/docker-deployment
    cd docker-deployment
    ```
2. Create the necessary .env files based on the examples:
    ```
    cp .backend.env.example .backend.env
    cp .frontend.env.example .frontend.env
    ```
3. Run the deployment:
    ```
    docker compose up -d
    ```
4. Verify that the services are running:
    ```
    docker ps
    ```

### Full Deployment with MongoDB

**This setup includes a MongoDB service within Docker**, making it a self-contained environment.

#### Setup

1. Clone this repo:
    ```
    https://github.com/Aftermath-Archive/docker-deployment
    cd docker-deployment/docker-with-mongodb
    ```
2. Create the necessary .env files based on the examples:
    ```
    cp .backend.env.example .backend.env
    cp .frontend.env.example .frontend.env
    ```
3. Run the deployment:
    ```
    docker compose up -d
    ```
4. Verify that the services are running:
    ```
    docker ps
    ```
5. If you need to connect to MongoDB manually (eg, for debugging):
    ```
    docker exec -it mongodb mongosh
    ```

### Stopping & Removing Containers

To stop and remove all containers, run:

```
docker compose down
```

For the MongoDB version, you may also want to remove the volume:

#### Please be careful with this step as it **deletes all stored data**. 

```
docker compose down -v
```

---

### Future Enhancements

-   Automating deployments with GitHub Actions.
-   Adding Docker secrets for managing environment variables securely.
-   Implementing HTTPS using Traefik or Nginx with SSL certificates.

---

🚀 Now you’re ready to deploy Aftermath Archive! Let us know if you run into any issues. 🎉
