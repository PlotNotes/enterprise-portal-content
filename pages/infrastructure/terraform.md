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

## Registry Authentication

Add the following to your `.terraformrc` to authenticate with the Purrfect Match module registry:

<CommandBlock label="~/.terraformrc">
credentials "proxy.purrfectproductions.com" {
  token = "{{ license.id }}"
}
</CommandBlock>

## Quick Start

<CommandBlock label="main.tf">
module "purrfect_match" {
  source  = "proxy.purrfectproductions.com/{{ app.slug }}/purrfect-terraform/github"
  version = "1.0.0"

}
</CommandBlock>

<CommandBlock label="Deploy">
terraform init
terraform plan
terraform apply
</CommandBlock>

## Configuration Reference

### Required Variables

| Variable | Type | Description |
|----------|------|-------------|

### Deployment Options

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `namespace` | string | `"purrfect"` | Kubernetes namespace |
| `release_name` | string | `"purrfect-match"` | Helm release name |
| `chart_version` | string | `"1.0.17"` | Chart version to deploy |
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

<CommandBlock label="external-db.tf">
module "purrfect_match" {
  source  = "proxy.purrfectproductions.com/{{ app.slug }}/purrfect-terraform/github"
  version = "1.0.0"


  embedded_database    = false
  external_db_host     = "db.example.com"
  external_db_user     = "purrfect"
  external_db_password = var.db_password
  external_db_name     = "purrfect"
}
</CommandBlock>

{{/if}}
