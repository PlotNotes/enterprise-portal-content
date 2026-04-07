---
title: Frequently Asked Questions
---

# Frequently Asked Questions

<Accordion title="What is Purrfect Match?">
Purrfect Match is a cat adoption platform that connects shelters with potential adopters. It features smart matching, real-time shelter dashboards, and an end-to-end adoption workflow.
</Accordion>

<Accordion title="What are the system requirements?">

The minimum requirements depend on your installation method:

{{#if entitlements.isHelmInstallEnabled}}
**Helm:** Kubernetes 1.28+, Helm 3.10+, 2 CPU / 2 GB RAM minimum.
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
**Linux (Embedded Cluster):** Ubuntu 20.04+ / RHEL 8+ / CentOS 8+, 2 CPU / 2 GB RAM / 40 GB disk minimum.
{{/if}}

See the [full requirements](../installation/requirements) for details.
</Accordion>

<Accordion title="Which installation method should I use?">

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
{{#if entitlements.isHelmInstallEnabled}}
Choose **Linux (Embedded Cluster)** if you want a single-server install that bundles Kubernetes. Choose **Helm** if you already have a Kubernetes cluster and want to manage Purrfect Match alongside other workloads.
{{/if}}
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
Your license includes [Linux installation](../installation/linux).
{{/if}}

{{#if entitlements.isHelmInstallEnabled}}
Your license includes [Helm installation](../installation/helm).
{{/if}}
</Accordion>

<Accordion title="How do I check for updates?">
Visit the [Checking for Updates](../updates/checking) page to see available updates for your installation.
</Accordion>

<Accordion title="Can I use an external database instead of the bundled PostgreSQL?">

{{#if entitlements.isHelmInstallEnabled}}
Yes. Set `postgresql.enabled` to `false` and configure `postgresql.externalHost` in your Helm values. See the [Helm Chart Reference](../installation/helm-chart-reference) for all database-related values.
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
The Embedded Cluster installation includes a bundled PostgreSQL instance. External database configuration is available with Helm installations.
{{/if}}
</Accordion>

<Accordion title="How do I collect diagnostic information?">
Generate a support bundle for troubleshooting:

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- [Linux support bundles](../operations/bundles/linux)
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- [Helm support bundles](../operations/bundles/helm)
{{/if}}
- [Upload an existing bundle](../operations/bundles/uploaded)
</Accordion>

<Accordion title="How do I configure TLS/HTTPS?">

{{#if entitlements.isHelmInstallEnabled}}
For Helm installs, configure the `ingress.tls` values in your Helm chart. See the [Helm Chart Reference](../installation/helm-chart-reference) for details.
{{/if}}

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
For Linux installs, TLS can be configured through the Admin Console after installation.
{{/if}}
</Accordion>

<Accordion title="How does the smart matching algorithm work?">
The matching engine analyzes adopter preferences (living space, activity level, experience with cats, other pets) and cat profiles (breed, age, temperament, special needs) to generate compatibility scores. Results are ranked to help shelter staff facilitate the best matches.
</Accordion>

<Accordion title="Where can I get help?">
Visit the [Contact Support](contact) page or [upload a support bundle](../operations/bundles/uploaded) to help our team diagnose issues quickly.
</Accordion>
