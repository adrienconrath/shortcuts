# Shortcuts Cheat Sheet

A single-file, static HTML page that displays keyboard shortcuts and commands organized by category (Xcode, VSCode, Claude Code, Git, etc.).

## Architecture

- **`index.html`** — The entire app. Contains CSS, HTML, and JavaScript in one file.
- **No server, no build step, no dependencies.** Open the file directly in a browser.
- Shortcut data lives inline in the `SHORTCUTS_DATA` JavaScript object inside `index.html`.
- The page is read-only — there is no UI to edit shortcuts. All modifications are done by asking Claude to edit `index.html`.

## Modifying shortcuts

Use the `/shortcuts` skill to add, remove, or modify shortcuts. Examples:

```
/shortcuts add Cmd+Shift+F "Find and replace" to Xcode
/shortcuts remove "Stage all and commit" from Git
/shortcuts add category "Terminal" with color teal
/shortcuts list
```

The skill edits the `SHORTCUTS_DATA` object in `index.html` directly using the Edit tool.

## Data format

Each category has a `name`, `color`, and `items` array. Each item has a `description` and either `keys`, `command`, or both:

```javascript
{ "description": "Build project", "keys": { "modifiers": ["Cmd"], "key": "B" } }
{ "description": "Show help", "command": "/help" }
```

Valid modifiers: `Cmd`, `Ctrl`, `Alt`, `Shift`, `Fn`
Available colors: `#4a90d9` (blue), `#e06c75` (red), `#98c379` (green), `#e5c07b` (yellow), `#c678dd` (purple), `#56b6c2` (teal), `#d19a66` (orange), `#be5046` (dark red)
