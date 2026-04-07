---
title: System Requirements
---

# System Requirements

Review these requirements before installing Purrfect Match. Getting the foundation right means a smoother ride to your first adoption match.

---

{{#if entitlements.isHelmInstallEnabled}}

## Helm (Kubernetes) Requirements

<Prerequisites title="Helm Prerequisites">
- Kubernetes **1.28** or later
- Helm **3.10** or later
- `kubectl` configured with cluster access
- A default StorageClass for persistent volumes
- Cluster-admin privileges for the installing user
</Prerequisites>

### Hardware Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| CPU | 2 cores | 4 cores |
| Memory | 2 GB | 4 GB |
| Disk | 10 GB available | 40 GB available |

<Tip title="Right-Size Your Cluster">
The recommended specs support production workloads with the matching engine processing up to 500 concurrent profiles. For larger shelter networks, consider scaling horizontally with additional replicas.
</Tip>

<Warning title="Unsupported Kubernetes Distributions">
The following distributions are **not supported** for production deployments:

- **Docker Desktop Kubernetes** — Resource limits and networking behavior differ significantly from production clusters
- **MicroK8s** — Known incompatibilities with the embedded storage and networking stack
- **Minikube** — Suitable for local evaluation only; not recommended for any production or staging use

Use a managed Kubernetes service (EKS, GKE, AKS) or a standard upstream distribution (kubeadm, k0s, RKE2) for production.
</Warning>

### Supported Kubernetes Versions

| Version | Status |
|---------|--------|
| 1.28.x | Supported |
| 1.29.x | Supported |
| 1.30.x | Supported |
| 1.31.x | Supported |
| 1.32.x | Supported (latest) |

{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}

## Linux (Embedded Cluster) Requirements

<Prerequisites title="Linux Prerequisites">
- Linux operating system (Ubuntu 20.04+, RHEL 8+, or CentOS 8+)
- x86-64 architecture
- systemd-based init system
- Root access or `sudo` privileges
- Internet access during installation (or air gap bundle for offline installs)
</Prerequisites>

### Hardware Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| CPU | 2 cores | 4 cores |
| Memory | 2 GB | 8 GB |
| Disk | 40 GB available | 100 GB available |

<Tip title="Plan for Growth">
Shelters with 1,000+ cat profiles and active photo storage should target the recommended specs or higher. Disk usage grows with the number of cat photos and adoption records stored locally.
</Tip>

<Warning title="Unsupported Configurations">
The following are **not supported**:

- **32-bit (i386/ARM)** architectures
- **Non-systemd init systems** (e.g., OpenRC, SysVinit)
- **WSL / Windows Subsystem for Linux** — Use the Helm installation on a proper Kubernetes cluster instead
- **Container-based Linux** (e.g., LXC/LXD containers) — Nested container runtimes cause conflicts with the embedded Kubernetes layer
</Warning>

### Supported Operating Systems

| Distribution | Versions |
|-------------|----------|
| Ubuntu | 20.04, 22.04, 24.04 |
| RHEL | 8.x, 9.x |
| CentOS | 8 Stream, 9 Stream |
| Rocky Linux | 8.x, 9.x |
| Amazon Linux | 2023 |

### Port Requirements

The following ports must be available on the host:

<Accordion title="Local Process Ports (no firewall changes needed)">

These ports are used by local processes and do not require firewall openings:

| Port | Protocol | Service |
|------|----------|---------|
| 2379 | TCP | etcd client |
| 7443 | TCP | k0s API |
| 9099 | TCP | Calico health |
| 10248 | TCP | kubelet health |
| 10257 | TCP | kube-controller-manager |
| 10259 | TCP | kube-scheduler |

</Accordion>

<Accordion title="Node Communication Ports (multi-node clusters)">

Open these ports between nodes in multi-node deployments:

| Port | Protocol | Service |
|------|----------|---------|
| 2380 | TCP | etcd peer |
| 4789 | UDP | VXLAN overlay |
| 6443 | TCP | Kubernetes API |
| 9091 | TCP | Cilium health |
| 9443 | TCP | k0s controller |
| 10249 | TCP | kube-proxy metrics |
| 10250 | TCP | kubelet API |
| 10256 | TCP | kube-proxy health |

</Accordion>

<Accordion title="Admin Console & Local Artifact Mirror">

| Port | Protocol | Service | Notes |
|------|----------|---------|-------|
| 30000 | TCP | Admin Console | Configurable with `--admin-console-port` |
| 50000 | TCP | Local Artifact Mirror | Configurable during installation |

</Accordion>

{{/if}}

---

<Note title="Before You Install">
Ensure all requirements are met before proceeding. Insufficient resources may lead to unstable behavior — and nobody wants a cat-astrophic deployment. When in doubt, go with the recommended specs.
</Note>
