# Link Validator agent guide

This repository is a placeholder for a Microsoft 365 link-validation toy. [README.md](README.md) describes planned behavior; the inspected default branch contains no implementation, package manifest, tests, or CI. Do not describe planned features as working capabilities or invent build commands.

## Starting implementation

Before introducing code, settle the first supported content source, the authentication contract, and what “reachable” means for a particular user. OneDrive document links, shared-link permissions, and Teams message links can fail for different reasons; retain those distinctions in results. Link the decision and acceptance criteria from the README.

Inspect the related `file-finder`, `mail-triage`, and `todo` repositories named in the README for reusable authentication and API patterns. Confirm their current contracts before adding a dependency; do not copy token-cache files or embed tenant credentials. Preserve the stated GPL-3.0-or-later license intent when adding source and dependency metadata.

## Operational boundaries and verification

The initial implementation should make inspection explicit. A scan must not silently change link permissions, recreate shares, modify documents, or send notifications. Never log access tokens, confidential document contents, or complete sensitive sharing URLs in diagnostics.

Use synthetic examples for malformed URLs, authorization failures, missing resources, throttling, and redirects. Any tenant-wide scan needs a named tenant and bounded authorized scope. Record the user identity and observation time without exposing credentials: access observed by one account is not proof of universal access.

When scaffolding lands, document its actual setup and test commands here and add checks that distinguish missing implementation from failed validation.
