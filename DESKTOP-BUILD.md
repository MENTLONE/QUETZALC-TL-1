# Quetzalcōātl 1 — Windows desktop build

This branch packages the existing synthesizer UI as a Windows desktop application with Electron. The browser version on `main` remains unchanged.

## Build locally on Windows

1. Install Node.js 22 LTS from https://nodejs.org/.
2. Download or clone this repository and check out `desktop-soundwave`.
3. Open PowerShell in the project folder.
4. Run:

   ```powershell
   npm install
   npm start
   ```

5. To create the Windows installer, run:

   ```powershell
   npm run dist
   ```

The installer will be written to `dist/Quetzalcōātl-1-Setup-1.0.0-Windows-x64.exe` (the exact filename may use the unaccented product name).

## Automated installer

Pushing to `desktop-soundwave` triggers the **Build Windows installer** GitHub Actions workflow. When it completes, open the workflow run and download the `Quetzalcoatl-1-Windows-Installer` artifact.

## Notes

- The app loads `index.html` locally; normal use does not require a web server or an internet connection.
- Patch and performance setup persistence uses the browser storage API in the Electron app's local application profile. Export a JSON bank as a backup when moving between environments.
- The Electron window uses context isolation and disables Node integration in the page.
- Web MIDI device access and audio behavior must be tested on the target Windows machine before treating the build as release-ready.
- This initial installer is unsigned, so Windows SmartScreen may show an unknown-publisher warning.
