# VGI Kiosk Scaffold (Openbox + Debian Trixie)

This folder contains a config-driven kiosk launcher intended to run inside an Openbox session.

## What this provides
- `vgi-kiosk-launch`:
  - Reads `/etc/vgi-kiosk/default-app`
  - Loads `/etc/vgi-kiosk/apps.d/<app>.ini`
  - Launches the configured command (optionally inside a venv)
  - Logs to journald (stdout/stderr)
- `vgi-kiosk-select`:
  - Lists available apps
  - Sets default app
- A systemd **user** unit: `vgi-kiosk.service`
- Openbox `autostart` template
- Example app descriptor(s)

## Install overview (target Pi)
1) Copy scripts to `/usr/local/bin/`
2) Copy systemd user unit to `/etc/systemd/user/`
3) Create `/etc/vgi-kiosk/apps.d/` descriptors and `/etc/vgi-kiosk/default-app`
4) Enable the user service for the kiosk user
5) In Openbox autostart, start the user service (or call the launcher directly)

This scaffold intentionally avoids external dependencies (no PyYAML).
Descriptors are `.ini` files parsed with Python's standard library.
