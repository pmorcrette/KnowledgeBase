# Kubernetes Networking

## Services

As covered in the [Resources](02-resources.md) document, Services enable network access to a set of Pods.

### Service Types Recap

- **ClusterIP**: Internal cluster IP (default)
- **NodePort**: Exposes service on each Node's IP at a static port
- **LoadBalancer**: Exposes service externally using cloud provider's load balancer
- **ExternalName**: Maps service to a DNS name (without using proxy)

### Headless Services

Setting `clusterIP: None` creates a headless service, which does not load-balance or proxy requests. It returns the IPs of the Pods associated with the service, useful for StatefulSets.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: headless-service
spec:
  selector:
    app: myapp
  clusterIP: None
  ports:
  - port: 80
    targetPort: 80
```

## Ingress

Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource.

### Ingress Controller

An Ingress controller is required to fulfill the Ingress. Popular controllers include:
- NGINX Ingress Controller
- Traefik
- HAProxy
- Istio (as an Ingress gateway)
- Contour
- Ambassador
- Kong

### Simple Ingress Example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: example-service
            port:
              number: 80
```

### TLS Termination

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: tls-ingress
  annotations:
    nginx.ingress.kubernetes.io/ssl-redirect: "true"
spec:
  tls:
  - hosts:
    - example.com
    secretName: example-tls-secret
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: example-service
            port:
              number: 80
```

## Network Policies

NetworkPolicy specifies how groups of Pods are allowed to communicate with each other and other network endpoints.

By default, Pods are non-isolated; they accept traffic from any source. NetworkPolicy allows you to isolate Pods.

### Network Policy Example

#### Deny All Ingress Traffic to a Namespace

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
spec:
  podSelector: {}  # selects all pods in the namespace
  policyTypes:
  - Ingress
```

#### Allow Traffic from Specific Namespace

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-from-namespace
spec:
  podSelector:
    matchLabels:
      role: db
  policyTypes:
  - Ingress
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          name: frontend
```

#### Allow Traffic on Specific Port

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-traffic-on-port
spec:
  podSelector:
    matchLabels:
      app: web
  policyTypes:
  - Ingress
  ingress:
  - ports:
    - protocol: TCP
      port: 8080
    from:
    - podSelector: {}
```

## DNS in Kubernetes

Kubernetes creates DNS records for Services and Pods.

### Service DNS
- A service named `my-service` in namespace `my-namespace` has DNS entry: `my-service.my-namespace.svc.cluster.local`
- Pods in the same namespace can resolve it as `my-service`
- Pods in different namespaces can use the full DNS

### Pod DNS
- By default, a Pod's DNS policy is set to `ClusterFirst`.
- Pod hostname: `<pod-name>.<namespace>.svc.cluster.local`
- However, note that Pods get a DNS A record only if they have a hostname set or if the `publishNotReadyAddresses` is set to true on the Service.

## CNI (Container Network Interface)

Kubernetes uses CNI plugins for networking. Popular CNI plugins include:
- Calico
- Flannel
- Weave Net
- Canal (Calico + Flannel)
- Cilium
- Romana
- Contiv

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Resources](02-resources.md) - Core Kubernetes objects (Pods, Deployments, Services)
- [Storage](04-storage.md) - Volumes and persistent storage
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling.md) - Node affinity, taints, resource management
- [Security](07-security.md) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging.md) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
