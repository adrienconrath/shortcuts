# Shortcuts Cheat Sheet Manager

Modify the shortcuts cheat sheet by editing the `SHORTCUTS_DATA` object in `index.html`.

## How it works

The file `index.html` contains an inline JavaScript object called `SHORTCUTS_DATA` that holds all shortcut categories and items. This is the single source of truth — there is no external JSON file or database.

## Data structure

```javascript
const SHORTCUTS_DATA = {
  "categories": [
    {
      "name": "Category Name",
      "color": "#hex",
      "items": [
        // Keyboard shortcut:
        { "description": "What it does", "keys": { "modifiers": ["Cmd"], "key": "B" } },
        // Text command:
        { "description": "What it does", "command": "/some-command" },
        // Both keyboard shortcut and command:
        { "description": "What it does", "keys": { "modifiers": ["Cmd"], "key": "Y" }, "command": "/accept" }
      ]
    }
  ]
};
```

## Rules

1. **Always read `index.html` first** to see the current state of `SHORTCUTS_DATA` before making changes.
2. **Use the Edit tool** to modify the `SHORTCUTS_DATA` object. Never rewrite the entire file.
3. **Valid modifiers**: `"Cmd"`, `"Ctrl"`, `"Alt"`, `"Shift"`, `"Fn"`
4. **Available colors**: `#4a90d9` (blue), `#e06c75` (red), `#98c379` (green), `#e5c07b` (yellow), `#c678dd` (purple), `#56b6c2` (teal), `#d19a66` (orange), `#be5046` (dark red)
5. Items can have `keys`, `command`, or both. At least one must be present.
6. Keep descriptions concise.

## Handling user requests

- **"add [shortcut] to [category]"**: Add a new item to the specified category. Create the category if it doesn't exist.
- **"remove [shortcut]"**: Remove the matching item.
- **"add category [name]"**: Add a new empty category with a color.
- **"remove category [name]"**: Remove the entire category.
- **"move [shortcut] to [category]"**: Remove from current category, add to target.
- **"rename [category]"**: Change the category name.
- **"list"** or no arguments: Read and display all current shortcuts.

The user said: $ARGUMENTS
