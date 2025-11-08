# Resistor Color Code Calculator

A small interactive web tool to decode 4-band resistor color codes and calculate resistance and tolerance. This project is a single-file web app (`index.html`) that can be served locally.

## Features

- Welcome overlay with a short introduction.
- Visual resistor representation with 4 color bands.
- Color selectors for each band (1st digit, 2nd digit, multiplier, tolerance).
- Eye-catching popup that displays the calculated resistance and tolerance after all bands are selected.
- Configurable UI options via a `defaultConfig` object inside `index.html` (colors, fonts, sizes).

## Files

- `index.html` — Main application file (UI, styles, and JS).
- `README.md` — This file.

## Prerequisites

- Windows (instructions below are PowerShell-specific).
- Python 3 installed (optional if you prefer to use the OS default `python` command). A venv exists in this workspace and can be used.

> The workspace has a Python virtual environment. If you used the project helper earlier, the Python executable path is:

`C:/docs/Resistance calculator/.venv/Scripts/python.exe`

And the PowerShell activation script is:

`C:/docs/Resistance calculator/.venv/Scripts/Activate.ps1`

If you don't want to use the virtual environment, use your system Python.

## Run (Quick start)

Open PowerShell in the project folder (or use the integrated VS Code terminal). Recommended steps:

1) Activate the workspace venv (optional but recommended):

```powershell
& "C:/docs/Resistance calculator/.venv/Scripts/Activate.ps1"
```

2) Start a simple HTTP server on port 8000 (serves the current folder):

```powershell
# If venv is active, `python` will point to the venv interpreter
python -m http.server 8000

# Or use the explicit venv python without activating
"C:/docs/Resistance calculator/.venv/Scripts/python.exe" -m http.server 8000
```

3) Open the page in your browser (or VS Code Simple Browser):

- Browser: http://localhost:8000/index.html
- VS Code Simple Browser: open `http://localhost:8000/index.html`

To stop the server, press Ctrl+C in the terminal running it.

## How to use

1. When you open the page you'll first see the welcome overlay. Click the **Get Started** button to dismiss it.
2. Use the color selectors shown below the resistor visual to choose:
   - First Band (1st digit) — cannot be black (0) for the first digit.
   - Second Band (2nd digit)
   - Multiplier Band (x1, x10, x0.1, etc.)
   - Tolerance Band (brown, red, gold, silver)
3. After selecting all four bands the app will compute the resistance and show an eye-catching popup with the value and tolerance.
4. Close the popup with the × button and change selections to compute again.

## Customization

Open `index.html` and look for the `defaultConfig` object near the top of the script. You can change:

- `background_color` — page background
- `surface_color` — card background
- `text_color` — primary text color
- `primary_action_color` — color used for important UI elements
- `result_background_color` — background for results
- `font_family` and `font_size` — typography
- `title_text` and `instruction_text` — welcome/heading texts

If the project is loaded inside an editor SDK (the page wires `elementSdk`), some of these can be changed from the edit panel.

## Recent changes / Changelog

- Added a welcoming overlay that appears on first load.
- Reworked selectors so color buttons are dynamically generated and show selected state.
- Removed default resistor value (page no longer shows 1kΩ until all bands are selected).
- Added an eye-catching popup that appears after all bands are selected.
- Fixed template literal and config binding bugs.

## Troubleshooting

- If the page still shows a default resistance value on load: ensure you cleared the browser cache or reload the page after restarting the server.
- If the color selectors are empty: make sure the page finished loading and `DOMContentLoaded` fired (open DevTools -> Console to check for errors).
- Port 8000 already in use: choose a different port, e.g. `python -m http.server 9000` and open `http://localhost:9000/index.html`.
- Windows Defender or firewall blocking connections: allow `python.exe` or use a different port.

## Notes for developers

- The app is a single-file demo for convenience. If you plan to expand it, consider splitting JS/CSS into separate files and adding a small build process.
- Behavior is implemented in plain JavaScript and styled with scoped CSS inside `index.html`.

## License

This project is provided as-is for learning and small utility use. Add a license file if you want to publish or share it.

---

If you'd like, I can also:

- Add a short automated test (simple HTML/JS smoke test).
- Extract CSS/JS into separate files.
- Add a tiny Node.js dev server or a `Makefile`/`ps1` start script.

Tell me which of those you'd like next.