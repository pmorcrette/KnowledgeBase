# Kubernetes Resources

## Pods

Pods are the smallest deployable units in Kubernetes. A Pod represents a single instance of a running process in your cluster and can contain one or more containers.

### Pod Manifest Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

### Key Pod Concepts

- **Containers**: One or more containers that share storage, network, and lifecycle
- **Volumes**: Shared storage accessible to containers in the Pod
- **Labels**: Key-value pairs for organizing and selecting objects
- **Annotations**: Non-identifying metadata for tools and libraries
- **Restart Policies**: Always, OnFailure, Never

## Deployments

Deployments provide declarative updates for Pods and ReplicaSets. They manage the creation, scaling, and updating of Pod instances.

### Deployment Manifest Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

### Deployment Strategies

- **RollingUpdate**: Update Pods gradually with max surge and max unavailable
- **Recreate**: Kill all existing Pods before creating new ones

### Managing Deployments

```bash
# Create deployment
kubectl create -f nginx-deployment.yaml

# Scale deployment
kubectl scale deployment/nginx-deployment --replicas=5

# Update image
kubectl set image deployment/nginx-deployment nginx=nginx:1.21

# Rollback
kubectl rollout undo deployment/nginx-deployment

# Status
kubectl rollout status deployment/nginx-deployment
```

## Services

Services define a logical set of Pods and a policy by which to access them, enabling loose coupling between dependent Pods.

### Service Types

- **ClusterIP** (default): Internal cluster IP
- **NodePort**: Exposes service on each Node's IP at a static port
- **LoadBalancer**: Exposes service externally using cloud provider's load balancer
- **ExternalName**: Maps service to a DNS name

### Service Manifest Examples

#### ClusterIP Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

#### NodePort Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-nodeport
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30080
  type: NodePort
```

### Service Discovery

- **Environment Variables**: Kubernetes injects service environment variables into Pods
- **DNS**: Automatic DNS entries for services (e.g., `my-service.my-namespace.svc.cluster.local`)

## Related Resources

- **ReplicaSet**: Ensures a specified number of pod replicas are running
- **StatefulSet**: Manages stateful applications with stable network identities
- **DaemonSet**: Ensures a copy of a Pod runs on each node
- **Job**: Runs one or more Pods to completion
- **CronJob**: Creates Jobs on a repeating schedule

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Networking](03-networking.md) - Services, Ingress, Network Policies
- [Storage](04-storage.md) - Volumes and persistent storage
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling.md) - Node affinity, taints, resource management
- [Security](07-security.md) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging.md) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
