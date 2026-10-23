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
4. Create `config.txt` in the application’s installation folder using the [configuration instructions below](#configuration).
5. Launch the application and confirm that the dashboard content loads.

The dashboard opens fullscreen and stays above other windows. Set it up on the intended kiosk computer rather than a machine you need to use for other work at the same time.

Use the `-setup.exe` installer from the official release page. The other release files support automatic updates and do not need to be downloaded separately.

## Configuration

The application reads its connection settings from a plain-text file named **`config.txt`**. Obtain the content service address and access token from your dashboard administrator before setting it up.

### Where to put the file

Place `config.txt` **in the same folder as the installed application’s `.exe` file**—not alongside the downloaded `-setup.exe` installer or the desktop shortcut.

To find the correct folder, right-click the application shortcut and select **Open file location**. If this opens a folder containing another shortcut, open that shortcut’s file location to reach the actual executable. Save `config.txt` there. Windows may require administrator permission to save files in the installation folder.

When saving from Notepad, select **All files** as the file type and use UTF-8 encoding. Make sure the filename is exactly `config.txt`, not `config.txt.txt`. Close and reopen the application after creating or changing the file; settings are read at startup.

### File contents

Use one `KEY=value` setting per line, without quotation marks. For example:

```ini
# Replace these example connection settings with those from your administrator.
API_ENDPOINT=https://missions.example.org
API_TOKEN=REPLACE_WITH_YOUR_ACCESS_TOKEN
POLLING_DELAY=300
```

| Setting | Required? | Accepted value |
| --- | --- | --- |
| `API_ENDPOINT` | Yes | The content service’s base URL, including `https://` or `http://`. Use HTTPS for remote connections. Do not append `/api`; the application adds it automatically. |
| `API_TOKEN` | Yes | A nonempty access token supplied by your administrator. Enter only the token, without quotes or a `Bearer ` prefix. |
| `POLLING_DELAY` | No | Content refresh interval in **seconds**: a positive finite number up to `86400` (24 hours). Defaults to `300` (5 minutes) when omitted or empty. For example, `60` refreshes every minute. |

Setting names are case-sensitive. Blank lines and lines beginning with `#` are ignored; place comments on their own lines. Leading and trailing spaces around names and values are trimmed. Both required settings must have nonempty values, and an invalid URL or refresh interval prevents the dashboard from loading.

`POLLING_DELAY` controls dashboard content refreshes, **not** the application’s 15-minute update checks.

**Keep `config.txt` private:** it contains an access token stored as plain text. Limit access to the file, keep any backup secure, and never attach it to a public issue or release.

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

Check the computer’s internet connection. If a **Retry** button is shown, use it once the connection is restored. For a new installation, confirm that `config.txt` is beside the installed executable and contains a valid `API_ENDPOINT` and `API_TOKEN`, then restart the application. If the problem continues, ask your dashboard administrator to check the settings and access to the content service.

### Content looks outdated or a section is missing

Look for a connection or saved-content notice and check internet access. Sections can also be hidden or reordered by the administrator. Ask them to confirm that the expected content and navigation settings have been published.

### An application update has not appeared

Confirm that the computer can reach GitHub. Restart the application to trigger a startup update check, or wait for the next scheduled check. Only published stable releases are delivered automatically. If needed, download the latest installer from the [Releases page](https://github.com/miromanestar/SAU-Dashboard-Releases/releases).

### Need more help?

Contact the person or team responsible for your SAU Missions Dashboard installation. Include the installed version if known, what you expected to see, and the exact message or a screenshot of the problem. Do not share access tokens, configuration files, or private personal information in public reports.
