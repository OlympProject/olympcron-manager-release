# OlympCron Manager

**Visually manage Linux cron jobs over SSH. Build expressions, deploy changes, and apply templates from a native desktop app.**

OlympCron Manager is a free desktop application for Linux server administration. It connects to servers over SSH, loads and edits the remote crontab, provides a visual expression builder, and ships with ready-to-use templates for common automation tasks.

Website: https://olympstack.com  
Contact: contact@olympstack.com  
Support: support@olympstack.com

![OlympCron Manager Crontab Screen](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabJobs.png?raw=true)

## Why OlympCron Manager

Editing crontabs over SSH means remembering syntax, finding the right server session, and deploying changes manually. OlympCron Manager removes that friction:

- View and edit the remote crontab of any saved server without typing `crontab -e`.
- Build cron expressions visually using guided field selectors and presets.
- Preview expressions in human-readable language and see the next scheduled run times.
- Apply battle-tested templates for Docker cleanup, SSL renewal, database dumps, and more.
- Enable or disable individual jobs without deleting them.
- Deploy all changes to the server with one action.
- Store server credentials in OS-backed secure storage.

## Free to Use

OlympCron Manager is completely free. No license key, no account, no activation required.

## Product Screenshots

### Crontab Management

Connect to a server and view its full crontab. Toggle jobs on or off, edit any entry, or add new ones. Deploy all staged changes to the server in one step.

![Crontab Jobs](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabJobs.png?raw=true)

![Add Cron Job](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/crontTabAddCronJob.png?raw=true)

![Edit Cron Job](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabEditCronJob.png?raw=true)

### Visual Cron Builder

Build cron expressions step by step using field tabs for Minute, Hour, Day, Month, and Weekday. Switch between presets, specific values, and range/step modes. See the human-readable description and next ten scheduled run times.

![Cron Builder](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronBuilderTab.png?raw=true)

### Templates

Browse a library of ready-to-use cron templates organized by category. Copy an expression, copy the full cron line, or deploy a template directly to a server.

![Templates](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabTemplates.png?raw=true)

![Deploy Template](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/templateTabTemplatesDeploy.png?raw=true)

### Server Management

Add and manage SSH server profiles with password or private-key authentication, optional jump host support, and SSH fingerprint verification.

![Servers](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/serversTab.png?raw=true)

![Add Server](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/serversTabAddServer.png?raw=true)

### Settings

Configure theme, accent colors, OlympSuite sharing, and app behavior.

![Settings](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/settingsTab.png?raw=true)

## Core Features

### SSH Server Management

- Add, edit, delete, and organize server profiles.
- Password and private-key SSH authentication.
- Jump host support through a saved jump host or manual jump host configuration.
- Known-host fingerprint verification to reduce man-in-the-middle risk.
- Last-connected timestamps and active server selection.
- Servers saved in the OlympSuite shared registry are automatically available across OlympSuite apps on the same machine.

### Crontab Management

- Load the full crontab from any saved server over SSH.
- Display each job with its expression, human-readable schedule, and command.
- Enable or disable individual jobs using a toggle.
- Add new cron jobs with the visual builder or manual entry.
- Edit existing jobs directly.
- Delete jobs with confirmation.
- Stage multiple changes and deploy everything to the server in one action.

### Visual Cron Builder

- Dedicated tabs for each cron field: Minute, Hour, Day, Month, Weekday.
- Preset options for every field: every, every N, every 5, every 15, and common intervals.
- Specific mode: checkbox-based selection for exact values.
- Range and step mode: set start, end, and step with numeric pickers.
- Expert mode: edit the raw expression string with live validation.
- Human-readable description updates as you build.
- Next 10 scheduled run times shown below the builder.
- Copy the expression to the clipboard.

### Templates

- Predefined cron templates grouped by category: Backup, Docker, Security, System, Web Server.
- Templates include Docker cleanup, Certbot renewal, PostgreSQL dump, home backup, system health check, MySQL dump, SQLite backup, and Nginx restart.
- Copy expression, copy full cron line, or deploy directly to a selected server.

### Security Model

- SSH passwords, private keys, and passphrases are stored using `flutter_secure_storage`, which uses platform OS-backed secure storage facilities.
- Server profile JSON stores connection metadata only, not passwords or private keys.
- Deleting a server removes its stored credentials.
- SSH host fingerprints are verified on first connection.
- Export and configuration sharing intentionally excludes credentials.

## Installation

Download the latest release:

https://github.com/OlympProject/olympcron-manager-release/releases

### Windows

Run the installer `OlympCron-Manager-Setup-vX.Y.Z-windows-x64.exe` or extract `OlympCron-Manager-vX.Y.Z-windows-x64.zip` for a portable installation.

### Linux

Extract the tarball and run the binary:

```bash
tar -xzf OlympCron-Manager-vX.Y.Z-linux-x64.tar.gz
cd olympcron-manager
./olympcron_manager
```

## Requirements

- A Linux server reachable through SSH.
- SSH username plus password or private key.
- The SSH user needs permission to run `crontab` on the target server.
- Network access from your device to the target server.

## Quick Start

1. Install OlympCron Manager from the latest release.
2. Open the app and go to `Servers`.
3. Select `Add Server`.
4. Enter name, host, port, username, and authentication details.
5. Save the server. On first connection, verify the SSH fingerprint.
6. Open `Crontab` and select the server from the dropdown.
7. The app connects and loads the remote crontab automatically.
8. Use the `+` button to add a new cron job.
9. Toggle, edit, or delete existing jobs as needed.
10. Select `Deploy to Server` to apply all staged changes.

For a guided workflow, see [USERMANUAL.md](https://github.com/OlympProject/olympcron-manager-release/blob/main/USERMANUAL.md).

## Verify Downloads

Always verify the integrity of downloaded files before running them.

### SHA256 Checksums

**Linux / macOS:**
```bash
sha256sum -c SHA256SUMS.txt
```

**Windows (PowerShell):**
```powershell
Get-FileHash .\OlympCron-Manager-Setup-vX.Y.Z-windows-x64.exe -Algorithm SHA256
# Compare output against SHA256SUMS.txt
```

### GPG Signature

```bash
gpg --import GPGPublickey.md
gpg --verify SHA256SUMS.txt.asc SHA256SUMS.txt
```

Expected output:
```
gpg: Good signature from "OlympProject Release <release@olympstack.com>"
```

## OlympSuite

OlympCron Manager is part of the OlympSuite family of server administration tools.

| Product | Purpose |
| --- | --- |
| OlympSSH Commander | SSH terminal, Docker management, monitoring, alerts |
| OlympCron Manager | Visual cron job management over SSH |

Servers added in any OlympSuite app are automatically available in all other OlympSuite apps on the same machine. SSH credentials must be entered separately per app and are never shared between applications.

## Support

For product questions and support:

- Website: https://olympstack.com
- Contact: contact@olympstack.com
- Support: support@olympstack.com

When reporting an issue, include the app version, operating system, target server type, and a description of the workflow. Do not include passwords, private keys, or other secrets.

## OlympStack Suite

OlympStack is a suite of native desktop tools for developers and DevOps engineers.

| App | Repository |
|-----|------------|
| OlympAPI | [github.com/OlympProject/olympapi-release](https://github.com/OlympProject/olympapi-release) |
| OlympAtlas | [github.com/OlympProject/olympatlas-release](https://github.com/OlympProject/olympatlas-release) |
| OlympCron Manager | [github.com/OlympProject/olympcron-manager-release](https://github.com/OlympProject/olympcron-manager-release) |
| OlympSSH Commander | [github.com/OlympProject/olympssh-commander-release](https://github.com/OlympProject/olympssh-commander-release) |
| OlympTest Manager | [github.com/OlympProject/olymptest-manager-release](https://github.com/OlympProject/olymptest-manager-release) |

---

## License

OlympCron Manager is proprietary software. This repository contains binary releases and related documentation only.

Use of the software is governed by the [OlympCron Manager EULA](https://github.com/OlympProject/olympcron-manager-release/blob/main/EULA.md).

Copyright (c) 2026 OlympStack. All rights reserved.
