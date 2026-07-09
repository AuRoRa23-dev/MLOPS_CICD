# CI/CD Demo Web App

This project is a simple static web page served by Nginx in a Docker container.

## Files
- Dockerfile: builds the Nginx-based container image
- nginx/default.conf: Nginx configuration
- .github/workflows/ci-cd.yml: GitHub Actions pipeline for build, test, and deploy to Docker Hub

## Local run
```bash
docker build -t cicd-demo:local .
docker run --rm -p 8080:80 cicd-demo:local
```
Then open http://localhost:8080

## GitHub Actions setup
Create these repository secrets in GitHub:
- DOCKERHUB_USERNAME
- DOCKERHUB_TOKEN

The workflow will:
1. Build the Docker image
2. Run a smoke test inside a temporary container
3. Log in to Docker Hub
4. Push the image with both commit-based and latest tags
