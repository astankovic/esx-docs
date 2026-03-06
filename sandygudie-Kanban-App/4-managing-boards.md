---
title: "Managing Boards"
section: "4"
slug: "managing-boards"
sortOrder: 7
parentSection: null
sourceFiles:
  - "src/components/Board/index.tsx"
  - "src/components/Board/AddBoard.tsx"
---
Boards allow you to organize your projects into customizable structures with columns for different stages, such as "Todo", "In Progress", and "Done". Managing boards involves creating new ones when starting a project, editing existing ones to rename or adjust columns, deleting unused boards, and switching between them via the sidebar. This keeps your workspace focused and adaptable to different workflows. When no boards exist in the current workspace, a dedicated empty state prompts you to create your first one.

## Empty Board State
If no board is active in the current workspace, the main area displays a centered panel with an illustration of an empty project, the heading **Create your first board**, and the message "You don't have any board for this workspace". A prominent **Add New Board** button invites you to get started.

- Click **Add New Board** to open the board creation modal.

This state ensures you can't miss the need to set up your first board and connects directly to the creation workflow.

## Creating a Board
Create a new board to define a project's name and initial columns. Boards must have a unique name and at least one column.

### Step-by-Step: Creating a Board
1. In the empty board state or from the sidebar (**3.1. Sidebar Board List**), click **Add New Board**.
2. In the modal titled **Add New Board**, fill in the **Name** field.
3. Add columns by clicking **+ Add New Column** (repeat as needed; at least one is required).
4. Enter a name for each column (e.g., "Todo", "Progress", "Done").
5. Click **Create Board** to save.
6. The modal closes, the new board becomes active, and its columns appear in the main area (**5. Managing Columns** for further adjustments).

### Board Creation Form Fields

| Field/Control | Description | Required? | Accepted Values/Format | What Happens on Change/Submit |
|---------------|-------------|-----------|-------------------------|-------------------------------|
| **Name** | The board's title, displayed in the sidebar and header. | Yes | Text string, 5-15 characters (e.g., "Development", "Marketing"). Duplicates not allowed within the workspace. | Updates the preview; invalid length shows error "At least 5 characters and not more than 15"; duplicate triggers a toast notification "Board already exist." with red error styling at top-center for 2 seconds. |
| **Columns** section | List of stages/phases for tasks. Starts empty. | Yes (min 1) | Dynamic list; each item has a **name** subfield (text, required, e.g., "Todo"). Use **+ Add New Column** button to add; drag or edit to reorder/remove individual ones. | Adds editable input for new column; error "Add a column." if none present on submit. New board loads with empty task lists in each column. |

> [!NOTE]  
> Column names can be edited later directly on the board (**5.2. Editing Column Names**). Newly created boards auto-activate and replace the empty state.

```mermaid
sequenceDiagram
    participant User
    participant UI as Main Area
    participant Modal as Add Board Modal
    User->>UI: Views empty state or clicks Add New Board
    UI->>+Modal: Opens form
    User->>Modal: Enters Name & adds columns
    User->>Modal: Clicks Create Board
    Modal->>-UI: Closes; new board active with columns
    Note over UI: Columns ready for tasks
```

## Editing a Board
Edit an active board to update its name or columns without losing tasks. Access via sidebar (**3.1. Sidebar Board List**) or header (**3.2. Header Controls**) edit options.

### Step-by-Step: Editing a Board
1. Switch to the board you want to edit (click its name in the sidebar).
2. Click the edit icon or option for that board.
3. The modal opens titled **Edit Board**, pre-filled with current values.
4. Modify the **Name** or columns (add/remove/edit as in creation).
5. Click **Update Board** to apply changes.
6. Modal closes; updated board remains active.

The same form fields and validation apply as in creation. Changes persist across sessions and don't affect tasks.

## Deleting a Board
Delete unused boards to declutter your workspace. This permanently removes the board, its columns, and all tasks.

### Step-by-Step: Deleting a Board
1. In the sidebar (**3.1. Sidebar Board List**), find the board and click its delete icon (trash bin).
2. Confirm the action in the prompt.
3. The board is removed; if it was active, the app returns to the empty state or switches to another board.

> [!WARNING]  
> Deletion is irreversible and clears all associated data. Export tasks first if needed.

## Switching Boards
Easily move between boards to manage multiple projects.

- In the sidebar (**3.1. Sidebar Board List**), click any board name.
- The selected board activates, displaying its columns and tasks in the main area.
- The header (**3.2. Header Controls**) shows the current board's name.

This integrates with task management (**6. Creating and Managing Tasks**) and customization (**8. UI Customization and Controls**).