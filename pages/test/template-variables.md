# Template Variables Test Page

This page exercises every template variable the Enterprise Portal renderer
knows about, plus a pile of nearby-but-unsupported variants so we can see
what resolves to what.

Syntax: Mustache-style `{{ variable }}` against the `RenderContext` shape
defined in `enterprise-portal/templates/docs/app/lib/render-context.ts`.
Missing values render as empty string.

---

## `app.*`

- `app.name` → `{{ app.name }}`
- `app.slug` → `{{ app.slug }}`
- `app.nonexistent` (not in context) → `{{ app.nonexistent }}`

## `customer.*`

- `customer.name` → `{{ customer.name }}`
- `customer.email` → `{{ customer.email }}`
- `customer.id` → `{{ customer.id }}`
- `customer.firstName` (not in context — only name/email/id) → `{{ customer.firstName }}`
- `customer.organization` (not in context) → `{{ customer.organization }}`

## `license.*`

The license is passed through as a raw `Record<string, unknown>`, so every
field on the API License object is reachable. Booleans render as
`"true"` / `"false"`.

### Identifiers / metadata

- `license.id` → `{{ license.id }}`
- `license.appId` → `{{ license.appId }}`
- `license.appName` → `{{ license.appName }}`
- `license.appIcon` → `{{ license.appIcon }}`
- `license.customerId` → `{{ license.customerId }}`
- `license.customerName` → `{{ license.customerName }}`
- `license.customerEmail` → `{{ license.customerEmail }}`
- `license.createdAt` → `{{ license.createdAt }}`
- `license.updatedAt` → `{{ license.updatedAt }}`
- `license.expireAt` → `{{ license.expireAt }}`
- `license.expiresAt` (computed alias) → `{{ license.expiresAt }}`
- `license.isExpired` → `{{ license.isExpired }}`
- `license.isArchived` → `{{ license.isArchived }}`
- `license.licenseType` → `{{ license.licenseType }}`
- `license.sequence` → `{{ license.sequence }}`
- `license.environment` → `{{ license.environment }}`

### Install / capability booleans

- `license.isAirgapSupported` → `{{ license.isAirgapSupported }}`
- `license.isGitopsSupported` → `{{ license.isGitopsSupported }}`
- `license.isIdentityServiceSupported` → `{{ license.isIdentityServiceSupported }}`
- `license.isGeoaxisSupported` → `{{ license.isGeoaxisSupported }}`
- `license.isSnapshotSupported` → `{{ license.isSnapshotSupported }}`
- `license.isDisasterRecoverySupported` → `{{ license.isDisasterRecoverySupported }}`
- `license.isSupportBundleUploadSupported` → `{{ license.isSupportBundleUploadSupported }}`
- `license.isEmbeddedClusterDownloadEnabled` → `{{ license.isEmbeddedClusterDownloadEnabled }}`
- `license.isEmbeddedClusterMultiNodeEnabled` → `{{ license.isEmbeddedClusterMultiNodeEnabled }}`
- `license.isKotsInstallEnabled` → `{{ license.isKotsInstallEnabled }}`
- `license.isHelmInstallEnabled` → `{{ license.isHelmInstallEnabled }}`
- `license.isKurlInstallEnabled` → `{{ license.isKurlInstallEnabled }}`
- `license.isHelmAirgapEnabled` → `{{ license.isHelmAirgapEnabled }}`
- `license.isSecurityCenterEnabled` → `{{ license.isSecurityCenterEnabled }}`

### Arrays / nested objects (the path resolver bails on non-objects)

- `license.channels` (array) → `{{ license.channels }}`
- `license.channels.0` (numeric index — resolver only walks objects, not arrays) → `{{ license.channels.0 }}`
- `license.entitlementFields` (array) → `{{ license.entitlementFields }}`
- `license.entitlementValues` (array) → `{{ license.entitlementValues }}`
- `license.fields` (computed array) → `{{ license.fields }}`

### Things not on the license object

- `license.signature` (not exposed via the EP license API) → `{{ license.signature }}`
- `license.endpoint` → `{{ license.endpoint }}`
- `license.licenseKey` (intentionally not exposed — would be a secret) → `{{ license.licenseKey }}`

## `entitlements.*`

Built-in allowlisted booleans (always present, even if false):

- `entitlements.isHelmInstallEnabled` → `{{ entitlements.isHelmInstallEnabled }}`
- `entitlements.isAirgapSupported` → `{{ entitlements.isAirgapSupported }}`
- `entitlements.isEmbeddedClusterDownloadEnabled` → `{{ entitlements.isEmbeddedClusterDownloadEnabled }}`
- `entitlements.isEmbeddedClusterMultiNodeEnabled` → `{{ entitlements.isEmbeddedClusterMultiNodeEnabled }}`
- `entitlements.isKotsInstallEnabled` → `{{ entitlements.isKotsInstallEnabled }}`
- `entitlements.isHelmAirgapEnabled` → `{{ entitlements.isHelmAirgapEnabled }}`

Custom entitlements (only resolve if the customer's license actually defines them):

- `entitlements.numSeats` → `{{ entitlements.numSeats }}`
- `entitlements.maxNodes` → `{{ entitlements.maxNodes }}`
- `entitlements.tier` → `{{ entitlements.tier }}`
- `entitlements.featureFoo` → `{{ entitlements.featureFoo }}`

Entitlements NOT in the allowlist and not custom on this license:

- `entitlements.isKurlInstallEnabled` (license has it, but it's not copied into entitlements) → `{{ entitlements.isKurlInstallEnabled }}`
- `entitlements.isGitopsSupported` → `{{ entitlements.isGitopsSupported }}`
- `entitlements.isSnapshotSupported` → `{{ entitlements.isSnapshotSupported }}`
- `entitlements.isSecurityCenterEnabled` → `{{ entitlements.isSecurityCenterEnabled }}`

## `channel.*`

- `channel.name` → `{{ channel.name }}`
- `channel.slug` → `{{ channel.slug }}`
- `channel.id` (not in context) → `{{ channel.id }}`

## `release.*`

- `release.version` → `{{ release.version }}`
- `release.channel` (not in context — channel is a sibling) → `{{ release.channel }}`
- `release.createdAt` (not in context) → `{{ release.createdAt }}`

## `branding.*`

- `branding.title` → `{{ branding.title }}`
- `branding.contact` → `{{ branding.contact }}`
- `branding.supportPortalLink` → `{{ branding.supportPortalLink }}`
- `branding.logo` (not in context) → `{{ branding.logo }}`
- `branding.theme` (not in context) → `{{ branding.theme }}`

## `terraform_modules.*`

Currently always an empty map — anything under it resolves to nothing.

- `terraform_modules.aws-infrastructure` → `{{ terraform_modules.aws-infrastructure }}`
- `terraform_modules.gcp` → `{{ terraform_modules.gcp }}`
- `terraform_modules.anything` → `{{ terraform_modules.anything }}`

## Namespaces that don't exist at all

- `{{ user.name }}` → `{{ user.name }}`
- `{{ vendor.name }}` → `{{ vendor.name }}`
- `{{ team.name }}` → `{{ team.name }}`
- `{{ org.name }}` → `{{ org.name }}`
- `{{ portal.version }}` → `{{ portal.version }}`
- `{{ env.NODE_ENV }}` → `{{ env.NODE_ENV }}`

---

## Asset helper

The `{{asset "..."}}` form expands to a same-origin EP URL that mints a
short-lived JWT and redirects to the asset.

- Existing-looking asset: `{{asset "assets/Enterprise-Portal-v2.pdf"}}`
- Nested path: `{{asset "downloads/installers/airgap.tgz"}}`
- Single-quoted form: `{{asset 'assets/logo.png'}}`
- Empty path: `{{asset ""}}`
- Missing path (just the literal tag — no quoted arg) → `{{asset}}`

---

## Block helpers

### `{{#if}}` (truthy check — `null`/`undefined`/`""`/`false`/`"false"`/`"0"`/`0` are falsy)

{{#if entitlements.isHelmInstallEnabled}}
This line renders when Helm install is enabled.
{{/if}}

{{#if entitlements.isAirgapSupported}}
This line renders when airgap is supported.
{{/if}}

{{#if license.isExpired}}
This license is expired.
{{/if}}

{{#if customer.name}}
Hello, {{ customer.name }}.
{{/if}}

### `{{#if}} ... {{else}} ... {{/if}}`

{{#if entitlements.isHelmInstallEnabled}}
Helm install path.
{{else}}
Non-Helm install path.
{{/if}}

{{#if license.isAirgapSupported}}
Airgap docs here.
{{else}}
Online-install docs here.
{{/if}}

### `{{#ifEquals path "value"}}`

{{#ifEquals release.version "1.0.0"}}
You are on version 1.0.0.
{{/ifEquals}}

{{#ifEquals channel.slug "stable"}}
Stable channel content.
{{else}}
Non-stable channel content.
{{/ifEquals}}

{{#ifEquals license.licenseType "prod"}}
Production license.
{{else}}
Non-production license.
{{/ifEquals}}

### Nested blocks

{{#if customer.email}}
{{#ifEquals channel.slug "stable"}}
You're on stable AND we know your email.
{{else}}
You're not on stable, but we know your email.
{{/ifEquals}}
{{/if}}

### Block helpers that DON'T exist (left as literal text by the renderer)

{{#unless license.isExpired}}
This `{{#unless}}` block is NOT supported — the whole thing should appear verbatim.
{{/unless}}

{{#each license.channels}}
`{{#each}}` is NOT supported either — this loop body should appear verbatim.
{{/each}}

{{#with customer}}
`{{#with}}` is NOT supported — appears verbatim.
{{/with}}

### Malformed blocks (parser flags as malformed and skips)

{{#if some thing with spaces}}
Malformed `{{#if}}` condition — left as-is.
{{/if}}

{{#ifEquals release.version no-quotes-around-value}}
Malformed `{{#ifEquals}}` — left as-is.
{{/ifEquals}}

---

## Syntax variants the regex does / doesn't match

- Spaces inside braces are fine: `{{   app.name   }}` → `{{   app.name   }}`
- Internal spaces in the path break it: `{{ app . name }}` → `{{ app . name }}`
- Hyphens in segments are allowed: `{{ terraform_modules.aws-infrastructure }}` → `{{ terraform_modules.aws-infrastructure }}`
- Case-sensitive: `{{ APP.NAME }}` → `{{ APP.NAME }}`
- Filters / pipes are not supported: `{{ customer.name | upper }}` → `{{ customer.name | upper }}`
- Liquid syntax is ignored: `{% if customer.name %}{% endif %}`
- Triple-stash (raw, Handlebars-style) is not supported: `{{{ customer.name }}}`
- Empty braces: `{{}}` and `{{ }}`
- Single brace doesn't trigger anything: `{ app.name }`
