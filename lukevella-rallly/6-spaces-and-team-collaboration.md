---
title: "Spaces and Team Collaboration"
section: "6"
slug: "spaces-and-team-collaboration"
sortOrder: 11
parentSection: null
sourceFiles:
  - "apps/web/src/app/[locale]/(app)/(space)/"
  - "apps/web/src/features/space/"
  - "apps/docs/spaces/"
---
This section covers **Spaces**, collaborative workspaces where teams organize and manage polls and events together. Designed for users on **Plus**, **Organization**, or **Enterprise** tiers (or licensed self-hosted instances), Spaces enable member invitations, role assignments, seat management, and shared views of team activity. Polls created in a Space are scoped to that workspace for better organization, integrating seamlessly with poll creation and management workflows. For licensing requirements and tiers, see [Billing and Subscriptions](billing-and-subscriptions). For self-hosted setup including license activation, see [Self-Hosting and Administration](self-hosting-and-administration) > [Control Panel](control-panel). Related: [Creating and Sharing Polls](creating-and-sharing-polls), [Managing Polls](managing-polls).

## Overview
**Spaces** provide a dedicated area for teams to collaborate on scheduling polls without mixing personal and group content. Key capabilities include:
- Creating unlimited Spaces (seat limits apply per Space).
- Inviting registered users as members with assigned roles.
- Viewing a **Space Dashboard** with all polls, events, and member activity.
- Enforcing seat limits based on your license tier to manage team scale.

Access Spaces from the main navigation menu via the **Spaces** tab, where you'll see a list of your personal Spaces (as Owner) and those you're invited to.

## Creating a Space
1. Click **New Space** in the **Spaces** tab.
2. Enter a **Space Name** (e.g., *Marketing Team*) and optional **Description**.
3. Click **Create Space**.

The new Space appears in your list, with you as the **Owner**. Polls created here are automatically organized within it.

> [!NOTE]  
> **Personal** tier users see a prompt to upgrade, as Spaces require multi-user licensing.

## Managing Members
Invite and manage team members directly in each Space. Only **Owners** can add/remove members or change roles.

### Inviting Members
1. Open a Space and click **Manage Members**.
2. In the **Invite Member** section, enter the email of a registered user.
3. Select a **Role** from the dropdown.
4. Click **Send Invite**.

Invited users receive an email notification and can join via **Spaces** > **Pending Invites**.

### Member Roles and Permissions
Use the table below to assign roles based on needed access.

| Role    | Default | Permissions |
|---------|---------|-------------```mermaid
graph TB
    subgraph "Owner"
        A[Full access: Create/edit/delete polls<br/>Invite/remove members<br/>Change roles<br/>View dashboard]
    end
    subgraph "Member"
        B[Create/edit own polls<br/>View all polls<br/>No member management]
    end
    subgraph "Viewer"
        C[View polls and results only<br/>No editing or creation]
    end
    Owner[Assign Owner] -->|"Promote to Owner"| Member
    Owner -->|"Demote to Member<br/>or Viewer"| Member
    Owner -->|"Remove"| Member
    Owner -->|"Remove"| Viewer
```

### Removing or Changing Roles
1. In **Manage Members**, click the **role dropdown** or **Remove** button next to a member.
2. Confirm the action.

> [!WARNING]  
> Removing a member revokes their access immediately; they lose visibility of Space polls.

## Space Dashboard
Each Space has a dedicated **Dashboard** showing:
- List of all polls with status (*Open*, *Closed*, *Scheduled*).
- Recent activity feed (e.g., *User X voted on Poll Y*).
- Member list summary and seat usage (e.g., *4/5 seats used*).

Click any poll for details or **New Poll** to create one scoped to the Space. Filter by **Status** or search by name.

## Seat Limits and Licensing
Seats enforce collaboration scale per your tier:

| Tier          | Max Users per Instance | Max Seats per Space |
|---------------|------------------------|---------------------|
| **Personal** | 1                     | 1 (no invites)     |
| **Plus**     | 5                     | 5                  |
| **Organization** | 50                | 50                 |
| **Enterprise**| 50+ (custom)         | 100                |

Only registered Space members count toward limits; guest poll participants do not.

To check or upgrade:
1. Admins: Go to **Control Panel** > **License**.
2. Enter/activate your key and click **Activate**.

## Troubleshooting
Common issues and messages:

| Message | Severity | Meaning |
|---------|----------|---------|
| "Upgrade required to create Spaces" | Info | Your license doesn't support multi-user features. Visit [Billing and Subscriptions](billing-and-subscriptions) or activate a key in [Control Panel](control-panel). |
| "Space full: X/Y seats used" | Warning | No more invites possible. Upgrade tier or remove members. Instance continues working (honor system). |
| "User not found" on invite | Error | Entered email isn't a registered user. Ask them to sign up first via [Account Creation and Login](account-creation-and-login). |

## Summary
- Create **Spaces** to organize team polls, with **Owner**/**Member**/**Viewer** roles controlling access.
- Manage invites and seats via **Manage Members**; view activity on the **Space Dashboard**.
- License tiers limit scale—activate in **Control Panel** for self-hosted.
- Integrates with [Creating and Sharing Polls](creating-and-sharing-polls), [Managing Polls](managing-polls), and [Billing and Subscriptions](billing-and-subscriptions) for full team workflows.
- For admin controls, see [Self-Hosting and Administration](self-hosting-and-administration) > [Control Panel](control-panel).