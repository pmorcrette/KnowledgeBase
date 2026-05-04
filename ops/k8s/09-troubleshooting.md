# Kubernetes Troubleshooting

## Common Debugging Commands

### Basic Status Checks

```bash
# List all pods in all namespaces
kubectl get pods --all-namespaces

# Get detailed pod information
kubectl describe pod <pod-name>

# View pod logs
kubectl logs <pod-name>
kubectl logs <pod-name> -c <container-name>  # multi-container pod
kubectl logs <pod-name> --previous  # logs from previous container instance

# Stream logs
kubectl logs -f <pod-name>

# View events
kubectl get events --sort-by='.lastTimestamp'
```

### Advanced Debugging

```bash
# Execute command in a container
kubectl exec -it <pod-name> -- /bin/sh

# Copy files to/from container
kubectl cp <pod-name>:/path/to/file ./local-file
kubectl cp ./local-file <pod-name>:/path/to/file

# Debug with ephemeral containers (Kubernetes 1.23+)
kubectl debug -it <pod-name> --image=busybox --target=<pod-name>

# Check node status
kubectl get nodes
kubectl describe node <node-name>

# Check component status
kubectl get componentstatuses
```

## Common Errors and Solutions

### CrashLoopBackOff

**Cause**: Container keeps crashing after starting.

**Debug Steps**:
1. Check logs: `kubectl logs <pod-name> --previous`
2. Check events: `kubectl get events --field-selector involvedObject.name=<pod-name>`
3. Check resource limits: `kubectl describe pod <pod-name>` (look for OOMKilled)
4. Verify container image and command

### ImagePullBackOff / ErrImagePull

**Cause**: Kubernetes can't pull the container image.

**Solutions**:
1. Check image name and tag: `kubectl describe pod <pod-name>`
2. Verify image exists in registry
3. Check image pull secrets: `kubectl get secrets`
4. Test pulling image manually: `docker pull <image-name>`

### Pod Stuck in Pending

**Cause**: No node available to schedule the pod.

**Debug Steps**:
1. Check node resources: `kubectl top nodes`
2. Check pod resource requests: `kubectl describe pod <pod-name>`
3. Check node taints: `kubectl describe nodes | grep Taint`
4. Verify storage availability if using PVCs

### Node NotReady

**Cause**: Node is unreachable or kubelet is not running.

**Solutions**:
1. SSH to node and check kubelet status: `systemctl status kubelet`
2. Check node resources (disk, memory, PID pressure)
3. Verify network connectivity between node and control plane
4. Check node logs: `journalctl -u kubelet`

### PVC Pending

**Cause**: No suitable PV available or storage class issues.

**Debug Steps**:
1. Check PVC status: `kubectl describe pvc <pvc-name>`
2. Check available PVs: `kubectl get pv`
3. Verify storage class exists: `kubectl get storageclass`
4. Check provisioner logs if using dynamic provisioning

## Debugging Workflow

1. **Identify the problem**: `kubectl get pods --all-namespaces` to see overall status
2. **Inspect the pod**: `kubectl describe pod <pod-name>` for events and conditions
3. **Check logs**: `kubectl logs <pod-name>` and `kubectl logs <pod-name> --previous`
4. **Verify dependencies**: Check services, configmaps, secrets the pod depends on
5. **Check node health**: `kubectl describe node <node-name>` if pod is scheduled
6. **Review resource usage**: `kubectl top pods` and `kubectl top nodes`

## Useful Labels for Filtering

```bash
# Get pods by label
kubectl get pods -l app=nginx

# Get pods by namespace
kubectl get pods -n kube-system

# Get pods with specific status
kubectl get pods --field-selector=status.phase=Running
```

## Related Documentation

- [Overview](00-overview) - Kubernetes architecture and concepts
- [Installation](01-installation) - Setting up kubectl and clusters
- [Resources](02-resources) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking) - Services, Ingress, Network Policies
- [Storage](04-storage) - Volumes and persistent storage
- [Configuration](05-configuration) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling) - Node affinity, taints, resource management
- [Security](07-security) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging) - Metrics, logging, observability
