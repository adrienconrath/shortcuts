# Shortcuts Cheat Sheet

A single-file, static HTML page that displays keyboard shortcuts and commands organized by category (Xcode, VSCode, Claude Code, Git, etc.).

## Architecture

- **`index.html`** — The entire app. Contains CSS, HTML, and JavaScript in one file.
- **No server, no build step, no dependencies.** Open the file directly in a browser.
- Shortcut data lives inline in the `SHORTCUTS_DATA` JavaScript object inside `index.html`.
- The page is read-only — there is no UI to edit shortcuts. All modifications are done by asking Claude to edit `index.html`.
- Hosted via GitHub Pages at https://adrienconrath.github.io/shortcuts/

## Modifying shortcuts

Ask Claude to edit the `SHORTCUTS_DATA` object in `index.html`. Examples:

- "Add Cmd+Shift+F Find and replace to Xcode"
- "Remove Stage all and commit from Git"
- "Add a new Terminal category with color teal"
- "List all current shortcuts"

Always read `index.html` first, then use the Edit tool to modify just the `SHORTCUTS_DATA` object.

## Data format

Each category has a `name`, `color`, and `items` array. Each item has a `description` and either `keys`, `command`, or both:

```javascript
{ "description": "Build project", "keys": { "modifiers": ["Cmd"], "key": "B" } }
{ "description": "Show help", "command": "/help" }
```

Valid modifiers: `Cmd`, `Ctrl`, `Alt`, `Shift`, `Fn`
Available colors: `#4a90d9` (blue), `#e06c75` (red), `#98c379` (green), `#e5c07b` (yellow), `#c678dd` (purple), `#56b6c2` (teal), `#d19a66` (orange), `#be5046` (dark red)
