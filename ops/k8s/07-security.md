# Kubernetes Security

## RBAC (Role-Based Access Control)

RBAC allows you to regulate access to Kubernetes resources based on roles assigned to users or groups.

### Roles and ClusterRoles

- **Role**: Grants permissions within a specific namespace
- **ClusterRole**: Grants permissions cluster-wide or for specific resources across all namespaces

#### Role Example

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""] # "" indicates the core API group
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

#### ClusterRole Example

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: node-reader
rules:
- apiGroups: [""]
  resources: ["nodes"]
  verbs: ["get", "watch", "list"]
```

### RoleBindings and ClusterRoleBindings

- **RoleBinding**: Grants permissions to users/groups within a namespace
- **ClusterRoleBinding**: Grants permissions cluster-wide

#### RoleBinding Example

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: jane
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

#### ClusterRoleBinding Example

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: read-nodes
subjects:
- kind: User
  name: jane
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: node-reader
  apiGroup: rbac.authorization.k8s.io
```

## Pod Security Standards

Pod Security Standards define three levels of security for Pods:

- **Privileged**: Unrestricted, allows all security features
- **Baseline**: Minimally restrictive, prevents known privilege escalations
- **Restricted**: Heavily restricted, follows Pod hardening best practices

### Enabling Pod Security Standards

```bash
# Label namespace to enforce baseline standard
kubectl label namespace default pod-security.kubernetes.io/enforce=baseline

# Check policy violations
kubectl label namespace default pod-security.kubernetes.io/audit=baseline
kubectl label namespace default pod-security.kubernetes.io/warn=baseline
```

## Image Scanning

Scan container images for vulnerabilities before deploying to Kubernetes.

### Popular Tools

- **Trivy**: Comprehensive vulnerability scanner for containers, Kubernetes, code repositories
- **Clair**: Static analysis of vulnerabilities in container images
- **Grype**: Vulnerability scanner for container images and filesystems
- **Anchore Engine**: Deep analysis of container images

### Trivy Example

```bash
# Install Trivy
brew install trivy  # macOS
# Or download binary from GitHub releases

# Scan an image
trivy image nginx:latest

# Scan Kubernetes cluster
trivy k8s --report summary cluster
```

## Secrets Management Best Practices

- Avoid storing secrets in ConfigMaps or environment variables in plain text
- Use Kubernetes Secrets with encryption at rest enabled
- Consider external secret stores (HashiCorp Vault, AWS Secrets Manager, etc.)
- Use secret rotation policies
- Limit access to secrets using RBAC

## Service Accounts

Service accounts provide an identity for processes that run in Pods to access the Kubernetes API.

### Managing Service Accounts

```bash
# Create a service account
kubectl create serviceaccount my-sa

# Assign to a Pod
apiVersion: v1
kind: Pod
metadata:
  name: sa-pod
spec:
  serviceAccountName: my-sa
  containers:
  - name: app
    image: nginx
```

## Security Contexts

Security contexts define privilege and access control settings for Pods and containers.

### Pod Security Context Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: security-context-pod
spec:
  securityContext:
    runAsUser: 1000
    runAsGroup: 3000
    fsGroup: 2000
  containers:
  - name: app
    image: nginx
    securityContext:
      allowPrivilegeEscalation: false
      capabilities:
        drop: ["ALL"]
```

## Network Policies

Control traffic flow between Pods and namespaces. See [Networking](03-networking.md) for detailed examples.

## Admission Controllers

Admission controllers intercept requests to the Kubernetes API server after authentication and authorization.

### Common Admission Controllers

- **PodSecurity**: Enforces Pod Security Standards
- **ResourceQuota**: Enforces resource quotas
- **LimitRanger**: Enforces resource limits
- **MutatingWebhookConfiguration**: Modify requests
- **ValidatingWebhookConfiguration**: Validate requests

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Resources](02-resources.md) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking.md) - Services, Ingress, Network Policies
- [Storage](04-storage.md) - Volumes and persistent storage
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling.md) - Node affinity, taints, resource management
- [Monitoring & Logging](08-monitoring-logging.md) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
