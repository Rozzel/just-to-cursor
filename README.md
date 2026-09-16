# Justfile for Cursor

> **Agent instructions:** This README is a step-by-step install guide for Cursor agents. Follow every step in order. Do not skip verification. Do not leave placeholders like `YOUR_USERNAME` in paths.

Justfile language support for Cursor.

## Install (agents)

### Prerequisites

- Working directory: this repository root (the folder that contains `local.just-file-1.0.0/` and this `README.md`).
- Target directory: Cursor user extensions folder:
  - macOS / Linux: `~/.cursor/extensions/`
  - Windows: `%USERPROFILE%\.cursor\extensions\`
- Always expand `~` / `%USERPROFILE%` to a real absolute path before writing anything.

### Step 1 — Copy the extension folder

Copy `local.just-file-1.0.0/` into the extensions directory.

Destination example (macOS):

```text
/Users/<username>/.cursor/extensions/local.just-file-1.0.0
```

Rules:

1. Create `~/.cursor/extensions/` if it does not exist.
2. If `local.just-file-1.0.0` already exists there, replace it with the copy from this repo.
3. Preserve the folder name exactly: `local.just-file-1.0.0`.

### Step 2 — Register the extension in `extensions.json`

Open `extensions.json` in the same extensions directory.

1. Parse it as a JSON **array**.
2. Remove any existing object whose `identifier.id` is `local.just-file` (idempotent reinstall).
3. Append the object below.
4. Set `location.path` to the **absolute** path of the copied folder (never keep `YOUR_USERNAME`).
5. Write valid JSON back (minified one-line array is fine).

Template (replace `location.path` only):

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

Path examples after substitution:

- macOS: `/Users/<username>/.cursor/extensions/local.just-file-1.0.0`
- Linux: `/home/<username>/.cursor/extensions/local.just-file-1.0.0`
- Windows: `C:\\Users\\<username>\\.cursor\\extensions\\local.just-file-1.0.0`

Do not change `identifier`, `uuid`, `relativeLocation`, or `metadata` fields.

### Step 3 — Verify

Confirm all of the following:

1. Folder exists at the absolute path used in `location.path`.
2. That folder contains `package.json` and `syntaxes/just.tmLanguage.json`.
3. `extensions.json` parses as JSON.
4. Exactly one entry has `"identifier":{"id":"local.just-file"}`.
5. That entry’s `location.path` matches the copied folder and contains no placeholder text.

### Step 4 — Ask the user to reload Cursor

Agents cannot reload the IDE. Tell the user to run:

Command Palette → `Developer: Reload Window`

- macOS: `Cmd+Shift+P`
- Windows / Linux: `Ctrl+Shift+P`

After reload, syntax highlighting applies to `Justfile` / `justfile` / `*.just`. Demo file in this repo: `demo/Justfile`.
