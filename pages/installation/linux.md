---
title: Linux Installation
visible_when:
  entitlements:
    - isEmbeddedClusterDownloadEnabled
---

# Install Purrfect Match on Linux

Install Purrfect Match on a Linux server using Embedded Cluster. This option bundles Kubernetes and all dependencies into a single installer — no cluster management required.

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

<InstallStep stepNumber={2} title="Configure Your Installation">

Select your installation preferences below.

<NetworkAvailability installType="linux" />
<VersionSelector installType="linux" />

</InstallStep>

<Tabs defaultActiveTab={0}>
<Tab title="Online Installation">

<InstallStep stepNumber={3} title="Run the Installer">

SSH into your target machine and run the following command as root or with `sudo`:

<LinuxInstallAssets />

The installer will download all required components and set up Kubernetes automatically.

</InstallStep>

<InstallStep stepNumber={4} title="Complete Setup via Admin Console">

Once the installer completes, it will display the Admin Console URL. Open it in your browser to finish configuration.

<CommandBlock label="Verify installation">
# Check that all pods are running
kubectl get pods -A

# Access the Admin Console
echo "Admin Console: https://$(hostname):30000"
</CommandBlock>

<Tip>
The Admin Console runs on port **30000** by default. Make sure this port is accessible from your browser. You can customize the port during installation with the `--admin-console-port` flag.
</Tip>

</InstallStep>

</Tab>
<Tab title="Air Gap Installation">

<Note title="Air Gap Mode">
Air gap installations are for environments without direct internet access. You'll download the bundle on a connected machine and transfer it to your server.
</Note>

<InstallStep stepNumber={3} title="Run the Air Gap Installer">

Transfer the air gap bundle to your target machine, then run:

<LinuxAirgapInstallAssets />

</InstallStep>

<InstallStep stepNumber={4} title="Complete Setup via Admin Console">

Once the installer completes, open the Admin Console URL displayed in the terminal.

<CommandBlock label="Verify installation">
# Check that all pods are running
kubectl get pods -A

# Access the Admin Console
echo "Admin Console: https://$(hostname):30000"
</CommandBlock>

</InstallStep>

</Tab>
</Tabs>

---

## Next Steps

<Tip title="You're Live!">
Your Purrfect Match instance is installed and ready. Here's what to explore next:
</Tip>

- **Complete initial setup** via the Admin Console (TLS, database, shelter configuration)
- **[Checking for Updates](../updates/checking)** — Stay current with new releases
- **[FAQ](../support/faq)** — Common questions and troubleshooting tips
- **[Contact Support](../support/contact)** — We're here if you need a helping paw
