---
title: Contact Support
---

# Contact Purrfect Match Support

We're here to help — let's get your issue resolved so you can get back to matching cats with families.

<ContactInfo />

---

## Before You Reach Out

<Note title="Help Us Help You">
Including a support bundle with your request dramatically speeds up resolution time. It gives our team the diagnostic data they need without back-and-forth.
</Note>

<InstallStep stepNumber={1} title="Check the FAQ">

Many common questions are already answered in our [Frequently Asked Questions](faq). A quick look might save you time.

</InstallStep>

<InstallStep stepNumber={2} title="Generate a Support Bundle">

A support bundle collects logs, cluster state, and configuration data — no sensitive credentials are included.

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}

**Linux installations:** Follow the guide at [Linux Support Bundles](../operations/bundles/linux) to generate a bundle from the Admin Console or CLI.

{{/if}}

{{#if entitlements.isHelmInstallEnabled}}

**Helm installations:** Follow the guide at [Helm Support Bundles](../operations/bundles/helm) to generate a bundle using the support-bundle plugin.

{{/if}}

</InstallStep>

<InstallStep stepNumber={3} title="Upload Your Bundle">

Use the uploader below to attach your support bundle directly to your support request. Accepted formats: `.tar.gz` and `.tgz`.

<SupportBundleUpload />

You can also manage previously uploaded bundles on the [Upload Support Bundle](../operations/bundles/uploaded) page.

</InstallStep>

---

<Tip title="Fastest Resolution">
Requests that include a support bundle and a clear description of the issue (steps to reproduce, expected vs. actual behavior) are resolved significantly faster. Every detail helps us track down the root cause.
</Tip>
