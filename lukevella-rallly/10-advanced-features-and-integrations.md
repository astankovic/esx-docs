---
title: "Advanced Features and Integrations"
section: "10"
slug: "advanced-features-and-integrations"
sortOrder: 20
parentSection: null
sourceFiles:
  - "apps/web/src/features/calendars/"
  - "apps/web/src/app/[locale]/(app)/(space)/settings/api-keys/"
---
This section covers **Advanced Features and Integrations**, designed for power users, team administrators, and self-hosters who want to extend functionality beyond core poll creation and voting. These tools enable seamless connections to external services, custom branding, enhanced security, and global accessibility. They build on basic account management in [User Settings and Preferences](user-settings-and-preferences) and self-hosting setups in [Self-Hosting and Administration](self-hosting-and-administration). For team-based usage, combine with features in [Spaces and Team Collaboration](spaces-and-team-collaboration).

## Overview

Advanced features provide deeper customization and connectivity, including syncing polls with calendars for reminders, generating API keys for third-party apps, moderating content in shared spaces, applying white-label branding, and supporting multiple languages. Access these via the **Account Settings** menu under **Advanced** tab or the **Space Settings** panel for team-specific options. Main capabilities include one-click integrations, toggleable moderation rules, and instant preview for branding changes.

## Calendar Connections

Connect your polls to external calendars to automatically add voting reminders, deadlines, or events. Users see a **Calendar Integrations** panel listing connected accounts with status indicators (*Connected*, *Disconnected*, or *Pending Authorization*). 

### Supported Providers

| Provider | Description | Connection Method |
|----------|-------------|-------------------|
| **Google Calendar** | Sync poll start/end dates as events with participant invites | OAuth 2.0 login |
| **Microsoft Outlook** | Add polls to shared calendars with RSVP links | OAuth or API key |
| **Apple iCal** | Export poll schedules as .ics files for import | Direct URL share |
| **Custom CalDAV** | Connect to self-hosted servers like Nextcloud | Server URL and credentials |

### Connecting a Calendar
1. Navigate to **Account Settings** > **Integrations** > **Calendar Connections**.
2. Click **Add Provider** and select from the dropdown.
3. Click **Connect** to launch the provider's authorization window (e.g., Google login prompt).
4. Grant permissions for event creation and editing.
5. Choose default options: *Auto-add poll deadlines*, *Include participant emails*, *Sync results*.
6. Click **Save**; the status updates to *Connected* with a **Disconnect** button.

> [!NOTE]  
> Connected calendars sync new polls within 5 minutes. Edit poll dates in [Creating and Sharing Polls](creating-and-sharing-polls) to trigger updates.

> [!WARNING]  
> Revoke access via the provider's security settings to prevent unintended event creation.

## API Keys

Generate secure API keys to integrate polls into external apps, websites, or automations (e.g., embedding results in dashboards or triggering votes via webhooks).

Users access the **API Keys** panel, showing a list of keys with columns for *Name*, *Created*, *Last Used*, *Permissions*, and **Revoke** button.

### Managing API Keys
1. Go to **Account Settings** > **Advanced** > **API Keys**.
2. Click **Generate New Key**.
3. Enter **Key Name** (e.g., *Slack Bot*), select **Permissions** (*Read Polls*, *Create Votes*, *Full Access*).
4. Click **Create**; copy the displayed *Key Value* (shown once only).
5. Use the key in HTTP headers: `Authorization: Bearer <key>`.

| Field | Required | Accepted Values | Description |
|-------|----------|-----------------|-------------|
| **Key Name** | Yes | Up to 50 characters, letters/numbers/hyphens | Label for identifying the key's purpose |
| **Permissions** | Yes | Read Polls / Create Votes / Manage Spaces / Full Access | Controls what actions the key allows |
| **Expires** | No | *Never* (default), 30 days, 90 days, 1 year | Auto-revokes after selected period |

> [!WARNING]  
> Store keys securely; revoked keys return 401 Unauthorized errors in integrations.

## Content Moderation

Enable automated and manual moderation for polls and comments in spaces to flag inappropriate content, spam, or violations.

The **Content Moderation** dashboard shows *Recent Flags* table, moderation stats, and toggle switches.

### Moderation Rules

| Setting | Default | Options | What It Controls |
|---------|---------|---------|------------------|
| **Auto-Flag Keywords** | Off | On/Off | Scans poll options/comments for banned words (customizable list) |
| **Profanity Filter** | On | On/Off, Sensitivity (Low/Medium/High) | Blocks/reviews explicit language |
| **Spam Detection** | On | On/Off | Limits rapid votes from same IP |
| **Manual Review Queue** | Off | On/Off | Holds new polls for admin approval |
| **Flag Notifications** | On | On/Off, Email/Slack | Alerts space owners of issues |

1. In **Space Settings** > **Moderation**, toggle rules and add **Custom Keywords** (comma-separated).
2. Click **Apply**; test with **Simulate Flag** button.
3. Review queue: Approve/Reject/Flag in the dashboard.

## White-Labeling

Customize the app's appearance for branded experiences, hiding default logos and using your domain.

The **White-Label** editor provides live preview pane, color picker, and upload zones.

| Setting | Default | Options | What It Controls |
|---------|---------|---------|------------------|
| **Logo Upload** | App default | PNG/SVG up to 5MB | Replaces header logo |
| **Primary Color** | #007BFF | HEX code | Buttons, links, accents |
| **Custom Domain** | Off | On + CNAME setup | Serves app at yourdomain.com |
| **Footer Text** | App credits | Custom text | Overrides branding notice |

1. Go to **Account Settings** > **White-Label**.
2. Upload **Logo**, pick **Primary Color**, enter **Domain**.
3. Click **Preview** and **Publish**.

> [!NOTE]  
> Custom domains require DNS CNAME to app host (instructions shown in panel).

## Multi-Language Support

Serve polls in users' preferred languages with automatic detection or manual selection.

Toggle in **Account Settings** > **Language**, with dropdown for **Default Language** and **Enabled Languages** list.

### Supported Languages

| Language | Code | Auto-Detect | RTL Support |
|----------|------|-------------|-------------|
| **English** | en | Yes | No |
| **Spanish** | es | Yes | No |
| **French** | fr | Yes | No |
| **German** | de | Yes | No |
| **Arabic** | ar | Yes | Yes |
| **Chinese (Simplified)** | zh | Yes | No |
| **Japanese** | ja | Yes | No |

1. Select languages to enable.
2. Set **Auto-Detect** based on browser locale.
3. Polls display translated UI; options remain as entered.

## Summary
- Connect calendars like **Google Calendar** for automated reminders: see [Creating and Sharing Polls](creating-and-sharing-polls) for poll scheduling.
- Generate **API Keys** for custom integrations with read/write permissions.
- Configure **Content Moderation** rules to maintain safe spaces: link with [Spaces and Team Collaboration](spaces-and-team-collaboration).
- Apply **White-Labeling** for branded deployments, preview changes live.
- Enable **Multi-Language Support** from 7+ languages with auto-detection.
For self-hosted customizations, refer to [Self-Hosting and Administration](self-hosting-and-administration). Adjust notifications for these features in [Notifications and Emails](notifications-and-emails).