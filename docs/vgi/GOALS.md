# VGI Kiosk Goals (Debian Trixie + Openbox)

## Primary intent
Use Openbox as a thin window manager for "appliance style" HMIs that read/control I/O.
Support rapid testing of multiple UI designs/apps on the same Pi image.

## Requirements
- Debian Trixie target
- Xorg + Openbox session
- Autologin kiosk user
- Launch a selected app on login (fullscreen by default)
- Multiple apps selectable without rebuilding the OS image
- Per-app Python venv support (dev-friendly; isolate dependencies per app)
- Clean logging (journald friendly)
- Safe maintenance escape hatch (SSH + optional hotkey)

## Proposed layout (runtime)
- Apps:            /opt/vgi/apps/<appname>/
- App venvs:       /opt/vgi/venvs/<appname>/
- App descriptors: /etc/vgi-kiosk/apps.d/<appname>.ini
- Default app:     /etc/vgi-kiosk/default-app

## Notes
- Keep upstream Openbox code as untouched as possible.
- Kiosk behavior should be driven by config + scripts first.
- Only patch Openbox when a real WM-level issue is proven (focus, stacking, input edge cases).
