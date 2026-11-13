# LabtopiaSnap

A free drag-box screenshot tool for KDE Plasma 6 on Wayland that works across several monitors, including with fractional scaling.

Press **Meta+Shift+S**. A frozen, dimmed copy of each monitor appears with a crosshair cursor. Drag a box anywhere, even across monitors, and release. Only the selected rectangle is copied to the clipboard as a PNG and saved to `~/Pictures/Screenshots/LabtopiaSnap_<time>.png`. Esc or right click cancels, and it closes itself after 90 seconds.

Free to use. See [LICENSE](LICENSE): not for redistribution or modification. Copyright Labtopia Farms.

## Download and install

1. Download `labtopiasnap-0.1.1.tar.gz` from the [latest release](../../releases/latest), and check it against `SHA256SUMS` (`sha256sum -c SHA256SUMS`).
2. Unpack it and run the installer:

```
tar xzf labtopiasnap-0.1.1.tar.gz
cd labtopiasnap-0.1.1
./install.sh
```

`./install.sh --dry-run` shows what it would do without changing anything. `./install.sh --no-shortcut` installs without binding a key. `./install.sh --uninstall` removes everything.

## Requirements

- KDE Plasma 6 on Wayland
- `spectacle` (it ships with Plasma), `wl-clipboard`, `notify-send`
- Python 3 with PySide6 (Fedora: `sudo dnf install python3-pyside6`)

## Why it exists

Spectacle 6.7.4's rectangular region mode mis-places the selector on multi-monitor setups with fractional scaling (KDE bugs 496241 and 500555), and general screenshot apps are restricted by KWin on Wayland. LabtopiaSnap captures the whole workspace once with Spectacle's background mode, which KWin allows, then draws its own selection overlay on every monitor.

Tested on Plasma 6.7.4 with 3 monitors at scale 1.65, including a selection across 2 monitors. Not tested on GNOME, wlroots desktops or X11, and it will not work there as it is.

## Known limits

- No annotation or crop after the drag.
- KDE Plasma on Wayland only.
- Cross-monitor dragging relies on Wayland's pointer grab. If a drag stops at a monitor edge on another setup, please report it.
