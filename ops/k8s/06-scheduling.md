# Kubernetes Scheduling

## What is Scheduling?

Scheduling in Kubernetes refers to the process of assigning newly created Pods to nodes. The kube-scheduler is the default scheduler that watches for unscheduled Pods and assigns them to nodes based on resource requirements, policies, and constraints.

## Resource Requests and Limits

Containers can specify resource requests (minimum required) and limits (maximum allowed) for CPU and memory.

### Resource Specification

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: resource-pod
spec:
  containers:
  - name: app
    image: nginx
    resources:
      requests:
        cpu: "250m"    # 250 millicores
        memory: "128Mi" # 128 mebibytes
      limits:
        cpu: "500m"
        memory: "256Mi"
```

### Key Concepts

- **Requests**: Minimum resources the container is guaranteed
- **Limits**: Maximum resources the container can use
- **QoS Classes**:
  - **Guaranteed**: Equal requests and limits for all containers
  - **Burstable**: At least one container has requests lower than limits
  - **BestEffort**: No requests or limits specified

## Node Affinity

Node affinity allows you to constrain which nodes your Pod can be scheduled on based on node labels.

### Required Node Affinity

Pods will only schedule on nodes that meet the requirements.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: required-affinity-pod
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: zone
            operator: In
            values:
            - us-east-1a
            - us-east-1b
  containers:
  - name: app
    image: nginx
```

### Preferred Node Affinity

Scheduler tries to find nodes that meet the preferences but will schedule elsewhere if not available.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: preferred-affinity-pod
spec:
  affinity:
    nodeAffinity:
      preferredDuringSchedulingIgnoredDuringExecution:
      - weight: 1
        preference:
          matchExpressions:
          - key: disktype
            operator: In
            values:
            - ssd
  containers:
  - name: app
    image: nginx
```

## Taints and Tolerations

Taints allow nodes to repel Pods that do not tolerate them. Tolerations allow Pods to be scheduled on nodes with matching taints.

### Adding Taints to Nodes

```bash
# Add a taint to a node
kubectl taint nodes node1 key=value:NoSchedule

# Remove a taint
kubectl taint nodes node1 key=value:NoSchedule-
```

### Taint Effects

- **NoSchedule**: Pods won't be scheduled on the node unless they tolerate the taint
- **PreferNoSchedule**: Scheduler tries to avoid scheduling on the node
- **NoExecute**: New pods won't be scheduled, and existing pods will be evicted if they don't tolerate the taint

### Pod with Tolerations

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: toleration-pod
spec:
  tolerations:
  - key: "key"
    operator: "Equal"
    value: "value"
    effect: "NoSchedule"
  containers:
  - name: app
    image: nginx
```

## Pod Affinity and Anti-Affinity

### Pod Affinity

Schedule Pods close to other Pods (e.g., same zone for low latency).

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-affinity
spec:
  affinity:
    podAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
      - labelSelector:
          matchLabels:
            app: cache
        topologyKey: topology.kubernetes.io/zone
  containers:
  - name: app
    image: nginx
```

### Pod Anti-Affinity

Schedule Pods away from other Pods (e.g., spread replicas across nodes).

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-anti-affinity
spec:
  affinity:
    podAntiAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
      - labelSelector:
          matchLabels:
            app: nginx
        topologyKey: kubernetes.io/hostname
  containers:
  - name: app
    image: nginx
```

## Pod Priority and Preemption

Pod Priority indicates the importance of a Pod relative to other Pods. The scheduler uses priority to schedule higher-priority Pods before lower-priority ones. If no space is available, the scheduler may preempt (evict) lower-priority Pods to make room.

### PriorityClass Example

```yaml
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: high-priority
value: 1000000
globalDefault: false
description: "This priority class should be used for high priority pods only."
```

### Using PriorityClass in Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: high-priority-pod
spec:
  priorityClassName: high-priority
  containers:
  - name: app
    image: nginx
```

## Node Selector

The simplest form of node selection, using node labels.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: node-selector-pod
spec:
  nodeSelector:
    disktype: ssd
  containers:
  - name: app
    image: nginx
```

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Resources](02-resources.md) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking.md) - Services, Ingress, Network Policies
- [Storage](04-storage.md) - Volumes and persistent storage
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Security](07-security.md) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging.md) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
