---
title: Linux Installation
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# Install Purrfect Match on Linux

Install Purrfect Match on a Linux server using Embedded Cluster. This option bundles Kubernetes and all dependencies into a single installer.

<Prerequisites>
- Ubuntu 20.04+, RHEL 8+, or CentOS 8+
- 2 CPUs, 2 GB RAM, 40 GB disk minimum
- Root access or `sudo` privileges
- See [full requirements](requirements) for port and system details
</Prerequisites>

## Configure Your Installation

<NetworkAvailability installType="linux" />
<VersionSelector installType="linux" />

## Install

SSH into your target machine and run the following command as root or with `sudo`:

<LinuxInstallAssets />

## Verify Installation

Once the installer completes, it will display the Admin Console URL. Open it in your browser to complete setup.

<CommandBlock label="Verify installation">
# Check that all pods are running
kubectl get pods -A

# Access the Admin Console
echo "Admin Console: https://$(hostname):30000"
</CommandBlock>

<InstanceName title="Name Your Purrfect Match Instance" />

## Next Steps

- Complete initial setup via the Admin Console
- Check [Updates](../updates/checking) to stay current with new releases
- Visit the [FAQ](../support/faq) for common questions
