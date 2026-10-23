# SAU Missions Dashboard — Release Guide

An interactive missions display for SAU, designed for large touchscreen kiosks. Explore mission opportunities, discover where student missionaries are serving, and meet the people behind Student Missions—all from a fullscreen dashboard.

**[Download the latest Windows release](https://github.com/miromanestar/SAU-Dashboard-Releases/releases/latest)** · **[Browse releases and release notes](https://github.com/miromanestar/SAU-Dashboard-Releases/releases)**

This guide covers installation, everyday use, and updates for **SAU Missions Dashboard**. Each release includes a Windows installer and release notes describing what has changed.

## What the dashboard offers

- **Mission opportunities:** browse featured opportunities and open their details.
- **Interactive globe:** explore countries and student missionary locations, with access to country statistics.
- **SM Friends:** browse student missionary profiles and filter the directory by country.
- **Mission updates:** view mission information and status slides.
- **Meet the Team:** explore team profiles and scan an appointment QR code when available.
- **Touch-friendly navigation:** move between sections using large on-screen controls and open profiles for more information.
- **Kiosk operation:** fullscreen, always-on-top presentation with configurable return to the home screen after inactivity.
- **Content refresh and recovery:** receive published content changes without reinstalling, with automatic retries and saved content to help keep the display usable during temporary connection problems.

Available sections, their order, and the home screen depend on the configuration published by the dashboard administrator. Content and available features may also vary by installed version.

## Requirements

- **64-bit Windows (x64).** Current releases provide a Windows desktop installer.
- **A large display, ideally a touchscreen.** The interface is designed for kiosk use rather than a phone-sized screen.
- **An internet connection** to load current content, access linked websites, and download application updates.
- **Dashboard configuration supplied by your administrator.** Installing the application alone does not provide access to the missions content service.

## Download and install

1. Open the [latest release](https://github.com/miromanestar/SAU-Dashboard-Releases/releases/latest).
2. Under **Assets**, download the Windows installer ending in `-setup.exe`.
3. Run the installer and follow the prompts.
4. Have your dashboard administrator provide or confirm the configuration for this installation.
5. Launch the application and confirm that the dashboard content loads.

The dashboard opens fullscreen and stays above other windows. Set it up on the intended kiosk computer rather than a machine you need to use for other work at the same time.

Use the `-setup.exe` installer from the official release page. The other release files support automatic updates and do not need to be downloaded separately.

## Using the dashboard

Choose a section using the on-screen navigation. Select an opportunity, country, or portrait to see more information, then use the on-screen close or dismiss control to return. Scan available QR codes with a phone to follow the associated links.

After a period of inactivity, the dashboard closes open details and resets the browsing view. It can also return to the configured home screen; the default inactivity timeout is **three minutes**, but the administrator can change this behavior.

Dashboard content is managed centrally and refreshes automatically. Content changes are separate from application releases and generally do not require a new installation.

### Temporary connection problems

When available, the dashboard can continue showing previously saved content while it retries the connection. A status notice indicates when displayed content is not current. Saved content is a temporary fallback, not a fully offline mode: a new installation needs a connection to load content, and images, external pages, or some information may remain unavailable offline.

## Releases and automatic updates

New versions are published on the [Releases page](https://github.com/miromanestar/SAU-Dashboard-Releases/releases) after review, with a Windows installer, release notes, and automatic-update files. Only published stable releases are delivered through automatic updates; prereleases are not included.

The installed application checks for a new stable release at startup and every **15 minutes** afterward. When an update is available, it downloads and verifies the update signature before installation, then restarts to run the new version. An update can briefly interrupt the display; a manual installer download is normally unnecessary after initial setup.

If an update check or download fails, the dashboard remains available and the updater tries again at a later scheduled check. You can also install the latest published version manually from the [Releases page](https://github.com/miromanestar/SAU-Dashboard-Releases/releases).

Check each release’s notes for version-specific changes and any installation guidance.

### Which release file should I download?

| File | Purpose | Download manually? |
| --- | --- | --- |
| `*-setup.exe` | Windows installer | **Yes**, for initial installation or a manual update |
| `*.sig` | Signature used by the automatic updater | No |
| `latest.json` | Information used by the application to find updates | No |

## Troubleshooting

### The dashboard cannot load

Check the computer’s internet connection. If a **Retry** button is shown, use it once the connection is restored. If the problem continues—or this is a new installation—ask your dashboard administrator to check the installation’s configuration and access to the content service.

### Content looks outdated or a section is missing

Look for a connection or saved-content notice and check internet access. Sections can also be hidden or reordered by the administrator. Ask them to confirm that the expected content and navigation settings have been published.

### An application update has not appeared

Confirm that the computer can reach GitHub. Restart the application to trigger a startup update check, or wait for the next scheduled check. Only published stable releases are delivered automatically. If needed, download the latest installer from the [Releases page](https://github.com/miromanestar/SAU-Dashboard-Releases/releases).

### Need more help?

Contact the person or team responsible for your SAU Missions Dashboard installation. Include the installed version if known, what you expected to see, and the exact message or a screenshot of the problem. Do not share access tokens, configuration files, or private personal information in public reports.
