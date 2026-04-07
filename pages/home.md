---
title: Purrfect Match Documentation
---

# Welcome to Purrfect Match

Purrfect Match is a cat adoption platform that connects shelters with loving families. It streamlines the adoption process with intelligent matching, real-time availability tracking, and comprehensive shelter management tools.

<Note title="Welcome, {{ customer.name }}!">
This portal contains documentation tailored to your license and deployment method. Use the sidebar to navigate.
</Note>

## Key Features

- **Smart Matching** -- AI-powered matching algorithm pairs adopters with cats based on lifestyle, preferences, and compatibility
- **Shelter Dashboard** -- Real-time inventory of cats across shelters with health records, photos, and adoption status
- **Adoption Workflow** -- End-to-end application processing with background checks, approvals, and follow-up scheduling
- **Analytics** -- Adoption trends, shelter capacity metrics, and outcome tracking

## Getting Started

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
- [System Requirements](installation/requirements) -- Review prerequisites before installing
- [Linux Installation](installation/linux) -- Install Purrfect Match on a Linux server
{{/if}}
{{#if entitlements.isHelmInstallEnabled}}
- [Helm Installation](installation/helm) -- Deploy to an existing Kubernetes cluster
- [Helm Chart Reference](installation/helm-chart-reference) -- Configure chart values
{{/if}}
- [Release History](installation/release-history) -- View all available versions
- [FAQ](support/faq) -- Common questions and answers

## Current Version

You are running **{{ release.version }}** on the **{{ channel.name }}** channel.

<Tip>
Need help? Visit our [FAQ](support/faq) or [contact support](support/contact) for assistance.
</Tip>
