# Windows 11 Virtual

A Windows 11–style desktop that lives in **one HTML file**. No server, no build step, no external app pages — the shell and every app are rendered by `index.html`.

**Live:** https://chernuga.github.io/windows-11-virtual/

## What is in it

- Windows 11 24H2-style shell: left-aligned taskbar with a wide Search box, dark acrylic Start menu, hidden-icons chevron, network/sound/battery tray, Quick Settings, notifications + calendar, task view, desktop context menu, light/dark themes and accent colours.
- Uses the real Windows 11 Bloom wallpaper (bundled as WebP) and real Windows 11 app icons extracted from the local Windows install.
- Real window management: drag, resize, minimise, maximise, double-click title bar, snap to left/right/top, restore session after reload.
- **IndexedDB** storage for the virtual file system, wallpaper/theme settings, notifications, sticky notes and open-window state. Nothing is sent to a server.
- 17 built-in apps, all inline:
  - File Explorer (folders, upload, rename, delete, download, grid/list views)
  - Notepad (open/save files from the virtual FS)
  - Photos (image viewer with filmstrip and zoom)
  - Microsoft Edge (embeds sites that allow framing, with an open-in-new-tab fallback)
  - German Article Finder (Wiktionary API)
  - Minecraft-style parkour (Three.js r160 bundled inline)
  - Calculator
  - Settings (wallpaper, accent, theme, storage reset, about)
  - ChatADV shortcut
  - Clock, Task Manager, Sticky Notes, Terminal, Paint, Calendar, Tips, About
- Responsive layout for Android: compact Windows-sized controls, safe-area support, full-screen windows on narrow screens, floating small windows for Calculator / German / ChatADV.

The Start menu is laid out to match the Windows 11 24H2 dark theme: 640 × 720 px panel, six-column pinned grid, six recommended items, and a user/power footer.

The desktop runs on a **virtual 1920 × 1080 design canvas**. All shell/window sizes are design units, and at desktop widths the entire canvas is scaled uniformly to the display. Narrow/mobile screens switch to the fluid touch layout.

## Run it

Download `index.html` and open it, or serve the folder:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>. IndexedDB works from `http://` and `https://` origins (and in current Chrome from `file://`). On GitHub Pages it works out of the box.

## Notes

- Everything is local to the browser profile. Settings → Storage → Reset this PC clears it.
- The Browser app cannot bypass sites that send `X-Frame-Options` / CSP `frame-ancestors`; use **Open in a new tab** for those.
- The German app calls `de.wiktionary.org` directly and needs a network connection.
- Three.js r160 is bundled for the Minecraft Parkour app (MIT licence — see `THIRD-PARTY-NOTICES.md`).

## Deploy

The repository root is the GitHub Pages site. Push `index.html`, `.nojekyll` and this README; Pages serves the default branch.
