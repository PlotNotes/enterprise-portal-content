---
title: System Requirements
---

# System Requirements

Review the following requirements before installing Purrfect Match.

## Kubernetes Requirements

{{#if entitlements.isHelmInstallEnabled}}

<Prerequisites title="Helm Installation Prerequisites">
- Kubernetes **1.28** or later
- Helm **3.10** or later
- `kubectl` configured with cluster access
- A default StorageClass for persistent volumes
- Cluster-admin privileges for the installing user
</Prerequisites>

### Minimum Resource Requirements

| Resource | Minimum |
|----------|---------|
| CPU | 2 cores |
| Memory | 2 GB |
| Disk | 10 GB available |

{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}

## Linux (Embedded Cluster) Requirements

<Prerequisites title="Linux Prerequisites">
- Linux operating system (Ubuntu 20.04+, RHEL 8+, or CentOS 8+)
- x86-64 architecture
- systemd-based init system
- Root access or `sudo` privileges
</Prerequisites>

### Minimum Resource Requirements

| Resource | Minimum |
|----------|---------|
| CPU | 2 cores |
| Memory | 2 GB |
| Disk | 40 GB available |

### Port Requirements

The following ports must be available:

<Accordion title="Ports used by local processes">

These ports must be available for local processes (no firewall openings needed):

- **2379/TCP** -- etcd client
- **7443/TCP** -- k0s API
- **9099/TCP** -- Calico health
- **10248/TCP** -- kubelet health
- **10257/TCP** -- kube-controller-manager
- **10259/TCP** -- kube-scheduler

</Accordion>

<Accordion title="Ports for node communication (multi-node)">

Create firewall openings between nodes for these ports:

- **2380/TCP** -- etcd peer
- **4789/UDP** -- VXLAN overlay
- **6443/TCP** -- Kubernetes API
- **9091/TCP** -- Cilium health
- **9443/TCP** -- k0s controller
- **10249/TCP** -- kube-proxy metrics
- **10250/TCP** -- kubelet API
- **10256/TCP** -- kube-proxy health

</Accordion>

<Accordion title="Admin Console and Local Artifact Mirror">

- **30000/TCP** -- Admin Console (configurable with `--admin-console-port`)
- **50000/TCP** -- Local Artifact Mirror (configurable during installation)

</Accordion>

{{/if}}

<Warning>
Ensure all requirements are met before proceeding with installation. Insufficient resources may cause instability.
</Warning>
