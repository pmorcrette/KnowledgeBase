# Kubernetes Overview

## What is Kubernetes?

Kubernetes (K8s) is an open-source system for automating deployment, scaling, and management of containerized applications.

## Architecture

### Control Plane Components

- **kube-apiserver**: Exposes the Kubernetes API
- **etcd**: Consistent and highly-available key value store for cluster data
- **kube-scheduler**: Watches for newly created Pods with no assigned node
- **kube-controller-manager**: Runs controller processes
- **cloud-controller-manager**: Links cluster into cloud provider's API

### Node Components

- **kubelet**: Agent that runs on each node, ensures containers are running in a Pod
- **kube-proxy**: Network proxy that maintains network rules on nodes
- **Container Runtime**: Software responsible for running containers (e.g., containerd, cri-o)

## Key Concepts

- **Pods**: Smallest deployable units that can be created and managed
- **Deployments**: Manage ReplicaSets for declarative updates to Pods
- **Services**: Abstract way to expose an application running on a set of Pods
- **Namespaces**: Virtual clusters inside a physical cluster
- **Volumes**: Directory accessible to containers in a Pod
- **ConfigMaps & Secrets**: Store configuration data and sensitive information

## Related Documentation

- [Installation Guide](01-installation) - Setting up kubectl and clusters
- [Kubernetes Resources](02-resources) - Core objects explained
- [Networking](03-networking) - Services, Ingress, Network Policies
- [Storage](04-storage) - Volumes and persistent storage
- [Configuration](05-configuration) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling) - Node affinity, taints, resource management
- [Security](07-security) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting) - Debugging and resolving issues
