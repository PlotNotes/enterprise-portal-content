---
title: Helm Installation
visible_when:
  entitlements:
    - isHelmInstallEnabled
---

# Install Purrfect Match with Helm

Deploy Purrfect Match to your existing Kubernetes cluster using Helm. You'll be matching cats with families in no time.

<Prerequisites>
- Kubernetes **1.28** or later
- Helm **3.10** or later
- `kubectl` configured with cluster access
- A default StorageClass for persistent volumes
- Review the [full system requirements](requirements) before proceeding
</Prerequisites>

---

<InstallStep stepNumber={1} title="Name Your Instance">

Give this Purrfect Match instance a name to identify it in your environment.

<InstanceName title="Name Your Purrfect Match Instance" />

</InstallStep>

<InstallStep stepNumber={2} title="Configure Your Deployment">

Select your deployment preferences below. The install commands will update automatically based on your choices.

<KubernetesDistribution />
<NetworkAvailability installType="helm" />
<RegistryAccess />
<VersionSelector installType="helm" />

</InstallStep>

<Tabs defaultActiveTab={0}>
<Tab title="Online Installation">

<InstallStep stepNumber={3} title="Install Purrfect Match">

Run the following commands to deploy Purrfect Match to your cluster.

<HelmInstallAssets />

</InstallStep>

<InstallStep stepNumber={4} title="Verify the Installation">

Confirm all pods are running and healthy:

<CommandBlock command="kubectl get pods -n purrfect-match" />

You should see all pods in a `Running` or `Completed` state. If any pods are in `CrashLoopBackOff` or `Pending`, check the [FAQ](../support/faq) for troubleshooting guidance.

<CommandBlock command="kubectl get svc -n purrfect-match" />

</InstallStep>

</Tab>
<Tab title="Air Gap Installation">

<Note title="Air Gap Mode">
Air gap installations are for environments without direct internet access. You'll need to download the bundle on a connected machine and transfer it to your cluster network.
</Note>

<InstallStep stepNumber={3} title="Install Purrfect Match (Air Gap)">

Follow the steps below to deploy in an air-gapped environment.

<HelmAirgapInstallAssets />

</InstallStep>

<InstallStep stepNumber={4} title="Verify the Installation">

Confirm all pods are running and healthy:

<CommandBlock command="kubectl get pods -n purrfect-match" />

You should see all pods in a `Running` or `Completed` state.

<CommandBlock command="kubectl get svc -n purrfect-match" />

</InstallStep>

</Tab>
</Tabs>

---

## Next Steps

<Tip title="You're Live!">
Your Purrfect Match instance is deployed. Here's what to do next:
</Tip>

- **[Helm Chart Reference](helm-chart-reference)** — Fine-tune your deployment with all available configuration values
- **[Checking for Updates](../updates/checking)** — Stay current with new releases and security patches
- **[FAQ](../support/faq)** — Common questions and troubleshooting tips
- **[Contact Support](../support/contact)** — Reach out if you need a helping paw
