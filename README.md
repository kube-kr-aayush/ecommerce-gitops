Overview

This repository contains the GitOps configuration for deploying a full-stack e-commerce application on Kubernetes using Argo CD.

It acts as the single source of truth for the desired state of the Kubernetes cluster.
All deployments, services, and ingress configurations are managed declaratively from this repository.

1- Purpose of This Repository

 --  Implement GitOps-based Continuous Deployment

 -- Separate application code from deployment configuration

 -- Enable declarative, auditable, and reproducible Kubernetes deployments

Allow Argo CD to automatically sync cluster state from Git

CI builds images.
CD happens via GitOps (this repo).

Tech Stack

Kubernetes

Argo CD (GitOps CD)

NGINX Ingress Controller

Docker Images (built via CI)

AWS EC2–based environment (for cluster hosting)

Repository Structure
ecommerce-gitops/
├── backend/
│   ├── deployment.yaml
│   └── service.yaml
│
├── frontend/
│   ├── deployment.yaml
│   └── service.yaml
│
├── mongo/
│   ├── deployment.yaml
│   └── service.yaml
│
└── ingress/
    └── ingress.yaml

Description

backend/ → Kubernetes manifests for backend API

frontend/ → Kubernetes manifests for frontend UI

mongo/ → MongoDB deployment and service

ingress/ → NGINX ingress rules for external access

Each component is managed independently and synced via Argo CD.

GitOps Deployment Flow
Application Code Repo
        ↓
      CI (Jenkins)
        ↓
  Docker Images Built
        ↓
  GitOps Repo Updated
        ↓
      Argo CD
        ↓
   Kubernetes Cluster


Argo CD continuously monitors this repository

Any change to manifests triggers an automatic sync

Cluster state always matches Git state

Kubernetes Objects Used

Deployments

Services (ClusterIP)

Ingress

ConfigMaps / Secrets (basic usage)

All resources are defined declaratively in YAML.

Why GitOps?

GitOps was chosen to:

Keep deployment state version-controlled

Enable easy rollback via Git history

Improve deployment visibility and auditability

Avoid direct manual changes to the cluster

Environment Notes

The Kubernetes cluster was hosted on an AWS EC2–based setup

Local clusters were used for learning and testing

This repository is intended for learning and demonstration purposes

Ownership & Scope

Web Application (Frontend & Backend): Original Project Owner

GitOps, Kubernetes Manifests & Deployment: Aayush

This repository focuses purely on deployment and infrastructure, not application feature development.

Status

✔ GitOps configuration complete
✔ Argo CD sync verified
✔ Kubernetes deployment stable
