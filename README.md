# SAU Missions Dashboard Releases

Official desktop releases of the **SAU Missions Dashboard**, a fullscreen kiosk application for displaying missions information.

This repository hosts installers and automatic-update files. Application source code is maintained in [SAU-Missions-React](https://github.com/miromanestar/SAU-Missions-React).

## Download and install

**[Download the latest release](https://github.com/miromanestar/SAU-Dashboard-Releases/releases/latest)**

1. Open the latest release.
2. Under **Assets**, download the Windows installer ending in `-setup.exe`.
3. Run the installer and follow the prompts.
4. Launch **SAU Missions Dashboard**.

Current releases target **64-bit Windows (x64)**. The application opens fullscreen and stays above other windows for kiosk use.

An internet connection is required to retrieve dashboard content and check for updates.

## Automatic updates

The application checks for updates when it starts and every **15 minutes** afterward.

When an update is available, the application downloads and installs it automatically, then restarts. No manual download is normally required after the initial installation.

Update signatures are verified before installation. If an update check fails, the application retries at the next scheduled check.

## Release assets

| File | Purpose |
| --- | --- |
| `*-setup.exe` | Windows installer for manual installation |
| `*.sig` | Signature used to verify an update |
| `latest.json` | Update metadata read by the application |

For manual installation, download the `.exe` installer. You do not need to download the `.sig` or `latest.json` files.

## Troubleshooting

### The dashboard cannot load

Check the kiosk's internet connection and configuration. If the application displays a **Retry** button, use it after resolving the issue.

### An update has not appeared

Confirm that the kiosk can reach GitHub. Restart the application to trigger an immediate update check, or wait for the next scheduled check.

You can also download the latest installer from the [Releases page](https://github.com/miromanestar/SAU-Dashboard-Releases/releases).

## For maintainers

Releases are built by the GitHub Actions workflow in the source repository and uploaded here as **draft releases**.

Before publishing:

1. Confirm the release version and notes.
2. Verify that the Windows installer, its update signature, and `latest.json` are attached.
3. Publish the release as a stable release.

The application reads update metadata from:

https://github.com/miromanestar/SAU-Dashboard-Releases/releases/latest/download/latest.json

Keep the updater assets attached to published releases. Draft and prerelease builds are not intended for the stable update channel.
