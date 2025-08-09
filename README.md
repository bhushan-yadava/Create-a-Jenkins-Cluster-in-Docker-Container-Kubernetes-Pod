# Jenkins Cluster (Manual Setup with Docker + Kubernetes)

This project demonstrates how to manually install Jenkins in Docker (without pre-built images) and use Kubernetes pods as Jenkins agents.

## Structure

- `jenkins-master/`: Jenkins master Dockerfile (manual WAR install)
- `jenkins-agent/`: Custom Kubernetes agent image (no pre-built image)
- `Jenkinsfile`: Sample pipeline that runs in Kubernetes agent

## Steps

1. Build Jenkins master image and run on Docker
2. Load agent image into Minikube
3. Configure Jenkins Kubernetes plugin
4. Run pipelines that dynamically launch agent pods

