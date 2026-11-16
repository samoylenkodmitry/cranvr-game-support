# cranvr game support

This repository publishes the Windows side of [cranvr](https://github.com/samoylenkodmitry), which plays Steam VR games on a Mac with a Meta Quest. The cranvr app downloads the release archive in its setup step, so a Mac needs no build tools.

The archive `cranvr-game-support-macos.tar.xz` holds:

- `engine/`: Wine 11.10 (Gcenx's macOS build) with DXMT's DLLs in place
- `dxmt/`: a DXMT v0.80 fork, which runs Direct3D 11 on Metal and shares each eye's picture with cranvr's host as an IOSurface
- `runtime/`: an OpenXR runtime from BasaltVR, its manifest, two checks and a shim for Steam's web helper
- `LICENSES/` and `SOURCES.md`: the licenses and the sources of each part

The release names the SHA-256 of the archive in `cranvr-game-support-macos.tar.xz.sha256`. The cranvr app checks it before it unpacks the archive.

## Requirements

- A Mac with Apple silicon and macOS 14 or later
- Rosetta 2: `softwareupdate --install-rosetta --agree-to-license`

## Licenses

Wine is under the GNU LGPL 2.1 or later. The archive carries Wine 11.10 unchanged; its source is at https://gitlab.winehq.org/wine/wine/-/tags/wine-11.10. DXMT and BasaltVR are under the MIT license. The OpenXR SDK loader is under the Apache License 2.0. The texts are in `LICENSES/`.
