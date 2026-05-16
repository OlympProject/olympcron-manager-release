# OlympCron Manager User Manual

This manual explains the main workflows in OlympCron Manager: adding servers, managing crontabs, using the visual builder, applying templates, and configuring settings.

Website: https://olympstack.com  
Support: support@olympstack.com

## 1. First Start

After launching OlympCron Manager, the main navigation appears at the bottom:

- `Servers`
- `Crontab`
- `Builder`
- `Templates`
- `Settings`

![Servers Tab](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/serversTab.png?raw=true)

Use `Servers` first. The Crontab screen requires at least one saved server to connect to.

## 2. Add a Server

Open `Servers`, then select the `+` button.

![Add Server](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/serversTabAddServer.png?raw=true)

Fill in:

| Field | Description |
| --- | --- |
| Type | `Server` for a normal target or `Jumphost` for a bastion server |
| Server Name | Friendly display name |
| Host | IP address or DNS name |
| Port | SSH port, usually `22` |
| Username | Remote SSH user |
| Authentication | `Password` or `Private Key` |
| Connect via Jump Host | Optional saved or manual jump host route |

For password authentication, enter the SSH password.

For private-key authentication, paste a private key manually. If the key is encrypted, enter the passphrase.

### First SSH Fingerprint

On the first connection, the app asks you to verify the server's SSH fingerprint. Verify it against the server before accepting. On many Linux servers you can compare with:

```bash
ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub
```

If a fingerprint changes unexpectedly, do not accept it until you know why it changed.

### OlympSuite Shared Registry

Servers are saved to a shared registry on your machine. Any server added here is automatically available in other OlympSuite apps such as OlympSSH Commander. SSH credentials are stored separately per app and are never shared.

## 3. Manage Servers

The `Servers` screen lists configured servers with authentication type and last connection time.

Common actions:

| Action | How |
| --- | --- |
| Select server | Tap a server card |
| Edit server | Open the server menu and choose `Edit` |
| Delete server | Open the server menu and choose `Delete` |

Deleting a server removes its stored credentials from this app.

## 4. Manage Crontabs

Open `Crontab` after adding at least one server.

![Crontab Jobs](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabJobs.png?raw=true)

If you have more than one server, use the server dropdown at the top to select which server to connect to. The app connects automatically and loads the remote crontab.

The crontab list shows each job with:

- Toggle switch for enabling or disabling the job
- Cron expression chip and human-readable schedule
- Command text
- Edit and delete actions

### Add a Cron Job

Tap the `+` button at the bottom right.

![Add Cron Job](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/crontTabAddCronJob.png?raw=true)

Enter the cron expression and command. Use `Open in Builder` to fill the expression using the visual builder, then return to the form with the expression pre-filled.

### Edit a Cron Job

Tap the edit icon on any job card.

![Edit Cron Job](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabEditCronJob.png?raw=true)

### Enable or Disable a Job

Use the toggle on the job card. Disabled jobs are commented out in the crontab with a `#` prefix and are not executed by the system.

### Delete a Job

Tap the delete icon and confirm. The change is staged locally until you deploy.

### Deploy Changes

Changes are staged locally until you explicitly deploy them. When you have unsaved changes, a banner appears at the top of the screen. Tap `Deploy to Server` to write all staged changes to the remote crontab using `crontab -`.

## 5. Visual Cron Builder

Open `Builder` to create cron expressions without memorizing syntax.

![Cron Builder](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronBuilderTab.png?raw=true)

The builder has five field tabs: `Minute`, `Hour`, `Day`, `Month`, `Weekday`.

For each field, choose a mode:

| Mode | Description |
| --- | --- |
| Every | Matches every value for the field (`*`) |
| Every N | Step pattern, e.g. `*/5` for every 5 minutes |
| Specific | Select exact values from a list |
| Range / Step | Set a start, end, and optional step |

The expression at the top updates as you change fields. The human-readable label below the expression describes the schedule in plain language, such as "At 03:00 AM, only on Monday".

The "Next 10 Runs" section below shows the next ten scheduled execution times.

Use the `Copy` button to copy the finished expression to the clipboard.

### Expert Mode

Toggle `Expert Mode` to edit the raw expression string directly. The expression is validated in real time.

### Open in Builder from Crontab

When editing a cron job in the Crontab screen, tap `Open in Builder` to load the current expression into the Builder tab. The Builder tab opens with the expression pre-filled so you can adjust it visually, then copy the result back.

## 6. Templates

Open `Templates` to browse ready-to-use cron job recipes.

![Templates](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/cronTabTemplates.png?raw=true)

Templates are grouped by category:

| Category | Templates |
| --- | --- |
| Backup | PostgreSQL Dump, MySQL Dump, SQLite Backup, Home Backup |
| Docker | Docker Cleanup |
| Security | Certbot Renewal |
| System | System Health Check |
| Web Server | Nginx Restart |

Each template shows the cron expression, a description, and the full command.

Available actions per template:

| Action | Result |
| --- | --- |
| Copy Expression | Copies only the cron expression to clipboard |
| Copy Full Line | Copies the complete cron line including command |
| Deploy to Server | Opens a server picker and adds the job to the selected server |

![Deploy Template](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/templateTabTemplatesDeploy.png?raw=true)

When deploying a template, select the target server in the dialog. The job is added to the remote crontab immediately. Review and adjust the command to match your server paths before deploying.

## 7. Settings

Open `Settings` for app-wide configuration.

![Settings](https://github.com/OlympProject/olympcron-manager-release/blob/main/screenshots/settingsTab.png?raw=true)

Settings areas:

| Area | Purpose |
| --- | --- |
| Appearance | Choose system, light, or dark mode; set accent colors |
| OlympSuite Sharing | Share theme settings with other OlympSuite apps on this machine |
| About | App version and license information |

### Accent Colors

Under `Appearance`, set separate accent colors for light mode and dark mode using the color swatch grid. Select `Reset` to return to the default accent color.

### OlympSuite Sharing

When enabled, theme mode and accent color settings are synchronized with other OlympSuite apps on the same machine. Disable this option to use independent appearance settings for OlympCron Manager.

## 8. Credentials and Security

Credentials behavior:

- SSH passwords, private keys, and passphrases are written to OS-backed secure storage using `flutter_secure_storage`.
- Server metadata (name, host, port, username) is stored separately from secrets.
- Credentials for OlympCron Manager are stored with an `ocm_` prefix and do not overlap with credentials from other OlympSuite apps.
- Deleting a server removes its credentials from this app.

Do not share private keys, passwords, passphrases, or screenshots that reveal sensitive infrastructure details.

## 9. Troubleshooting

### Cannot Connect to Server

Check:

- Hostname or IP address is correct.
- SSH port is correct.
- Server is reachable from your network.
- Firewall allows SSH traffic.
- Username and credentials are correct.
- Jump host configuration is correct if used.

### Fingerprint Warning

A changed fingerprint can mean:

- The server was rebuilt.
- SSH host keys were rotated.
- DNS or IP now points to another machine.
- A man-in-the-middle attack is possible.

Only accept a new fingerprint after verifying it against the server.

### Crontab Does Not Load

Check:

- The SSH user has permission to run `crontab -l` on the server.
- The server is reachable and the SSH session is active.
- The server is not a jump host type. Jump hosts require connecting through them to a target server.

### Deployed Changes Are Not Running

Check:

- The cron daemon is running on the server: `systemctl status cron` or `systemctl status crond`.
- The expression is correct. Use the Builder to verify the schedule.
- The command path is correct on the server. Test it manually in an SSH session first.
- The SSH user's crontab was deployed. Check with `crontab -l` on the server.

### Toggle Does Not Persist After Deploy

Disabled jobs use a `#` comment prefix. If the server's crontab was edited outside the app between a load and deploy, the app's staged changes overwrite the external edits. Always reload the crontab after external changes before making new edits in the app.

## 10. Support

For support, contact:

- support@olympstack.com
- contact@olympstack.com
- https://olympstack.com

Include app version, operating system, target server type, and the affected workflow. Do not send passwords, private keys, passphrases, or other secrets.

Copyright (c) 2026 OlympStack. All rights reserved.
