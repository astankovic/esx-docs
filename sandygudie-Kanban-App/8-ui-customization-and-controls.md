---
title: "UI Customization and Controls"
section: "8"
slug: "ui-customization-and-controls"
sortOrder: 19
parentSection: null
sourceFiles:
  - "src/components/ToggleBtn/index.tsx"
  - "src/components/Header.tsx"
  - "src/components/SideBar/index.tsx"
---
UI Customization and Controls allow you to personalize your viewing experience, improve usability on different devices, and reduce eye strain. You can switch between light and dark themes, show or hide the sidebar for more board space, enter fullscreen mode for immersion, and benefit from automatic adaptations for mobile or desktop screens. Hover effects provide visual feedback on interactive elements like buttons.

## Available UI Toggles

These toggles are accessible from the header bar at the top of the screen. They update instantly and persist across sessions where supported.

| Toggle          | Location                  | Icon(s) Displayed                  | Possible States          | Default State | Effect When Toggled |
|-----------------|---------------------------|------------------------------------|--------------------------|---------------|---------------------|
| **Theme**      | Right side of header     | Sun icon (light), Moon icon (dark) | *light*, *dark*         | *dark*       | Changes background, text, and accent colors across the entire app; saves your preference for future visits. |
| **Fullscreen** | Right side of header, before theme toggle | Expand icon (normal), Compress icon (fullscreen) | *normal*, *fullscreen* | *normal*     | Expands the app to fill your entire screen, hiding browser chrome; exits on toggle or Esc key. |
| **Sidebar**    | Top-right corner of sidebar panel | Collapse arrow icon               | *shown*, *hidden*       | *shown* (desktop), *hidden* (mobile) | Slides the sidebar in or out; on mobile, it overlays the board area when shown. |

> [!NOTE]  
> Theme and fullscreen states apply globally to the app. Sidebar state is device-aware and resets on window resize.

## Switching Themes

1. Locate the theme button in the upper-right corner of the header—it shows a sun icon if currently in light mode or a moon icon if in dark mode.
2. Click the button.
3. The app immediately switches themes: light mode uses white backgrounds with dark text, while dark mode uses dark backgrounds with light text.
4. Your choice is remembered for next time you open the app.

Expected result: All boards, tasks, sidebar, and modals update colors instantly. No data is affected.

> [!WARNING]  
> If the theme does not persist, check your browser's local storage settings or clear cache and reload.

## Managing Sidebar Visibility

The sidebar lists your boards (3.1. Sidebar Board List) and is always visible on larger screens but collapsible for focus on boards.

### On Desktop (wider screens)
- The sidebar is fixed on the left by default.
- Click the **Hide Sidebar** button (collapse arrow icon) in the top-right of the sidebar.
- The sidebar slides out of view, expanding the board area.
- To show it again, click the **Show Sidebar** button that appears in the same spot or resize your window wider.

### On Mobile or Narrow Screens
1. Tap the menu icon (if visible) or the board list area to expand the sidebar overlay.
2. Use the **Hide Sidebar** button to collapse it.
3. The app automatically hides it to prioritize board content.

Expected result: More space for columns and tasks (5. Managing Columns) when hidden; quick access to board switching when shown.

## Entering Fullscreen Mode

1. Find the fullscreen button in the header, next to the theme toggle—it shows an expand icon when not in fullscreen.
2. Click the button.
3. The app expands to fullscreen, removing browser toolbars and tabs.
4. Click the button again (now a compress icon) or press Esc to exit.

Expected result: Immersive view ideal for managing tasks (6. Creating and Managing Tasks) or details (7. Task Details and Subtasks). Works best with boards that have columns.

> [!NOTE]  
> Fullscreen requires browser permission; if blocked, check your site settings.

## Responsive Layout for Devices

The app automatically adjusts for your screen size without manual setup:

- **Desktop/Widescreen**: Full sidebar, header with all controls visible, ample space for multiple columns.
- **Tablet/Narrow Desktop**: Sidebar remains but controls compact; some text truncates if too long.
- **Mobile/Phone**:
  - Compact header with logo icon instead of full logo.
  - Sidebar hidden by default, opens as overlay on tap.
  - **Add Task** button simplifies to icon-only.
  - Workspace menu (3.2. Header Controls) shows profile details on hover/tap.

Resize your browser window to see changes live. No configuration needed—layout prioritizes touch-friendly interactions on mobile.

## Hover and Visual Feedback

Interactive elements respond to your mouse or touch for better usability:

- Buttons (e.g., **Add New Board**, theme toggle) lighten or highlight on hover.
- Board list items in the sidebar show a vertical ellipsis (...) for menu options on hover.
- Active boards highlight with a colored right border and white text.

These subtle animations confirm your actions and guide navigation, especially when switching boards or opening popups.

> [!TIP]  
> On touch devices, long-press equivalents trigger hover states for menus like workspace or board options.