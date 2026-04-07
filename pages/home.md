---
title: Purrfect Match Documentation
---

# 🐾 Welcome to Purrfect Match, {{ customer.name }}!

Purrfect Match is the cat adoption platform that connects shelters with loving families. Streamline your adoption workflow with intelligent matching, real-time availability tracking, and comprehensive shelter management — all in one purrfectly integrated system.

<Note title="Your Portal at a Glance">
This documentation is tailored to your license and deployment. You're on version **{{ release.version }}** in the **{{ channel.name }}** channel.
</Note>

---

## What Purrfect Match Does

<Tabs>
<Tab title="Smart Matching">

**AI-Powered Compatibility Scoring**

The matching engine analyzes adopter preferences — living space, activity level, cat experience, and existing pets — against cat profiles including breed, temperament, age, and special needs. The result? Higher adoption success rates and happier forever homes.

</Tab>
<Tab title="Shelter Dashboard">

**Real-Time Shelter Operations**

Track every cat across your shelter network with live inventory, health records, photos, and adoption status. Manage capacity, monitor intake trends, and coordinate transfers between locations — all from a single dashboard.

</Tab>
<Tab title="Adoption Workflow">

**End-to-End Application Processing**

From initial application through background checks, approvals, and post-adoption follow-ups, Purrfect Match handles the entire journey. Automated notifications keep adopters informed while staff focus on what matters most — the cats.

</Tab>
<Tab title="Analytics">

**Data-Driven Decisions**

Track adoption trends, shelter capacity metrics, length-of-stay statistics, and outcome tracking. Export reports for stakeholders or use the built-in dashboards to spot opportunities and optimize operations.

</Tab>
</Tabs>

---

## Get Started

Choose your installation path below and you'll be up and running in no time — it's the cat's meow.

<Tabs>
<Tab title="Linux (Embedded Cluster)">

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}

The Linux installer bundles Kubernetes and all dependencies into a single package. Ideal if you don't already have a cluster.

1. **[Review System Requirements](installation/requirements)** — Confirm your server meets hardware and OS prerequisites
2. **[Install on Linux](installation/linux)** — Run the installer and complete setup via the Admin Console
3. **[Check for Updates](updates/checking)** — Keep Purrfect Match current with the latest features and fixes

<Tip title="Recommended for Single-Server Deployments">
The Embedded Cluster option is the fastest path to a running Purrfect Match instance. No Kubernetes experience required.
</Tip>

{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
{{else}}

<Note>
Linux installation is not available on your current license. Contact your account team if you'd like to explore this option.
</Note>

{{/if}}

</Tab>
<Tab title="Helm (Existing Cluster)">

{{#if entitlements.isHelmInstallEnabled}}

Deploy Purrfect Match into your existing Kubernetes cluster using Helm. Best for teams that already manage Kubernetes infrastructure.

1. **[Review System Requirements](installation/requirements)** — Confirm cluster version and resource availability
2. **[Install with Helm](installation/helm)** — Deploy using your preferred configuration
3. **[Helm Chart Reference](installation/helm-chart-reference)** — Fine-tune every aspect of your deployment

<Tip title="Recommended for Kubernetes Teams">
Helm gives you full control over namespaces, resource limits, ingress, and database configuration.
</Tip>

{{/if}}

{{#if entitlements.isHelmInstallEnabled}}
{{else}}

<Note>
Helm installation is not available on your current license. Contact your account team if you'd like to explore this option.
</Note>

{{/if}}

</Tab>
</Tabs>

---

## Quick Links

| Resource | Description |
|----------|-------------|
| [Release History](installation/release-history) | Browse all available versions and changelogs |
| [FAQ](support/faq) | Answers to common questions |
| [Contact Support](support/contact) | Get help from the Purrfect Match team |
| [Security](operations/security) | View security reports for your instance |

---

<Accordion title="What's New in {{ release.version }}" defaultOpen={true}>

Check the [Release History](installation/release-history) for the full changelog. Highlights of the current release include improvements to the matching engine, shelter dashboard performance, and adoption workflow notifications.

<Tip>
Enable automatic update checks to stay current. Visit [Checking for Updates](updates/checking) to learn more.
</Tip>

</Accordion>

<Accordion title="Need Help?">

We're here to help you find your footing — no cat-astrophes on our watch.

- **[FAQ](support/faq)** — Quick answers to common questions
- **[Contact Support](support/contact)** — Reach the team directly
- **[Upload a Support Bundle](operations/bundles/uploaded)** — Help us diagnose issues faster

</Accordion>
