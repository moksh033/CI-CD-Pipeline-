# CI/CD Pipeline with Docker & GitHub Actions

A simple web application automated with a Continuous Integration & Continuous Delivery (CI/CD) pipeline using Docker and GitHub Actions.

## 🚀 Features

- **Web App**: Lightweight single-page login interface served via Nginx Alpine.
- **Dockerized**: Containerized for consistency across all environments.
- **GitHub Actions CI/CD**:
  - Automatically triggers on every push and pull request to `main`.
  - Builds the Docker image.
  - Spins up a test container and verifies HTTP response (`curl --fail http://localhost:8080/`).
  - Tags and pushes the verified image to Docker Hub (`latest` and commit SHA).

## 🐳 Running Locally with Docker

1. **Build the image**:
   ```bash
   docker build -t login-app:test .
   ```

2. **Run the container**:
   ```bash
   docker run -d --name login-test -p 8080:80 login-app:test
   ```

3. **Open in browser**:
   Visit [http://localhost:8080](http://localhost:8080)

4. **Stop and cleanup**:
   ```bash
   docker stop login-test
   docker rm login-test
   ```

## ⚙️ GitHub Secrets Required for Deployment

To enable pushing to Docker Hub in GitHub Actions, add these secrets to your repository settings (`Settings` > `Secrets and variables` > `Actions`):
- `DOCKERHUB_USERNAME`: Your Docker Hub username.
- `DOCKERHUB_TOKEN`: Your Docker Hub Personal Access Token (PAT).
