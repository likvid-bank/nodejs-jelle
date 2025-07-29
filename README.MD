# 🚀 Your Application with AKS deployment

[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=flat&logo=kubernetes&logoColor=white)](https://kubernetes.io/)

> Your containerized application with automated deployment to Azure Kubernetes Service (AKS) via GitHub Actions.

## 📋 Overview

This repository contains your containerized application configured for automatic deployment to Azure Kubernetes Service (AKS). The deployment pipeline is powered by:

- **🔄 GitHub Actions CI/CD**: Automated build and deployment workflows
- **🐳 Azure Container Registry**: Secure container image storage
- **☁️ Azure Kubernetes Service**: Scalable container orchestration
- **🏗️ Infrastructure as Code**: Kubernetes manifests generated dynamically
- **🔒 Secure Authentication**: Service principal-based AKS access

## 🎯 Features

- ✅ **Automated Docker builds** with Azure Container Registry integration
- ✅ **One-click deployments** triggered by git pushes
- ✅ **Kubernetes deployment manifests** generated automatically
- ✅ **Resource management** with CPU and memory limits
- ✅ **Secure image pulls** with configured secrets
- ✅ **Branch-based deployments** for different environments

## 🚀 Quick Start

### Prerequisites

- [ ] Access to this GitHub repository with push permissions
- [ ] Your application code with a working Dockerfile
- [ ] Azure Container Registry and AKS cluster (pre-configured via secrets)

### Making Changes

1. **Clone the repository**:
   ```bash
   git clone https://github.com/likvid-bank/aks-starterkit-template.git
   cd aks-starterkit-template
   ```

2. **Update your application code** and ensure your Dockerfile is properly configured

3. **Commit and push your changes**:
   ```bash
   git add .
   git commit -m "feat: update application code"
   git push origin main
   ```

4. **Monitor the deployment** in the [GitHub Actions tab](../../actions)

## 🔄 Deployment Pipeline

### How It Works

The deployment process is fully automated through GitHub Actions:

1. **Trigger**: Push commits to the configured branch
2. **Build**: Docker image is built from your Dockerfile
3. **Push**: Image is tagged with commit SHA and pushed to Azure Container Registry
4. **Deploy**: Kubernetes deployment manifest is generated and applied to AKS

### Deployment Process

```bash
git add .
git commit -m "feat: your feature description"
git push origin main  # or your configured branch
```

**What happens automatically:**

- ✅ **Docker Build**: Your application is containerized using the Dockerfile
- ✅ **Image Registry**: Container image is pushed to Azure Container Registry with commit SHA tag
- ✅ **Kubernetes Deployment**: A deployment manifest is generated with:
  - 1 replica by default
  - Resource limits: 64Mi memory, 100m CPU
  - Resource requests: 48Mi memory, 25m CPU
  - Automatic image pull secrets configuration
- ✅ **AKS Deployment**: Application is deployed to your AKS namespace

### Deployment Configuration

The GitHub Actions workflow automatically creates a Kubernetes deployment with these specifications:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: your-app
  namespace: your-namespace
spec:
  replicas: 1
  template:
    spec:
      containers:
        - name: your-app
          image: your-registry/your-app:commit-sha
          resources:
            requests:
              memory: "48Mi"
              cpu: "25m"
            limits:
              memory: "64Mi"
              cpu: "100m"
```

## 📊 Monitoring Your Deployments

### GitHub Actions Dashboard

Monitor all deployments in the [GitHub Actions tab](../../actions):

- 🟢 **Successful deployments** show with green checkmarks
- 🔴 **Failed deployments** show with red X marks and detailed error logs
- 📊 **Build logs** show Docker build process and kubectl deployment steps
- ⏱️ **Deployment history** tracks all releases with commit SHAs

### Deployment Logs

Each workflow run provides detailed logs for:

1. **Checkout**: Repository code retrieval
2. **ACR Login**: Authentication with Azure Container Registry
3. **Build and Push**: Docker image build and registry push
4. **Deploy to AKS**: Kubernetes manifest application and deployment status

### AKS Access

Your application is deployed to your pre-configured AKS namespace. Access details are managed through the repository secrets and KUBECONFIG.

## 📚 Additional Resources

- [Azure Kubernetes Service Documentation](https://docs.microsoft.com/en-us/azure/aks/)
- [Docker Best Practices](https://docs.docker.com/develop/dev-best-practices/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [meshStack Documentation](https://docs.meshcloud.io/)

---

**Ready to deploy?** 🚀 Make your changes and push to start the automated deployment process!
