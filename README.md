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

## Commands Used in This Project
# -------------------------------
✅ Jenkins Agent Docker Image
# -------------------------------
cd jenkins-agent

 Build agent image
docker build -t jenkins-agent-custom .

# Load agent image into Minikube
minikube image load jenkins-agent-custom

# Verify image loaded into Minikube
minikube image ls | grep jenkins-agent-custom


# -------------------------------
# ✅ Jenkins Master Docker Image
# -------------------------------
cd ../jenkins-master

# Build Jenkins master image manually from WAR file
docker build -t jenkins-master-manual .

# Run Jenkins master container
docker run -d -p 8080:8080 --name jenkins-master jenkins-master-manual

# View Jenkins initial admin password
docker exec jenkins-master cat /root/.jenkins/secrets/initialAdminPassword


# -------------------------------
# ✅ Kubernetes Commands
# -------------------------------

# View pods to confirm Kubernetes is running
kubectl get pods

# Watch Jenkins agents spin up dynamically
kubectl get pods --watch

# (Optional) Delete completed agent pods manually
kubectl delete pod <pod-name>


# -------------------------------
# ✅ Git Commands for GitHub Upload
# -------------------------------

# Initialize Git repository
git init

# Remove nested .git folders if needed
rm -rf jenkins-agent/.git
rm -rf jenkins-master/.git

# Add files and commit
git add .
git commit -m "Initial commit with Jenkins master and agent setup"

# Set main branch
git branch -M main

# Set remote origin (use your actual GitHub repo URL)
git remote add origin https://github.com/your-username/your-repo-name.git

# Push to GitHub
git push -u origin main

