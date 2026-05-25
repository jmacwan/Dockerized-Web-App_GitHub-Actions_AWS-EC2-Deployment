**1. Purpose**

A Dockerized Node.js web app that automatically:

Runs CI (build + test)

Builds a Docker image

Pushes it to GitHub Container Registry (GHCR)

Deploys to an AWS EC2 instance via SSH + Docker Compose

**2. Tech Stack**

Node.js + Express (simple web server)

Docker (containerization)

GitHub Actions (CI/CD automation)

GHCR (container registry)

AWS EC2 (deployment target)

Docker Compose (runs app on EC2)

**3. Repository Structure**

Code
my-app/
  src/index.js        → Express server
  package.json        → App metadata
  Dockerfile          → Build container image
  docker-compose.yml  → Run container on EC2
  .github/workflows/ci-cd.yml → CI/CD pipeline

**4. CI Pipeline (GitHub Actions)**

Triggered on:

Push to main

Pull requests

Steps:

Checkout code

Install Node.js

Install dependencies

Run tests

**5. CD Pipeline (GitHub Actions)**

Runs after CI passes.

Steps:

Build Docker image

Push image to GHCR

Copy docker-compose.yml to EC2

SSH into EC2

Pull latest image

Restart container with zero downtime

**6. Required GitHub Secrets**

EC2_HOST → EC2 public IP

EC2_SSH_KEY → private SSH key

GITHUB_TOKEN → auto‑generated

(Optional) AWS credentials

**7. Deployment Behavior**

EC2 always pulls the latest image

Docker Compose restarts the service

App updates with no downtime
