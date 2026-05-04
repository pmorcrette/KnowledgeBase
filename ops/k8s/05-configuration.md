# Kubernetes Configuration

## ConfigMaps

ConfigMaps allow you to decouple configuration artifacts from image content to keep containerized applications portable.

### Creating ConfigMaps

#### From Literal Values

```bash
kubectl create configmap game-config \
  --from-literal=player_initial_lives=3 \
  --from-literal=ui_properties_file_name=ui.properties
```

#### From Files

```bash
kubectl create configmap game-config \
  --from-file=game.properties \
  --from-file=ui.properties
```

#### From Directory

```bash
kubectl create configmap game-config --from-file=config/
```

### ConfigMap Manifest

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: game-config
data:
  # property-like keys; each key maps to a simple value
  player_initial_lives: "3"
  ui_properties_file_name: "ui.properties"
  game.properties: |
    enemy.types=aliens,monsters
    player.maximum-lives=5
  ui.properties: |
    color.good=purple
    color.bad=yellow
    allow.textmode=true
```

### Using ConfigMaps in Pods

#### As Environment Variables

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: configmap-pod
spec:
  containers:
  - name: game
    image: nginx
    env:
    - name: PLAYER_INITIAL_LIVES
      valueFrom:
        configMapKeyRef:
          name: game-config
          key: player_initial_lives
    - name: UI_PROPERTIES_FILE_NAME
      valueFrom:
        configMapKeyRef:
          name: game-config
          key: ui_properties_file_name
```

#### As Command-Line Arguments

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: cmdargs-pod
spec:
  containers:
  - name: game
    image: nginx
    command: ["/bin/sh", "-c", "echo $(PLAYER_INITIAL_LIVES) $(UI_PROPERTIES_FILE_NAME)"]
    env:
    - name: PLAYER_INITIAL_LIVES
      valueFrom:
        configMapKeyRef:
          name: game-config
          key: player_initial_lives
    - name: UI_PROPERTIES_FILE_NAME
      valueFrom:
        configMapKeyRef:
          name: game-config
          key: ui_properties_file_name
```

#### As Volumes

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: volume-pod
spec:
  containers:
  - name: game
    image: nginx
    volumeMounts:
    - name: config
      mountPath: "/etc/config"
      readOnly: true
  volumes:
  - name: config
    configMap:
      name: game-config
      items:
      - key: game.properties
        path: game.properties
      - key: ui.properties
        path: ui.properties
```

## Secrets

Secrets are similar to ConfigMaps but are specifically intended to hold confidential data, such as passwords, OAuth tokens, and SSH keys.

### Creating Secrets

#### From Literal Values

```bash
kubectl create secret generic db-user-pass \
  --from-literal=username=admin \
  --from-literal=password=SecretPa55word
```

#### From Files

```bash
kubectl create secret generic db-user-pass \
  --from-file=./username.txt \
  --from-file=./password.txt
```

#### From Docker Config

```bash
kubectl create secret docker-registry regcred \
  --docker-server=<your-registry-server> \
  --docker-username=<your-name> \
  --docker-password=<your-pword> \
  --docker-email=<your-email>
```

### Secret Manifest

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-user-pass
type: Opaque
data:
  username: YWRtaW4=  # base64 encoded "admin"
  password: U2VjcmV0UHAzNXdvcmQ=  # base64 encoded "SecretPa55word"
```

### Using Secrets in Pods

#### As Environment Variables

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-pod
spec:
  containers:
  - name: app
    image: nginx
    env:
    - name: USERNAME
      valueFrom:
        secretKeyRef:
          name: db-user-pass
          key: username
    - name: PASSWORD
      valueFrom:
        secretKeyRef:
          name: db-user-pass
          key: password
```

#### As Volumes

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-volume-pod
spec:
  containers:
  - name: app
    image: nginx
    volumeMounts:
    - name: secret-volume
      mountPath: "/etc/secret"
      readOnly: true
  volumes:
  - name: secret-volume
    secret:
      secretName: db-user-pass
      items:
      - key: username
        path: username
      - key: password
        path: password
```

### Secret Types

- **Opaque**: Default type for arbitrary user-defined data
- **kubernetes.io/service-account-token**: Service account token
- **kubernetes.io/dockercfg**: Dockercfg file for Docker registry authentication
- **kubernetes.io/dockerconfigjson**: Docker config JSON file for Docker registry authentication
- **kubernetes.io/basic-auth**: Basic authentication credentials
- **kubernetes.io/ssh-auth**: SSH authentication credentials
- **kubernetes.io/tls**: TLS certificate and key
- **bootstrap.kubernetes.io/token**: Bootstrap token data

## Helm

Helm is a package manager for Kubernetes that helps you install and manage applications on your Kubernetes cluster.

### Helm Concepts

- **Chart**: A Helm package containing all the resource definitions necessary to run an application
- **Release**: An instance of a chart running in a Kubernetes cluster
- **Repository**: A collection of charts

### Installing Helm

```bash
# Using a script
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Using package managers
# macOS
brew install helm
# Linux (Debian/Ubuntu)
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

### Basic Helm Commands

```bash
# Add a repository
helm repo add stable https://charts.helm.sh/stable
helm repo update

# Search for charts
helm search repo wordpress

# Install a chart
helm install my-wordpress stable/wordpress

# List releases
helm list

# Upgrade a release
helm upgrade my-wordpress stable/wordpress

# Rollback a release
helm rollback my-wordpress 1

# Uninstall a release
helm uninstall my-wordpress
```

### Creating a Helm Chart

```bash
# Create a new chart
helm create mychart

# Chart structure
mychart/
  Chart.yaml          # Chart metadata
  values.yaml         # Default configuration values
  charts/             # Dependency charts
  templates/          # Template files
    deployment.yaml
    service.yaml
    _helpers.tpl
```

### Chart.yaml Example

```yaml
apiVersion: v2
name: mychart
description: A Helm chart for Kubernetes
type: application
version: 0.1.0
appVersion: "1.0"
```

### values.yaml Example

```yaml
replicaCount: 1

image:
  repository: nginx
  tag: "stable"
  pullPolicy: IfNotPresent

service:
  type: ClusterIP
  port: 80

resources:
  limits:
    cpu: 100m
    memory: 128Mi
  requests:
    cpu: 100m
    memory: 128Mi
```

### Template Example (templates/deployment.yaml)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "mychart.fullname" . }}
  labels:
    {{- include "mychart.labels" . | nindent 4 }}
spec:
  replicas: {{ .Values.replicaCount }}
  selector:
    matchLabels:
      {{- include "mychart.selectorLabels" . | nindent 6 }}
  template:
    metadata:
      labels:
        {{- include "mychart.selectorLabels" . | nindent 8 }}
    spec:
      containers:
      - name: {{ .Chart.Name }}
        image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
        imagePullPolicy: {{ .Values.image.pullPolicy }}
        ports:
        - containerPort: {{ .Values.service.port }}
          name: http
        resources:
          {{- toYaml .Values.resources | nindent 12 }}
```

## Kustomize

Kustomize lets you customize raw, template-free YAML files for multiple purposes, leaving the original YAML untouched and usable as is.

### Kustomize Concepts

- **Base**: A set of resources that you want to customize
- **Overlay**: A set of patches and other customizations applied to a base
- **kustomization.yaml**: File that defines how to customize resources

### Installing Kustomize

```bash
# Using Go install
go install sigs.k8s.io/kustomize/kustomize/v5@latest

# Using package managers
# macOS
brew install kustomize
# Linux (Debian/Ubuntu)
sudo apt-get install kustomize
```

### Basic Kustomize Structure

```
/app
  /base
    deployment.yaml
    service.yaml
    kustomization.yaml
  /overlays
    /development
      kustomization.yaml
    /production
      kustomization.yaml
```

### Base kustomization.yaml

```yaml
resources:
  - deployment.yaml
  - service.yaml
```

### Deployment.yaml (base)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 2
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

### Service.yaml (base)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: ClusterIP
```

### Development Overlay kustomization.yaml

```yaml
resources:
  - ../../base
patchesStrategicMerge:
  - deployment.patch.yaml
```

### deployment.patch.yaml (development overlay)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 1
  template:
    spec:
      containers:
      - name: nginx
        image: nginx:stable
```

### Production Overlay kustomization.yaml

```yaml
resources:
  - ../../base
patchesStrategicMerge:
  - deployment.patch.yaml
  - service.patch.yaml
```

### deployment.patch.yaml (production overlay)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 5
  template:
    spec:
      containers:
      - name: nginx
        image: nginx:1.21
        resources:
          limits:
            cpu: 500m
            memory: 512Mi
          requests:
            cpu: 250m
            memory: 256Mi
```

### service.patch.yaml (production overlay)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  type: LoadBalancer
```

### Using Kustomize

```bash
# Build the base
kustomize build ./app/base

# Build an overlay
kustomize build ./app/overlays/development
kustomize build ./app/overlays/production

# Apply to cluster
kubectl apply -k ./app/overlays/development
kubectl apply -k ./app/overlays/production
```

## Related Documentation

- [Overview](00-overview) - Kubernetes architecture and concepts
- [Installation](01-installation) - Setting up kubectl and clusters
- [Resources](02-resources) - Core Kubernetes objects (Pods, Deployments, Services)
- [Networking](03-networking) - Services, Ingress, Network Policies
- [Storage](04-storage) - Volumes and persistent storage
- [Scheduling](06-scheduling) - Node affinity, taints, resource management
- [Security](07-security) - RBAC, Pod Security, image scanning
- [Monitoring & Logging](08-monitoring-logging) - Metrics, logging, observability
- [Troubleshooting](09-troubleshooting) - Debugging and resolving issues
