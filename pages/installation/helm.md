---
title: Helm Installation
visible_when:
  entitlements:
    - isHelmInstallEnabled
---

# Install Purrfect Match with Helm

Deploy Purrfect Match to your existing Kubernetes cluster using Helm.

<Prerequisites>
- Kubernetes **1.28** or later
- Helm **3.10** or later
- `kubectl` configured with cluster access
- A default StorageClass for persistent volumes
</Prerequisites>

## Configure Your Installation

Select your deployment preferences below. The install commands will update automatically.

<KubernetesDistribution />
<NetworkAvailability installType="helm" />
<RegistryAccess />
<VersionSelector installType="helm" />

## Install

<HelmInstallAssets />

<InstanceName title="Name Your Purrfect Match Instance" />

## Verify Installation

After installation completes, verify that all pods are running:

<CommandBlock label="Verify pods">
kubectl get pods -n purrfect-match
</CommandBlock>

<Tip>
See the [Helm Chart Reference](helm-chart-reference) for a full list of configurable values.
</Tip>

## Next Steps

- Review the [Helm Chart Reference](helm-chart-reference) to customize your deployment
- Check [Updates](../updates/checking) to stay current with the latest releases
- Visit the [FAQ](../support/faq) for common questions
