---
title: Frequently Asked Questions
---

# Frequently Asked Questions

Find answers to the most common questions about Purrfect Match. Can't find what you're looking for? [Contact support](contact) — we don't bite (but some of the cats might).

---

<Note title="General">
Questions about what Purrfect Match is and how it works.
</Note>

<Accordion title="What is Purrfect Match?">

Purrfect Match is a cat adoption platform built for animal shelters. It connects shelters with potential adopters through intelligent matching, real-time shelter dashboards, and an end-to-end adoption workflow — from application to forever home.

</Accordion>

<Accordion title="How does the smart matching algorithm work?">

The matching engine analyzes adopter preferences — living space, activity level, experience with cats, other pets — alongside cat profiles including breed, age, temperament, and special needs. It generates compatibility scores and ranks results so shelter staff can facilitate the best possible matches.

The algorithm continuously improves based on successful adoption outcomes, so the more your shelter uses it, the smarter it gets. Purrfectly adaptive.

</Accordion>

---

<Note title="Installation & Requirements">
Questions about getting Purrfect Match up and running.
</Note>

<Accordion title="What are the system requirements?">

Requirements depend on your installation method:

{{#if entitlements.isHelmInstallEnabled}}
**Helm:** Kubernetes 1.28+, Helm 3.10+, 2 CPU / 2 GB RAM minimum (4 CPU / 4 GB recommended).
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
**Linux (Embedded Cluster):** Ubuntu 20.04+ / RHEL 8+ / CentOS 8+, 2 CPU / 2 GB RAM / 40 GB disk minimum (4 CPU / 8 GB / 100 GB recommended).
{{/if}}

See the [full system requirements](../installation/requirements) for detailed hardware tables, supported OS versions, and port requirements.

</Accordion>

<Accordion title="Which installation method should I use?">

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
{{#if entitlements.isHelmInstallEnabled}}
**Choose Linux (Embedded Cluster)** if you want a single-server install that bundles Kubernetes — no cluster management needed. **Choose Helm** if you already run Kubernetes and want to manage Purrfect Match alongside your other workloads.
{{/if}}
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
Your license includes [Linux installation](../installation/linux). This is the fastest path to getting started.
{{/if}}

{{#if entitlements.isHelmInstallEnabled}}
Your license includes [Helm installation](../installation/helm). This gives you full control over your Kubernetes deployment.
{{/if}}

</Accordion>

---

<Note title="Configuration & Operations">
Questions about customizing and managing your deployment.
</Note>

<Accordion title="Can I use an external database instead of the bundled PostgreSQL?">

{{#if entitlements.isHelmInstallEnabled}}
Yes. Set `postgresql.enabled` to `false` and configure `postgresql.externalHost` and related values in your Helm chart. See the [Helm Chart Reference](../installation/helm-chart-reference) for all database-related configuration options.
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
The Embedded Cluster installation includes a bundled PostgreSQL instance. External database configuration is available with Helm installations only.
{{/if}}

</Accordion>

<Accordion title="How do I configure TLS/HTTPS?">

{{#if entitlements.isHelmInstallEnabled}}
For Helm installs, configure the `ingress.tls` section in your Helm values. You can provide your own certificate or integrate with cert-manager for automatic issuance. See the [Helm Chart Reference](../installation/helm-chart-reference) for details.
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
For Linux installs, TLS is configured through the Admin Console after installation. Navigate to **Settings > TLS/SSL** to upload your certificate and key.
{{/if}}

</Accordion>

<Accordion title="How do I check for updates?">

Visit the [Checking for Updates](../updates/checking) page for instructions specific to your installation method. We recommend checking regularly — each release includes improvements to matching accuracy, performance, and security.

</Accordion>

---

<Note title="Troubleshooting & Support">
Questions about diagnosing issues and getting help.
</Note>

<Accordion title="How do I collect diagnostic information?">

Generate a support bundle to share with our team:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- **Linux:** [Generate a Linux support bundle](../operations/bundles/linux) from the Admin Console or CLI
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- **Helm:** [Generate a Helm support bundle](../operations/bundles/helm) using the support-bundle kubectl plugin
{{/if}}
- **Upload:** [Upload an existing bundle](../operations/bundles/uploaded) directly through the portal

Support bundles collect logs, cluster state, and configuration — no sensitive credentials are included.

</Accordion>

<Accordion title="Where can I get help?">

- **[FAQ](faq)** — You're already here! Browse the sections above.
- **[Contact Support](contact)** — Reach out to the Purrfect Match team directly
- **[Upload a Support Bundle](../operations/bundles/uploaded)** — Help us diagnose issues faster by uploading diagnostic data

We're always happy to lend a paw.

</Accordion>
