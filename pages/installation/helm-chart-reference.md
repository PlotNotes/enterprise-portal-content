---
title: Helm Chart Reference
visible_when:
  entitlements:
    - isHelmInstallEnabled
---

# Helm Chart Reference

Reference documentation for the Purrfect Match Helm chart.

**Chart location:** `oci://proxy.purrfectproductions.com/purrfect/purrfect-match`

## Global Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `global.domain` | string | `""` | The domain name for the Purrfect Match portal |
| `global.storageClass` | string | `""` | StorageClass to use for persistent volumes. Uses cluster default if empty |

## Application Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `app.replicas` | integer | `2` | Number of application server replicas |
| `app.image.tag` | string | `""` | Override the application image tag (defaults to chart appVersion) |
| `app.resources.requests.cpu` | string | `"500m"` | CPU request for application pods |
| `app.resources.requests.memory` | string | `"512Mi"` | Memory request for application pods |
| `app.resources.limits.cpu` | string | `"2000m"` | CPU limit for application pods |
| `app.resources.limits.memory` | string | `"2Gi"` | Memory limit for application pods |

## Database Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `postgresql.enabled` | boolean | `true` | Deploy the bundled PostgreSQL instance |
| `postgresql.auth.database` | string | `"purrfectmatch"` | Name of the application database |
| `postgresql.auth.username` | string | `"purrfect"` | Database username |
| `postgresql.auth.existingSecret` | string | `""` | Name of an existing Secret containing the database password |
| `postgresql.primary.persistence.size` | string | `"10Gi"` | Size of the PostgreSQL data volume |
| `postgresql.externalHost` | string | `""` | Hostname of an external PostgreSQL server (when `postgresql.enabled` is `false`) |
| `postgresql.externalPort` | integer | `5432` | Port of the external PostgreSQL server |

## Ingress Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `ingress.enabled` | boolean | `true` | Create an Ingress resource |
| `ingress.className` | string | `"nginx"` | IngressClass name |
| `ingress.hostname` | string | `""` | Hostname for the Ingress rule |
| `ingress.tls.enabled` | boolean | `true` | Enable TLS on the Ingress |
| `ingress.tls.secretName` | string | `""` | Name of the TLS Secret |
| `ingress.annotations` | object | `{}` | Additional Ingress annotations |

## Matching Engine Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `matchingEngine.enabled` | boolean | `true` | Enable the cat-adopter matching engine |
| `matchingEngine.modelSize` | string | `"standard"` | Model size: `standard` or `large` |
| `matchingEngine.replicas` | integer | `1` | Number of matching engine replicas |
| `matchingEngine.resources.requests.cpu` | string | `"250m"` | CPU request for the matching engine |
| `matchingEngine.resources.requests.memory` | string | `"256Mi"` | Memory request for the matching engine |

## Object Storage Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `minio.enabled` | boolean | `true` | Deploy the bundled MinIO instance for cat photos and documents |
| `minio.persistence.size` | string | `"20Gi"` | Size of the MinIO data volume |
| `minio.externalEndpoint` | string | `""` | Endpoint for external S3-compatible storage (when `minio.enabled` is `false`) |
| `minio.externalBucket` | string | `""` | Bucket name for external storage |

<Note>
For a complete list of all chart values, run:

<CommandBlock>
helm show values oci://proxy.purrfectproductions.com/purrfect/purrfect-match
</CommandBlock>
</Note>

## Example: External Database with Custom Domain

<CodeBlock language="yaml" title="custom-values.yaml">
global:
  domain: adopt.example.com

postgresql:
  enabled: false
  externalHost: db.example.com
  auth:
    existingSecret: purrfect-db-credentials

ingress:
  hostname: adopt.example.com
  tls:
    enabled: true
    secretName: adopt-tls

app:
  replicas: 3
</CodeBlock>

<CommandBlock label="Install with custom values">
helm install purrfect-match oci://proxy.purrfectproductions.com/purrfect/purrfect-match -f custom-values.yaml
</CommandBlock>
