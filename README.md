# nperf-gui-appimage (Arch Linux PKGBUILD)

Arch Linux `PKGBUILD` that packages the official **nPerf** GUI network speed-test
client for Linux, distributed upstream as an AppImage
([nperf.com](https://www.nperf.com/)).

This is a continuation of the
[AUR `nperf-gui-appimage`](https://aur.archlinux.org/packages/nperf-gui-appimage)
package, kept up to date with newer nPerf releases. Full credit for the original
packaging goes to the maintainer listed in the `PKGBUILD` header; this repo only
tracks new upstream versions on top of that work.

## What it does

Downloads the upstream `nPerf-<version>-x86_64.AppImage`, installs it under
`/opt/appimages/`, adds a launcher script at `/usr/bin/nperf-gui`, and installs
the desktop entry for menu integration.

## Building & installing

```bash
git clone https://github.com/FoxKyong/aur-nperf-gui-appimage.git
cd aur-nperf-gui-appimage
makepkg -si
```

Requires `fuse` (fuse2) at runtime to run the AppImage.

## Updating to a new version

nPerf's Linux downloads live at `https://repo.nperf.com/linux/nperf/`. To bump:

1. Set `pkgver` to the new version (verify the AppImage exists at that URL first).
2. Regenerate the checksum: `makepkg -g` and paste the printed `md5sums=(...)`.
3. Regenerate metadata: `makepkg --printsrcinfo > .SRCINFO`.
4. Verify it builds: `makepkg -f`.

## License

nPerf is proprietary freeware (`license=GPL` in the PKGBUILD refers to the
packaging). This repository contains only the packaging recipe; the AppImage
itself is downloaded from nPerf's servers during the build.
