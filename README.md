
# MobSF Helm Chart

This repository provides a Helm chart for deploying [MobSF (Mobile Security Framework)](https://github.com/MobSF/Mobile-Security-Framework-MobSF) in a Kubernetes cluster.

## Features

- Deploys MobSF as a Kubernetes Deployment.
- Exposes MobSF via a Kubernetes Service (ClusterIP).
- Optional Ingress for HTTP/HTTPS access with TLS support.
- Persistent storage using PersistentVolumeClaim (PVC).
- Fully configurable via `values.yaml`.

## Requirements

- Kubernetes cluster (1.19+)
- Helm (3.0+)
- Ingress controller (e.g., NGINX) if Ingress is enabled
- TLS certificates (optional for HTTPS)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Dorison/mobsf-helm-kubernetes.git
   cd mobsf-helm-chart
   ```

2. Modify `values.yaml` to set your desired configuration (e.g., domain name, storage class).

3. Install the chart:
   ```bash
   helm install mobsf ./mobsf -n mobsf --create-namespace
   ```

4. Verify the deployment:
   ```bash
   kubectl get all -n mobsf
   ```

## Configuration

You can configure the chart by modifying the `values.yaml` file. Key options include:

- **replicaCount**: Number of replicas for the MobSF Deployment.
- **image**: MobSF Docker image repository and tag.
- **service**: Type and port of the Service.
- **ingress**: Domain, paths, and TLS configuration.
- **persistence**: Persistent storage settings.

Refer to the `values.yaml` file for the complete list of configurable options.

## Uninstallation

To remove the MobSF deployment, run:
```bash
helm uninstall mobsf -n mobsf
```

## Structure

```
mobsf/
  ├── Chart.yaml        # Metadata for the Helm chart
  ├── values.yaml       # Default configuration values
  └── templates/        # Kubernetes resource templates
      ├── deployment.yaml
      ├── service.yaml
      ├── ingress.yaml
      ├── pvc.yaml
```

## Contributing

Contributions are welcome! Please submit a pull request or open an issue for improvements or bug fixes.
