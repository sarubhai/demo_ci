# Demo Continuous Integration & Deployment to Kubernetes
This repository demonstrates Continuous Integration (CI) and Continuous Deployment (CD) for a sample Python web application microservice. The application is containerized using Docker, and GitHub Actions is used for automating the CI/CD pipeline. The repository is designed to work in conjunction with the [Demo CD repository](https://github.com/sarubhai/demo_cd), which contains the Kubernetes Manifests.

## Overview
This project is a simple Python web application built using Flask. The primary focus of this repository is to showcase a CI/CD pipeline that automates the build, test, and deployment processes using Docker and GitHub Actions.

The application is containerized using Docker. The Dockerfile sets up the environment, installs dependencies, and runs the Flask application inside a container.

### Project Structure
```
demo_ci/
├── .github/
│   └── workflows/
│       └── ci-cd.yml        # GitHub Actions CI/CD pipeline configuration
├── app.py                   # Main application file (Flask web server)
├── Dockerfile               # Dockerfile for containerizing the application
└── requirements.txt         # Python dependencies
```

#### Build & Run the Docker container locally
```
docker compose up -d
```
The application will be accessible at http://localhost:5000/api/products


#### Build & Push the Docker image to Dockerhub
```
docker login -u sauravm
docker build -t sauravm/demo-cicd:manualBuild_v1 .

# Test Image
# docker run -d -p 5000:5000 sauravm/demo-cicd:manualBuild_v1

docker push sauravm/demo-cicd:manualBuild_v1
```

After the [Manifest files](https://github.com/sarubhai/demo_cd) are deployed in Kubernetes cluster using either kubectl or [Argo CD](https://argo-cd.readthedocs.io/en/stable/user-guide/best_practices/#separating-config-vs-source-code-repositories)
#### Update hosts file
```
sudo vi /etc/hosts

# Append the server entry
127.0.0.1	python-api.local
```
The application will be accessible at https://python-api.local/api/products

