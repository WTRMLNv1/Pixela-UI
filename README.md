# Pixela-UI

A small, friendly desktop GUI for interacting with Pixela (https://pixe.la).

This app provides a simple Tkinter interface to create a Pixela user, create graphs, add pixels, open the graph in your browser, and manage UI themes and keyboard shortcuts.

## Features
- Create a Pixela user and graph
- Add pixels (supporting int/float depending on graph configuration)
- Open your graph in the default browser
- Theme support (predefined themes in `themes.json`, plus create new themes in-app)
- Keyboard shortcuts (defined in `keyBinds.json`)
- Stores minimal credentials/settings in `creds.json` (keeps app state between runs)

## Requirements
- Python 3.7 or newer
- The `requests` package (used to call the Pixela API)
- `tkinter` (usually bundled with standard Python installers)

Install the required Python package:

```powershell
pip install requests
```

## Quick start

1. Clone or download this repository and open a terminal in the project folder.
2. Install dependencies: `pip install requests`.
3. Run the app:

```powershell
python .\main.py
```

When the app first opens it will prompt you to create a Pixela user if `creds.json` does not contain a username.

## Configuration

Credentials and a few preferences are stored in `creds.json` in the project root. Keep your token secret — don’t commit it to public repos.

Example `creds.json` (create this file if it doesn't exist):

```json
{
   "username": "your_username",
   "tokenID": "your_secret_token",
   "graphID": "your_graph_id",
   "quantity": null,
   "quantityType": null
}
```

Keybinds are stored in `keyBinds.json`. The default mapping is:

```json
{
   "open_pixel": "Control-p",
   "create_graph": "Control-g",
   "create_user": "Control-u",
   "change_theme": "Control-t",
   "go_home": "Control-h"
}
```

Themes are kept in `themes.json`. The app saves the last used theme to `lastUsed_theme.json`.

## Usage overview

- Create a user: either via the UI or by setting `creds.json` manually and using the Create User flow.
- Create a graph: pick name, id, unit, type (int/float), timezone and a color.
- Add pixels: select a date (DD-MM-YYYY) and a quantity and submit.
- Open chart: the app will open your graph page in the browser.
- Themes: choose or create a theme with the built-in color picker.
- View shortcuts: open the list of keyboard shortcuts from the UI.

## Important files
- `main.py` — program entrypoint.
- `UI.py` — Tkinter UI logic and screens.
- `core.py` — functions that call the Pixela API (create user, create graph, add pixel).
- `helpers.py` — small UI helpers and JSON helpers.
- `getCreds.py` — helper that reads `creds.json`.
- `getThemes.py` — theme loading and listing utilities.
- `getKeyBinds.py` — keybinds loader and binder.
- `ChartViewer.py` — opens your graph URL in the default browser.
- `themes.json`, `keyBinds.json`, `lastUsed_theme.json` — configuration/state files.

## Troubleshooting
- Missing tkinter: On Windows use the standard Python installer which includes tkinter. On some Linux distros you may need to install `python3-tk`.
- HTTP errors when calling Pixela: ensure your token and username are correct, and that you have an active network connection.
- Invalid date format when adding pixels: use DD-MM-YYYY (app will validate and show an error message).

## Security notes
- `creds.json` stores your Pixela token. Treat it like a secret. Add `creds.json` to `.gitignore` before committing if you plan to put the repo in version control.

## Contributing & next steps
- Add unit tests for API wrappers in `core.py`.
- Consider packaging (`pyinstaller`) for an executable build.
- Add screenshot(s) and a LICENSE file if you want to share the project publicly.

## License
This project is provided under the MIT license — feel free to reuse and modify.

---

Made with ❤️ by WTRMLN
