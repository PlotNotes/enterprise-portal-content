---
title: Terraform Module
visible_when:
  entitlements:
    - terraformModuleEnabled
---

{{#if entitlements.terraformModuleEnabled}}

# Purrfect Match Terraform Module

Deploy Purrfect Match to any Kubernetes cluster using Terraform.

<Note>
This module provisions a namespace, configures registry credentials, and deploys Purrfect Match via Helm. Requires a valid Purrfect Match license.
</Note>

## Prerequisites

- Terraform >= 1.5.0
- A Kubernetes cluster with `kubectl` access
- Helm and Kubernetes providers configured
- Your Purrfect Match license ID

## Registry Authentication

Configure your `.terraformrc` to authenticate with the Purrfect Match registry:

<CodeBlock language="hcl" title="~/.terraformrc">
credentials "{{ registry.proxyDomain }}" {
  token = "{{ license.id }}"
}
</CodeBlock>

## Quick Start

<CodeBlock language="hcl" title="main.tf">
module "purrfect_match" {
  source  = "{{ registry.proxyDomain }}/purrfect/purrfect-terraform/github"
  version = "1.0.0"

  registry_username = "{{ license.id }}"
  registry_password = "{{ license.id }}"
  admin_email       = "admin@example.com"
}
</CodeBlock>

<CodeBlock language="bash" title="Deploy">
terraform init
terraform plan
terraform apply
</CodeBlock>

## Configuration Reference

### Required Variables

| Variable | Type | Description |
|----------|------|-------------|
| `registry_username` | string | Your license ID (for pulling images) |
| `registry_password` | string | Your license ID (for pulling images) |
| `admin_email` | string | Admin email for notifications |

### Deployment Options

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `namespace` | string | `"purrfect"` | Kubernetes namespace |
| `release_name` | string | `"purrfect-match"` | Helm release name |
| `chart_version` | string | `"{{ release.version }}"` | Chart version to deploy |
| `service_type` | string | `"ClusterIP"` | Service type (ClusterIP, NodePort, LoadBalancer) |
| `service_port` | number | `8000` | Service port |

### Database

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `embedded_database` | bool | `true` | Deploy embedded PostgreSQL |
| `external_db_host` | string | `""` | External PostgreSQL host |
| `external_db_port` | string | `"5432"` | External PostgreSQL port |
| `external_db_user` | string | `""` | External PostgreSQL user |
| `external_db_password` | string | `""` | External PostgreSQL password |
| `external_db_name` | string | `"purrfect"` | External database name |

### Features

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `allow_add_cats` | bool | `true` | Allow adding cats to catalog |
| `dark_mode` | bool | `false` | Enable dark mode theme |
| `max_cats_per_page` | number | `12` | Cats displayed per page (1-100) |

### Ingress

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `ingress_enabled` | bool | `false` | Enable ingress |
| `ingress_class` | string | `""` | Ingress class name |
| `ingress_host` | string | `""` | Ingress hostname |

## Outputs

| Output | Description |
|--------|-------------|
| `namespace` | Deployment namespace |
| `release_name` | Helm release name |
| `release_version` | Deployed chart version |
| `service_endpoint` | In-cluster service endpoint |

## Example: External Database

<CodeBlock language="hcl" title="external-db.tf">
module "purrfect_match" {
  source  = "{{ registry.proxyDomain }}/purrfect/purrfect-terraform/github"
  version = "1.0.0"

  registry_username = var.license_id
  registry_password = var.license_id
  admin_email       = "admin@example.com"

  embedded_database    = false
  external_db_host     = "db.example.com"
  external_db_user     = "purrfect"
  external_db_password = var.db_password
  external_db_name     = "purrfect"
}
</CodeBlock>

## Example: Full Configuration

<CodeBlock language="hcl" title="full.tf">
module "purrfect_match" {
  source  = "{{ registry.proxyDomain }}/purrfect/purrfect-terraform/github"
  version = "1.0.0"

  registry_username = var.license_id
  registry_password = var.license_id
  admin_email       = "ops@example.com"

  namespace    = "purrfect-prod"
  service_type = "LoadBalancer"

  ingress_enabled = true
  ingress_class   = "nginx"
  ingress_host    = "cats.example.com"

  allow_add_cats    = true
  dark_mode         = false
  max_cats_per_page = 24
}
</CodeBlock>

{{/if}}
