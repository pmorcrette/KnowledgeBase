# Kubernetes Installation

## Installing kubectl

kubectl is the command-line tool for interacting with Kubernetes clusters.

### macOS

```bash
# Using Homebrew
brew install kubectl

# Or download directly
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

### Linux

```bash
# Using snap (Ubuntu)
sudo snap install kubectl --classic

# Or download binary
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

### Windows

```powershell
# Using Chocolatey
choco install kubernetes-cli

# Or using Scoop
scoop install kubectl

# Or download MSI from Kubernetes website
```

## Setting Up a Cluster

### Local Development Options

#### Kind (Kubernetes IN Docker)

```bash
# Install kind
# macOS
brew install kind
# Linux
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create a cluster
kind create cluster

# Verify
kubectl cluster-info
```

#### Minikube

```bash
# Install minikube
# macOS
brew install minikube
# Linux
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Start cluster
minikube start

# Verify
kubectl cluster-info
```

#### Docker Desktop

- Enable Kubernetes in Docker Desktop Preferences > Kubernetes
- Click "Apply & Restart"

### Cloud Providers

#### Google Kubernetes Engine (GKE)

```bash
# Install gcloud CLI
# Then authenticate
gcloud auth login

# Set project
gcloud config set project PROJECT_ID

# Create cluster
gcloud container clusters create my-cluster --num-nodes=3

# Get credentials
gcloud container clusters get-credentials my-cluster
```

#### Amazon Elastic Kubernetes Service (EKS)

```bash
# Install eksctl and awscli
# macOS
brew install eksctl awscli
# Linux (eksctl)
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin

# Create cluster
eksctl create cluster --name my-cluster --region us-east-1 --nodegroup-name standard-workers --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed

# Update kubeconfig
aws eks update-kubeconfig --name my-cluster --region us-east-1
```

#### Azure Kubernetes Service (AKS)

```bash
# Install Azure CLI
# macOS
brew install azure-cli
# Linux (Debian/Ubuntu)
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

# Login
az login

# Create resource group
az group create --name myResourceGroup --location eastus

# Create AKS cluster
az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 3 --enable-addons monitoring --generate-ssh-keys

# Get credentials
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

## Verifying Installation

```bash
# Check kubectl version
kubectl version --client

# Check cluster info
kubectl cluster-info

# List nodes
kubectl get nodes

# Run a test pod
kubectl run nginx --image=nginx --restart=Never
kubectl get pods
kubectl delete pod nginx
```

## Related Documentation

- [Overview](00-overview) - Kubernetes architecture and concepts
- [Resources](02-resources) - Core Kubernetes objects
- [Networking](03-networking) - Services, Ingress, Network Policies
- [Storage](04-storage) - Volumes and persistent storage
- [Configuration](05-configuration) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling) - Node affinity, taints, resource management
- [Security](07-security) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting) - Debugging and resolving issues
