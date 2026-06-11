---
title: Security
visible_when:
  entitlements:
    - canViewSecurity
---

{{#if entitlements.canViewSecurity}}
You can view security center
{{else}}
You cannot view security center
{{/if}}


# Purrfect Match Security

View vulnerability scanning results and security reports for your Purrfect Match releases.

Security Version Selector
<SecurityVersionSelector />

CVE Report
<CVEReport />

SBOM Report
<SBOMReport />

<Warning>
Security reports contain sensitive information. Access to this page is restricted to users with security view permissions.
</Warning>
