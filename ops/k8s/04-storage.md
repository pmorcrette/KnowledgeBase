# Kubernetes Storage

## Volumes

A Volume is a directory, possibly with some data in it, which is accessible to containers in a Pod.

### Volume Types

- **emptyDir**: Empty directory that is created when a Pod is assigned to a node
- **hostPath**: Mounts a file or directory from the host node's filesystem
- **gcePersistentDisk**: Google Compute Engine Persistent Disk
- **awsElasticBlockStore**: AWS Elastic Block Store (EBS)
- **azureDisk**: Microsoft Azure Disk
- **azureFile**: Microsoft Azure File
- **photonPersistentDisk**: Photon Controller persistent disk
- **portworxVolume**: Portworx Volume
- **scaleIO**: ScaleIO Volume
- **storageos**: StorageOS Volume
- **vsphereVolume**: vSphere VMDK Volume

### PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs)

PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes.

PersistentVolumeClaim (PVC) is a request for storage by a user.

#### PV Example

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-example
spec:
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: slow
  hostPath:
    path: /mnt/data
```

#### PVC Example

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-example
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
  storageClassName: slow
```

#### Using a PVC in a Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-with-pvc
spec:
  containers:
  - name: app
    image: nginx
    volumeMounts:
    - name: data
      mountPath: /usr/share/nginx/html
  volumes:
  - name: data
    persistentVolumeClaim:
      claimName: pvc-example
```

## StorageClasses

StorageClasses allow administrators to describe the "classes" of storage they offer. Different classes might map to quality-of-service levels, backup policies, or arbitrary policies determined by the cluster administrators.

### StorageClass Example

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: standard
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2
  zone: us-east-1a
reclaimPolicy: Retain
mountOptions:
  - debug
volumeBindingMode: Immediate
```

### Dynamic Provisioning

When a PVC references a StorageClass, the control plane dynamically provisions a PV for the user.

## Volume Snapshots

Volume snapshots represent a point-in-time copy of a volume.

### VolumeSnapshotClass Example

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshotClass
metadata:
  name: csi-hostpath-snapclass
driver: hostpath.csi.k8s.io
deletionPolicy: Delete
```

### VolumeSnapshot Example

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: new-snapshot-test
spec:
  volumeSnapshotClassName: csi-hostpath-snapclass
  source:
    persistentVolumeClaimName: pvc-example
```

## CSI (Container Storage Interface)

CSI is a standard for exposing arbitrary block and file storage systems to containerized workloads on Kubernetes.

### Benefits of CSI

- Enables storage vendors to write a plugin once and have it work across multiple container orchestrators
- Allows Kubernetes to use third-party storage solutions without adding code to the core Kubernetes

## Common Storage Use Cases

### Databases

- Use PersistentVolumes with appropriate access modes (ReadWriteOnce for single node, ReadWriteMany for shared)
- Consider local SSDs for performance-critical workloads
- Use snapshots for backups

### Shared Filesystems

- Use ReadWriteMany access modes (e.g., NFS, cloud file services like AWS EFS, Azure Files, GCP Filestore)
- Suitable for content management systems, shared logs, etc.

### Ephemeral Storage

- Use emptyDir for temporary storage (scratch space, caching)
- Data is lost when the Pod is removed from the node

## Related Documentation

- [Overview](00-overview.md) - Kubernetes architecture and concepts
- [Installation](01-installation.md) - Setting up kubectl and clusters
- [Resources](02-resources.md) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking.md) - Services, Ingress, Network Policies
- [Configuration](05-configuration.md) - ConfigMaps, Secrets, Helm, Kustomize
- [Scheduling](06-scheduling.md) - Node affinity, taints, resource management
- [Security](07-security.md) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging.md) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting.md) - Debugging and resolving issues
