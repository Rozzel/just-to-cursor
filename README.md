# Justfile for Cursor

Justfile language support for Cursor.

Copy the `local.just-file-1.0.0` folder into:

- macOS / Linux: `~/.cursor/extensions/`
- Windows: `%USERPROFILE%\.cursor\extensions\`

Open `extensions.json` in that same directory and add this object to the array. Set `location.path` to the absolute path of the copied folder.

```json
{
  "identifier": {
    "id": "local.just-file",
    "uuid": "7c3e9f12-4a81-4d6b-9e20-b4c81a0d9170"
  },
  "version": "1.0.0",
  "location": {
    "$mid": 1,
    "path": "/Users/YOUR_USERNAME/.cursor/extensions/local.just-file-1.0.0",
    "scheme": "file"
  },
  "relativeLocation": "local.just-file-1.0.0",
  "metadata": {
    "id": "7c3e9f12-4a81-4d6b-9e20-b4c81a0d9170",
    "publisherId": "7c3e9f12-4a81-4d6b-9e20-b4c81a0d9170",
    "publisherDisplayName": "local",
    "source": "resource",
    "pinned": true
  }
}
```

On Linux the path is `/home/YOUR_USERNAME/.cursor/extensions/local.just-file-1.0.0`.  
On Windows it is `C:\\Users\\YOUR_USERNAME\\.cursor\\extensions\\local.just-file-1.0.0`.

> Reload Cursor: Command Palette → `Developer: Reload Window` (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows and Linux).
