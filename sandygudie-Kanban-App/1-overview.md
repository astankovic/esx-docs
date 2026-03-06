---
title: "Overview"
section: "1"
slug: "overview"
sortOrder: 0
parentSection: null
sourceFiles:
  - "README.md"
  - "src/page/home/index.tsx"
---
The Kanban Board app provides a visual, intuitive way for teams and individuals to manage projects, track tasks, and monitor progress, much like Trello or Asana. It helps users organize work into customizable boards with columns representing workflow stages (e.g., *To Do*, *In Progress*, *Done*), supports drag-and-drop task movement for quick status updates, includes subtasks for breaking down complex work, and persists all changes even after refreshing the browser. Ideal for personal task tracking or collaborative projects, it features responsive design for any device, light/dark theme options, and simple navigation to keep you focused on productivity.

```mermaid
flowchart TD
    HomePage[Landing Page] -->|Click **Get Started*** Workspace[Enter App Workspace]
    Workspace --> Dashboard[Dashboard View]
    Dashboard --> Boards[Select or Create Board]
    Boards -->|Drag tasks or add new| Columns[Manage Columns and Tasks]
```

## Getting Started

### Accessing the App
1. Open your web browser and navigate to the live site.
2. On the landing page, you'll see a prominent hero section with the app logo, a tagline like "Effortlessly Manage Your Projects," and a description of visual task management.
3. Scroll to explore features like simplified board views, drag-and-drop, and theme toggles.
4. Click the **Get Started** button (styled in primary color) to enter the app workspace—no login required.

> [!NOTE]  
> The app works entirely in your browser and saves data locally, so your boards are private to your device.

### First Workspace Setup
1. After clicking **Get Started**, you'll land on the **Dashboard**.
2. If no boards exist, a prompt or empty state appears encouraging you to create your first board.
3. Use the sidebar or header **+ New Board** button to set up your initial project (see [Managing Boards](managing-boards) for details).
4. Once a board is created, it loads with default columns, ready for tasks.

Expected result: A fully functional board view with columns like *To Do*, *In Progress*, and *Done*, where you can immediately add tasks.

## Dashboard and Navigation

The **Dashboard** is your central hub, showing a sidebar on the left for quick board access and the main area displaying the selected board's columns and tasks. Navigation is streamlined for efficiency.

### Sidebar Board List
- Displays a vertical list of all your boards, each with its *board name* as a clickable title.
- **+ New Board** button at the top: Opens a form to create a new board.
- **Hide/Show Sidebar** toggle (often an icon like three lines or an arrow in the header): Collapses the sidebar to expand the board area; click again to expand.
- Hover over a board name for options like **Edit** or **Delete**.
- Select a board to load it in the main view.

### Header Controls
The top header bar spans the screen with these interactive elements:
- App logo (left): Returns to dashboard if on a board.
- **Theme Toggle** (sun/moon icon): Switches between *light* and *dark* modes; persists your choice.
- **Sidebar Toggle** (hamburger icon): Hides/shows the sidebar.
- Search or board selector dropdown (if multiple boards): Quickly switch boards.
- Hover states highlight all buttons for better usability.

> [!WARNING]  
> Changes like theme or sidebar state save automatically but are local to your browser.

## Managing Boards

Boards represent individual projects. Switch between them via the sidebar, and all data persists across sessions.

### Creating a Board
1. Click **+ New Board** in the sidebar or header.
2. A modal or inline form appears with the following fields:

| Field          | Description                          | Required | Format/Values                  |
|----------------|--------------------------------------|----------|--------------------------------|
| **Board Name** | Unique title for your project board | Yes      | Text (1-50 characters); no special chars that break display |

3. Enter a name (e.g., *Website Redesign*).
4. Click **Create** or **Save**.
5. The new board appears in the sidebar list and loads automatically with starter columns.

Error messages:
- "Board name is required" if empty.
- "Name too long" if over limit.

Expected output: New board in sidebar, main view shows empty columns ready for tasks.

### Editing and Deleting Boards
1. Hover over a board name in the sidebar and click **Edit** (pencil icon).
2. Update the **Board Name** field and click **Save**.
3. For deletion: Click **Delete** (trash icon), confirm in the popup (*Are you sure? This can't be undone.*).
   
Expected result: Changes update instantly; deletion removes the board and selects another (or shows empty dashboard).

## Managing Columns

Columns define workflow stages on a board (e.g., *To Do*, *In Progress*, *Done*). Drag tasks between them to update status.

### Adding Columns
1. At the end of the board (or via **+ Add Column** button on the right), click the **+** icon.
2. Enter a **Column Name** (text field, required, 1-30 chars).
3. Click **Add** or press Enter.

Error: "Column name required" if blank.

Result: New empty column appears, draggable for reordering.

### Editing Column Names
1. Hover over a column header and click the edit icon (pencil).
2. Type new name in the inline field.
3. Press Enter or click outside to save.

> [!NOTE]  
> Columns auto-adjust width based on content; drag header to reorder.

## Creating and Managing Tasks

Tasks are cards placed in columns. Drag them vertically to reorder within a column or horizontally to move between columns—status updates instantly.

### Adding Tasks
1. Hover over a column and click **+ Add Task** (at bottom or top).
2. Form opens with fields:

| Field             | Description                           | Required | Format/Values             |
|-------------------|---------------------------------------|----------|---------------------------|
| **Task Title**    | Short summary of the work             | Yes      | Text (1-100 chars)        |
| **Description**   | Detailed notes or instructions        | No       | Multi-line text           |

3. Fill details and click **Create Task**.
4. Task appears as a card with title visible; hover for gripper icon to drag.

Errors: "Title is required"; validation highlights invalid fields in red.

### Deleting Tasks
1. Hover over a task card, click **Delete** (trash icon, often top-right).
2. Confirm in popup.

Result: Task removed immediately; subtasks lost if any.

## Task Details and Subtasks

### Viewing Task Details
1. Click any task card to open a details panel or modal.
2. View **Task Title**, **Description**, column position, and subtask list.
3. Drag from here mirrors board behavior.
4. Close by clicking outside or **X**.

### Managing Subtasks
In task details:
1. **+ Add Subtask** button opens a text field.
2. Enter subtask name (required, text), click **Add**.
3. Subtasks show as a checklist with checkboxes.
4. Check to mark *complete* (strikethrough); progress bar shows completion % at top of task card on board.

Result: Completed subtasks update task visuals; full completion may style the card differently (e.g., green tint).

## UI Customization and Controls

- **Theme Toggle**: Light (default, bright backgrounds) or *dark* (low-light for eyes); applies site-wide.
- **Sidebar Visibility**: Toggle to focus on boards during heavy task management.
- Responsive layout: On mobile, sidebar collapses by default; columns stack vertically; pinch-zoom for drags.
- Hover states: Buttons glow, cards lift slightly for feedback.
- All interactions include smooth animations for drag-drop and modals.

> [!TIP]  
> Refresh anytime—data persists. Use *dark* theme for late-night sessions and hide sidebar for full-screen boards.

| Option              | Controls                          | Possible Values     | Default    |
|---------------------|-----------------------------------|---------------------|------------|
| **Theme**           | Overall color scheme              | *Light*, *Dark*     | *Light*   |
| **Sidebar**         | Left panel visibility             | *Shown*, *Hidden*   | *Shown*   |