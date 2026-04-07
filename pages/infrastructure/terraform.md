---
title: Terraform Module
visible_when:
  entitlements:
    - terraformModuleEnabled
---

{{#if entitlements.terraformModuleEnabled}}

# Purrfect Match Terraform Module

Deploy and manage Purrfect Match infrastructure using Terraform.

<Note>
This module provisions the required infrastructure and deploys Purrfect Match via Helm. It handles cluster provisioning, namespace creation, and chart installation.
</Note>

## Quick Start

<CodeBlock language="hcl" title="main.tf">
module "purrfect_match" {
  source  = "purrfectproductions/purrfect-match/kubernetes"
  version = "~> 1.0"

  namespace    = "purrfect-match"
  domain       = "adopt.example.com"
  license_id   = var.license_id

  # Application settings
  app_replicas = 2

  # Database
  postgresql_enabled = true
  postgresql_size    = "10Gi"

  # Matching engine
  matching_engine_enabled    = true
  matching_engine_model_size = "standard"

  # Object storage for cat photos
  minio_enabled = true
  minio_size    = "20Gi"

  # Ingress
  ingress_class_name = "nginx"
  tls_secret_name    = "purrfect-match-tls"
}
</CodeBlock>

## Variables

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `namespace` | string | `"purrfect-match"` | Kubernetes namespace for the deployment |
| `domain` | string | -- | Domain name for the Purrfect Match portal |
| `license_id` | string | -- | Your Purrfect Match license ID |
| `app_replicas` | number | `2` | Number of application replicas |
| `postgresql_enabled` | bool | `true` | Deploy bundled PostgreSQL |
| `postgresql_size` | string | `"10Gi"` | PostgreSQL PVC size |
| `postgresql_external_host` | string | `""` | External PostgreSQL host (when `postgresql_enabled` is `false`) |
| `postgresql_external_port` | number | `5432` | External PostgreSQL port |
| `matching_engine_enabled` | bool | `true` | Enable the matching engine |
| `matching_engine_model_size` | string | `"standard"` | Model size: `standard` or `large` |
| `minio_enabled` | bool | `true` | Deploy bundled MinIO for cat photos |
| `minio_size` | string | `"20Gi"` | MinIO PVC size |
| `ingress_class_name` | string | `"nginx"` | IngressClass name |
| `tls_secret_name` | string | `""` | TLS Secret name for Ingress |

## Outputs

| Output | Description |
|--------|-------------|
| `namespace` | The namespace where Purrfect Match is deployed |
| `endpoint` | The URL to access Purrfect Match |
| `helm_release_name` | The Helm release name |
| `helm_release_version` | The deployed chart version |

## Example: External Database

<CodeBlock language="hcl" title="external-db.tf">
module "purrfect_match" {
  source  = "purrfectproductions/purrfect-match/kubernetes"
  version = "~> 1.0"

  namespace  = "purrfect-match"
  domain     = "adopt.example.com"
  license_id = var.license_id

  postgresql_enabled       = false
  postgresql_external_host = "db.example.com"
  postgresql_external_port = 5432
}
</CodeBlock>

<CommandBlock label="Deploy with Terraform">
terraform init
terraform plan
terraform apply
</CommandBlock>

{{/if}}
