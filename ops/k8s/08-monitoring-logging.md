# Kubernetes Monitoring & Logging

## Metrics with Metrics Server

Metrics Server provides resource metrics (CPU, memory) for nodes and Pods, enabling `kubectl top` commands.

### Installing Metrics Server

```bash
# Install metrics-server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

# Verify installation
kubectl get pods -n kube-system | grep metrics-server
```

### Using Metrics Server

```bash
# View node metrics
kubectl top nodes

# View pod metrics
kubectl top pods
kubectl top pods --all-namespaces
```

## Prometheus for Monitoring

Prometheus is an open-source monitoring and alerting toolkit widely used with Kubernetes.

### Installing Prometheus (Using Helm)

```bash
# Add Prometheus Helm repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# Install Prometheus
helm install prometheus prometheus-community/prometheus

# Verify
kubectl get pods -l app=prometheus
```

### Accessing Prometheus

```bash
# Port-forward to access Prometheus UI
kubectl port-forward svc/prometheus-server 9090:80
```

## Grafana for Visualization

Grafana is an open-source visualization and analytics software for time-series data.

### Installing Grafana (Using Helm)

```bash
# Add Grafana Helm repo
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# Install Grafana
helm install grafana grafana/grafana

# Get admin password
kubectl get secret grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

# Port-forward
kubectl port-forward svc/grafana 3000:80
```

## Logging in Kubernetes

### Native Logging

Containers write logs to stdout/stderr, which are captured by the container runtime and accessible via `kubectl logs`.

```bash
# View logs for a pod
kubectl logs my-pod

# View logs for a specific container in a multi-container pod
kubectl logs my-pod -c my-container

# Stream logs
kubectl logs -f my-pod

# View previous logs (if container restarted)
kubectl logs my-pod --previous
```

### Centralized Logging with Fluentd

Fluentd is a unified logging layer that collects, processes, and forwards logs.

#### Fluentd Setup with Elasticsearch and Kibana (ELK Stack)

```bash
# Install Elasticsearch
helm repo add elastic https://helm.elastic.co
helm repo update
helm install elasticsearch elastic/elasticsearch

# Install Kibana
helm install kibana elastic/kibana

# Install Fluentd
helm repo add fluent https://fluent.github.io/helm-charts
helm install fluentd fluent/fluentd
```

### Loki for Log Aggregation

Grafana Loki is a horizontally scalable, multi-tenant log aggregation system inspired by Prometheus.

#### Installing Loki with Helm

```bash
# Add Loki Helm repo
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update

# Install Loki
helm install loki grafana/loki-stack
```

## Monitoring Best Practices

- Set up alerting for critical metrics (CPU, memory, disk, pod failures)
- Use dashboards for quick visualization of cluster health
- Monitor both infrastructure and application metrics
- Implement log retention policies
- Use structured logging in applications

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Resources](02-resources.md) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking.md) - Services, Ingress, Network Policies
- [Storage](04-storage.md) - Volumes and persistent storage
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling.md) - Node affinity, taints, resource management
- [Security](07-security.md) - RBAC, Pod Security, image scanning
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
