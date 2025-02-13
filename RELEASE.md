# Coolify Release Guide

This guide outlines the release process for Coolify, intended for developers and those interested in understanding how Coolify releases are managed and deployed.

> Do not use nightly/beta builds in production as there is no guarantee of stability.

## Version Availability

When a new version is released and a new GitHub release is created, it doesn't immediately become available for your instance. Here's how version availability works for different instance types.

### Self-Hosted

- **Update Frequency:** More frequent updates, especially on the nightly release channel.
- **Update Availability:** New versions are available once the CDN has been updated.
- **Update Methods:**
  1. **Manual Update in Instance Settings:**
     - Go to `Settings > Update Check Frequency` and click the `Check Manually` button.
     - If an update is available, an upgrade button will appear on the sidebar.
  2. **Automatic Update:**
     - If enabled, the instance will update automatically at the time set in the settings.
  3. **Re-run Installation Script:**
     - Run the installation script again to upgrade to the latest version available on the CDN:
     ```bash
     curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash
     ```

> [!IMPORTANT]
> If a new release is available on GitHub but your instance hasn't updated yet or no upgrade button is shown in the UI, the CDN might not have been updated yet. This intentional delay ensures stability and allows for hotfixes before official release.

### Cloud

- **Update Frequency:** Less frequent as it's a managed service.
- **Update Availability:** New versions are available once Andras has updated the cloud version manually.
- **Update Method:**
  - Updates are managed by Andras, who ensures each cloud version is thoroughly tested and stable before releasing it.

> [!IMPORTANT]
> The cloud version of Coolify may be several versions behind the latest GitHub releases even if the CDN is updated. This is intentional to ensure stability and reliability for cloud users and Andras will manully update the cloud version when the update is ready.

## Manually Update/ Downgrade to Specific Versions

> [!CAUTION]  
> Updating to unreleased versions is not recommended and can cause issues.

> [!IMPORTANT]
> Downgrading is supported but not recommended and can cause issues because of database migrations and other changes.

To update your Coolify instance to a specific version, use the following command:

```bash
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | bash -s <version>
```
Replace `<version>` with the version you want to update to (for example `4.0.0-beta.332`).
