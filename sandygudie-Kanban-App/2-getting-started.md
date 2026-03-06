---
title: "Getting Started"
section: "2"
slug: "getting-started"
sortOrder: 1
parentSection: null
sourceFiles:
  - "README.md"
  - "src/page/workspace/index.tsx"
  - "src/App.tsx"
---
The Getting Started section guides you through accessing the Kanban app in your web browser, creating your first workspace (which represents your organization and enables board management), and navigating to your dashboard. This is essential for new users to set up their project tracking environment quickly, with built-in validations to ensure valid data and a responsive design that works on desktop and mobile devices.

## 2.1 Accessing the App

Visit the live Kanban app at [https://kanban-management-app.netlify.app/](https://kanban-management-app.netlify.app/) in a modern web browser. The app loads with a loading spinner if content is fetching, then directs you to the workspace setup screen if no workspace exists yet. The interface adapts to your screen size, showing a mobile-optimized logo on smaller devices and a full logo on larger ones.

### Browser Compatibility

| Browser       | Minimum Version | Notes                          |
|---------------|-----------------|--------------------------------|
| Google Chrome | 90+            | Fully supported; recommended  |
| Mozilla Firefox | 85+         | Fully supported                |
| Apple Safari  | 14+            | Fully supported on macOS/iOS   |
| Microsoft Edge | 90+            | Fully supported                |

> [!NOTE]  
> Enable JavaScript and avoid private browsing modes for full functionality, as the app persists your workspace and theme settings across sessions.

The header bar appears at the top of every screen, featuring:
- **App logo** (left side, clickable on desktop): Returns to the main workspace view.
- **Title** (e.g., *No Workspace* or *Workspace*): Indicates your current setup status.
- **Theme toggle** (right side): Switches between *light* and *dark* modes; defaults to *dark* based on your system preferences or browser settings, and persists after refresh.

## 2.2 First Workspace Setup

On first visit (or if no workspace exists), you see the workspace creation screen with a welcome message: "Welcome to Kanban! Get started by creating a workspace!" A slideshow of promotional images (project starting, todo graphics) plays automatically on desktop screens wider than a tablet. On mobile, the images are hidden to prioritize the form.

If a workspace already exists:
- A centered card displays your current workspace details: a placeholder image, **organization name**, and **email**.
- **Available workspace** link below the details: Click to go to the [Dashboard and Navigation](dashboard-and-navigation).
- **Add Workspace** button: Opens the creation form to add another (shows a back arrow button to return to the list).

### Workspace Creation Form Fields

| Field Name            | Description                                      | Required | Accepted Values/Format                  | What Happens on Change/Submit |
|-----------------------|--------------------------------------------------|----------|-----------------------------------------|------------------------------|
| **Organization's name** | Your organization's or team's name (e.g., "xyz Corp") | Yes     | Text; 5-25 characters                   | Real-time placeholder shown; validation error if too short/long |
| **Email**             | Contact email for the workspace (e.g., "team@xyz.com") | Yes     | Valid email format                      | Real-time placeholder shown; validation error if invalid |

- Errors appear below each field as red text (e.g., "Required" or "At least 5 characters and not more than 25").
- **Create Workspace** button (full-width, blue): Submits the form. On success, saves the workspace and redirects to the [Dashboard and Navigation](dashboard-and-navigation); no confirmation popup, but the URL changes to `/dashboard`.

### Step-by-Step: Creating Your First Workspace

1. Visit the app URL in your browser.
2. If prompted, fill in the **Organization's name** (at least 5 characters, max 25).
3. Enter a valid **Email**.
4. Click **Create Workspace**.
5. You are automatically taken to the dashboard, where you can create your first board (see [Managing Boards](managing-boards)).

```mermaid
sequenceDiagram
    participant User
    participant App
    User->>App: Visit app URL
    App->>User: Show workspace screen (no workspace detected)
    User->>App: Fill form fields and click Create Workspace
    App->>User: Validate fields; on success, save workspace
    App->>User: Redirect to dashboard with boards ready for setup
```

> [!WARNING]  
> Invalid submissions (e.g., short name or bad email) show field-specific errors but do not submit—correct and retry. Changes persist after browser refresh once created.

This setup connects directly to the [Dashboard and Navigation](dashboard-and-navigation), where your sidebar lists boards, and you can proceed to [Managing Boards](managing-boards) for initial board creation. Theme and workspace data save automatically for future sessions.