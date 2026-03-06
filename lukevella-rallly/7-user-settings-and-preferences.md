---
title: "User Settings and Preferences"
section: "7"
slug: "user-settings-and-preferences"
sortOrder: 14
parentSection: null
sourceFiles:
  - "apps/web/src/app/[locale]/(app)/(space)/settings/"
  - "apps/web/src/features/user/"
---
This section covers **User Settings and Preferences**, the central place for personalizing your account information, securing your access, and adjusting how the app looks and behaves. It's designed for all users—from individuals creating personal polls to team members in shared **Spaces**—to make the platform feel tailored to their needs. Changes here affect your experience across polls, voting, collaboration, and notifications throughout the app. For account basics, see [Account Creation and Login](account-creation-and-login). For notification specifics, see [Notifications and Emails](notifications-and-emails). Related team settings appear in [Managing Members](managing-members) and [Space Dashboard](space-dashboard).

## Overview

**User Settings and Preferences** provides tabs or sections for managing your profile details, updating security credentials, selecting display preferences like language and theme, and controlling notifications. Access it via your profile icon in the top-right corner, then select **Settings** from the dropdown menu. All changes save automatically after confirmation, with previews where applicable (e.g., theme switches).

## Profile Management

Update your personal information visible to others in polls, **Spaces**, and shared results.

### Steps to Edit Profile
1. Click your **profile icon** (top-right) > **Settings**.
2. Select the **Profile** tab.
3. Modify fields as needed.
4. Click **Save Changes** (bottom of form).

| Field | Required | Accepted Values | Description |
|-------|----------|-----------------|-------------|
| **Full Name** | Yes | Up to 100 characters, letters, spaces, hyphens | Your display name in polls, results, and **Spaces**. Changes appear immediately in new views. |
| **Profile Picture** | No | Image files (PNG, JPG, GIF up to 5MB), or Gravatar link | Upload or link an avatar; crops to circular. Updates across the app after save. Default: initial of **Full Name**. |
| **Email Address** | Yes | Valid email format (e.g., *user@example.com*) | Primary contact for notifications, invites, and recovery. Must verify new emails via sent link. |

> [!NOTE] Profile changes sync to all your polls and **Spaces** but do not retroactively update past results.

## Security Settings

Manage password and session controls to keep your account safe.

### Steps to Change Password
1. In **Settings**, go to **Security** tab.
2. Enter **Current Password**.
3. Fill **New Password** and **Confirm New Password**.
4. Click **Update Password**.

| Field | Required | Accepted Values | Description |
|-------|----------|-----------------|-------------|
| **Current Password** | Yes | Your existing password | Verifies identity before changes. |
| **New Password** | Yes | 8+ characters, mix of letters/numbers/symbols | Strength indicator shows below field (Weak/Medium/Strong). |
| **Confirm New Password** | Yes | Must match **New Password** | Ensures no typos. |

Additional controls:
- **Active Sessions**: List of devices/browsers logged in. Click **Log Out** next to any to revoke.
- **Two-Factor Authentication** (if enabled in billing): Toggle **Enable 2FA**; scan QR or enter backup codes.

> [!WARNING] Logging out all sessions affects all devices—relogin required everywhere.

## Preferences

Customize appearance, language, and time handling for your view of the app.

### Steps to Update Preferences
1. In **Settings**, select **Preferences** tab.
2. Adjust toggles, dropdowns, or inputs.
3. Changes apply instantly (e.g., theme) or on next page load (e.g., language).

| Setting | Default | Options | What It Controls |
|---------|---------|---------|------------------|
| **Language** | *Browser default* (e.g., English) | Dropdown: English, Español, Français, Deutsch, etc. (20+ languages) | App interface text, poll labels, and emails. |
| **Theme** | *Light* | Light, Dark, Auto (follows OS) | Overall color scheme; preview swatch updates live. |
| **Timezone** | *Browser timezone* (e.g., UTC) | Dropdown: 500+ zones (e.g., *America/New_York*) | Poll deadlines, results timestamps, and schedules. |
| **Date Format** | *MM/DD/YYYY* | Short (MM/DD/YY), Long (MMMM DD, YYYY), ISO (YYYY-MM-DD) | How dates appear in polls, dashboards, and exports. |

## Notifications

Control email and in-app alerts for poll activity, invites, and updates. Detailed options in [Notifications and Emails](notifications-and-emails).

- Toggle **Email Notifications** on/off.
- Per-category checkboxes: Poll Votes, Space Invites, Results Updates.

## Troubleshooting

Common issues and resolutions:

| Message | Severity | Meaning |
|---------|----------|---------|
| "Email already in use" | Error | Another account uses this email. Use a different one or merge accounts via support. |
| "Password too weak" | Warning | New password lacks strength. Add numbers/symbols and retry. |
| "Picture upload failed" | Error | File too large or unsupported. Resize under 5MB, try PNG/JPG. |
| "Timezone not applied" | Info | Clear browser cache or refresh; affects new sessions only. |

## Summary
- Manage **Profile** (**Full Name**, **Profile Picture**, **Email**) to personalize your identity across polls and **Spaces**.
- Secure access via **Security** tab with password updates and session management.
- Tailor your view with **Preferences** (**Language**, **Theme**, **Timezone**, **Date Format**).
- Preview and save changes instantly where possible; verify emails for critical updates.
- For deeper notification controls, see [Notifications and Emails](notifications-and-emails). Connects to [Account Creation and Login](account-creation-and-login) for setup and [Billing and Subscriptions](billing-and-subscriptions) for advanced security like 2FA. For team-wide prefs, check [Managing Members](managing-members).