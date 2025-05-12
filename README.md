# Bootstrap Kubernetes Infrastructure with FluxCD 

This repository contains infrastructure-as-code for deploying and managing a Kubernetes cluster on Proxmox using FluxCD and GitOps principles.

## Overview

The project leverages [FluxCD](https://fluxcd.io/) to automate the deployment and reconciliation of Kubernetes resources. The infrastructure is modularized and organized into several components, each managed via Kustomize and Helm.

## Structure

- **clusters/**  
  Contains cluster-specific configuration.  
  - `proxmox-local/` — main cluster definition, including FluxCD sync and infrastructure composition.

- **infrastructure/**  
  Shared infrastructure components, split into:
  - `network/` — Cilium CNI deployment for advanced networking.
  - `ingress/` — Ingress-NGINX controller for external access.
  - `storage/` — Piraeus Operator for distributed storage.

## Key Components

- **FluxCD**: GitOps tool for continuous delivery.
- **Cilium**: Advanced networking and security for Kubernetes.
- **Ingress-NGINX**: Ingress controller for HTTP/HTTPS routing.
- **Piraeus Operator**: Manages distributed storage with LINSTOR.

## Getting Started

1. **Install FluxCD** on your management workstation and bootstrap it to your cluster.
2. **Clone this repository** and review the cluster and infrastructure manifests.
3. **Apply the manifests** using FluxCD or push changes to your Git repository to trigger reconciliation.

## Folder Details

- `infrastructure/network/cilium.yaml`: Deploys Cilium CNI via Helm.
- `infrastructure/ingress/ingress.yaml`: Deploys Ingress-NGINX via Helm, with Cilium integration.
- `infrastructure/storage/piraeus-operator.yaml`: Deploys Piraeus Operator for storage management.
- `clusters/proxmox-local/infrastructure.yaml`: Orchestrates the application of infrastructure components in the correct order using FluxCD Kustomizations.

## Requirements

- Kubernetes cluster (e.g., on Proxmox)
- FluxCD
- kubectl
- Helm

## License

[MIT](LICENSE) 