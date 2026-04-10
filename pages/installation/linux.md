---
title: Linux Installation
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# Install Purrfect Match on Linux

Install Purrfect Match on a Linux server using Embedded Cluster v3. This option bundles Kubernetes and all dependencies into a single installer — no cluster management required.

<Prerequisites>
- Ubuntu 20.04+, RHEL 8+, or CentOS 8+
- 2 CPUs, 2 GB RAM, 40 GB disk minimum
- Root access or `sudo` privileges
- Review the [full system requirements](requirements) for port and OS details
</Prerequisites>

---

<InstallStep stepNumber={1} title="Name Your Instance">

Give this Purrfect Match instance a name to identify it in your environment.

<InstanceName title="Name Your Purrfect Match Instance" />

</InstallStep>

<InstallStep stepNumber={2} title="Download the Installer">

Select your version and download the installation assets.

<VersionSelector installType="linux" />

<LinuxInstallAssets />

</InstallStep>

<InstallStep stepNumber={3} title="Extract and Install">

SSH into your target machine, transfer the downloaded archive, then extract and run:

<CommandBlock label="Extract and install">
tar -xvzf purrfect-unstable.tgz
sudo ./purrfect install --license license.yaml
</CommandBlock>

The installer will:
1. Run host preflight checks
2. Install Kubernetes (k0s) and infrastructure components
3. Run application preflight checks
4. Deploy Purrfect Match and all dependencies

<Note>
For headless (non-interactive) installations, add the `--headless` and `--installer-password` flags:

`sudo ./purrfect install --license license.yaml --headless --installer-password YOUR_PASSWORD -y`
</Note>

</InstallStep>

<InstallStep stepNumber={4} title="Access the Installer UI">

Once the installer bootstraps, it will display a URL to complete the setup. Open it in your browser to configure the application.

The installer UI runs on port **30080** by default and uses a self-signed TLS certificate.

<Tip>
You can provide your own TLS certificate during installation with the `--tls-cert` and `--tls-key` flags.
</Tip>

</InstallStep>

<InstallStep stepNumber={5} title="Verify the Installation">

After the installation completes, verify all pods are running:

<CommandBlock label="Verify installation">
sudo purrfect shell -c "k0s kubectl get pods -A"
</CommandBlock>

All pods should show `Running` status. The Purrfect Match application is accessible on port **8000** of the host.

</InstallStep>

---

## Upgrading

To upgrade to a new version, download the latest installer and run:

<CommandBlock label="Upgrade">
tar -xvzf purrfect-unstable.tgz
sudo ./purrfect upgrade --license license.yaml
</CommandBlock>

The upgrade preserves all data and configuration.

---

## Next Steps

<Tip title="You're Live!">
Your Purrfect Match instance is installed and ready. Here's what to explore next:
</Tip>

- **[Checking for Updates](../updates/checking)** — Stay current with new releases
- **[Linux Support Bundles](../operations/bundles/linux)** — Generate diagnostics if needed
- **[FAQ](../support/faq)** — Common questions and troubleshooting tips
- **[Contact Support](../support/contact)** — We're here if you need a helping paw
