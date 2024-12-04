# Keycloak Deployment on Kubernetes

This repository contains Kubernetes manifests for deploying **Keycloak**, an open-source Identity and Access Management (IAM) solution. The configuration uses an **Nginx Ingress Controller** to expose Keycloak to the public internet securely.

---

## Prerequisites

1. A Kubernetes cluster.
2. `kubectl` configured to interact with your cluster.
3. **Nginx Ingress Controller** installed in your cluster.
4. Domain name (e.g., `domain.com`) pointing to your ingress controller's IP address.

---

## Deployment Overview

This setup includes:

- **Deployment**: Runs Keycloak in development mode (`start-dev`).
- **Service**: Exposes Keycloak within the cluster.
- **Ingress**: Provides external access to Keycloak via the configured domain.

---

## Files

- **`deployment.yaml`**: Defines the Keycloak Deployment, Service, and Ingress resources.

---

## Keycloak Configuration

The Keycloak container is configured with the following environment variables:

| Variable                 | Value          | Description                                     |
|--------------------------|----------------|-------------------------------------------------|
| `KEYCLOAK_ADMIN`         | `admin`        | Default admin username.                        |
| `KEYCLOAK_ADMIN_PASSWORD`| `admin`        | Default admin password.                        |
| `KC_HOSTNAME`            | `https://domain.com` | External hostname for Keycloak.               |
| `KC_PROXY`               | `edge`         | Proxy setting for handling SSL termination.    |

---

## Steps to Deploy

1. Clone this repository:

   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. Apply the manifests:

   ```bash
   kubectl apply -f deployment.yaml
   ```

3. Verify that all resources are created:

   ```bash
   kubectl get all
   ```

4. Access Keycloak at `https://domain.com`. Use the admin credentials (`admin/admin`) to log in.

---