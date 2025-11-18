# minimalistic-VS-code

> A clean, minimal, and professional Visual Studio Code configuration bundle by BinaryOxide.

This repository contains everything needed to reproduce a clean, productivity-focused VS Code look and behaviour. It includes two ways to apply the setup: using the full exported **profile** (fast, less professional) or manually applying the **settings.json** and **keybindings.json** (recommended for control and portability).

---

## Repository structure

```
minimalistic-VS-code/

├── .vscode/                 # Optional workspace settings (if any)
├── Previews/                # UI screenshots showing the final look
│   ├── preview1.png
│   ├── preview2.png
│   └── preview3.png
├── Profile/                 # VS Code exported profile file
│   └── BinaryOxide-vscode-profile-v1.code-profile
├── extensions/              # extension exports & lists
│   ├── extensions-list.txt  # simple list of extension identifiers
│   └── extensions.json      # full metadata export (optional)
├── json/
│   └── settings.json        # core VS Code settings (recommended to review)
├── keybindings/
│   └── keybindings.json     # custom keybindings
└── README.md                # this file
```

---

![Alt text](Preview1.png)

## Two ways to apply this configuration

### Method A — Import the VS Code Profile (quick, not recommended for professionals)

**What it does:** imports settings, extensions, snippets, and keybindings in one click.

**Why it’s *not recommended* for professionals:**

* It imports **everything** (extensions and exact settings), which can bring unnecessary extensions or machine-specific settings that you may not want.
* Harder to audit: you can’t easily review every setting before applying.
* May overwrite local preferences and workspace-specific settings unintentionally.

**When to use it:** when you want a one-click look match (for demos, quick sharing with friends), not for production machines or long-term setups.

**How to use the profile:**

1. Open VS Code.
2. Open the **Account/Profile** menu (bottom-left or use the Command Palette).
3. Choose **Profiles → Manage Profiles → Import profile from file**.
4. Select `Profile/BinaryOxide-vscode-profile-v1.code-profile`.
5. Restart VS Code if required.

**Important keybindings included** (quick reference):

* `Alt + 1` — Toggle terminal
* `Alt + 2` — Toggle side panel (explorer)
* `Alt + 3` — Change title bar style

> ⚠️ Reminder: Using the profile will add any extensions listed inside it. Check `extensions/extensions-list.txt` before importing if you want to avoid installing all extensions.

---

### Method B — Manual configuration (recommended for professionals)

This method is the recommended, controlled way. It lets you review and selectively apply settings and keybindings.

**Steps — Minimal & safe**

1. Backup your current user settings and keybindings (always do this first):

   * Open Command Palette (`Ctrl+Shift+P`) → `Preferences: Open Settings (JSON)` → Save a copy.
   * Command Palette → `Preferences: Open Keyboard Shortcuts (JSON)` → Save a copy.

2. Apply settings.json

   * Open `json/settings.json` from this repo in VS Code.
   * Review the file and remove any entries you don’t want.
   * Copy the contents.
   * Open Command Palette → `Preferences: Open Settings (JSON)` and paste. Save.

   Alternatively, you can copy `json/settings.json` to your user folder manually:

   ```text
   Windows: C:\Users\<your-username>\AppData\Roaming\Code\User\settings.json
   ```

3. Apply keybindings.json

   * Open `keybindings/keybindings.json` and review the bindings.
   * Copy the contents.
   * Command Palette → `Preferences: Open Keyboard Shortcuts (JSON)` and paste. Save.

   Important keybindings (already configured in this repo):

   * `Alt + 1` — Toggle terminal
   * `Alt + 2` — Toggle side panel
   * `Alt + 3` — Change title bar style

4. Install extensions (selective)

   * Open `extensions/extensions-list.txt` to see the extension IDs included.
   * Recommended: install only the extensions you need. To install from the terminal:

   ```bash
   # Windows example (run in PowerShell or CMD where 'code' is in PATH)
   code --install-extension ms-python.python
   code --install-extension esbenp.prettier-vscode
   # or install all from the list:
   for /f %i in (extensions\extensions-list.txt) do code --install-extension %i
   ```

   * Or use the Extensions view in VS Code: open the three-dot menu → `Install from VSIX...` for local vsix files, or manually search and install by name.

5. Restart VS Code.

6. Verify the look with `Previews/preview1.png` and `preview2.png`.

---

## Why prefer manual configuration?

* **Control:** Only the settings and extensions you want are applied.
* **Security:** Avoid unknowingly installing extensions that require permissions.
* **Auditability:** You can review and version-control small JSON files easily.
* **Portability:** Easier to apply parts of the config across machines and teams.

---

## Troubleshooting & common notes

* **`code` command not found:** In VS Code Command Palette search `Shell Command: Install 'code' command in PATH` and run it.
* **CRLF / LF warnings:** Windows Git may warn `LF will be replaced by CRLF`. Acceptable — to control behavior use:

  ```bash
  git config --global core.autocrlf true
  ```
* **Conflicts when pushing to GitHub:** If Git rejects a push because the remote has changes, consider pulling with `--allow-unrelated-histories` or force-pushing if you intentionally want to overwrite the remote.
* **Keep your email private in commits:** Use GitHub no‑reply in `git config --global user.email "USERNAME@users.noreply.github.com"`.

---

## Contributing

* If you improve a setting or add a useful extension, please open a PR. Keep changes small and documented.
* When adding screenshots to `Previews/`, use 1280×720 or 1920×1080 for clear images.

---

## Changelog

* **v1.0** — Initial repo layout and baseline settings.




---

*Prepared professionally by BinaryOxide — keep configs minimal, auditable, and portable.*

