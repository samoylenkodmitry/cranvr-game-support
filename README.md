# cranvr game support

This repository publishes the Windows side of [cranvr](https://github.com/samoylenkodmitry), which plays Steam VR games on a Mac with a Meta Quest. The cranvr app downloads the release archive in its setup step, so a Mac needs no build tools.

The archive `cranvr-game-support-macos.tar.xz` holds:

- `engine/`: Wine 11.10 (Gcenx's macOS build) with DXMT's DLLs in place
- `dxmt/`: a DXMT v0.80 fork, which runs Direct3D 11 on Metal and shares each eye's picture with cranvr's host as an IOSurface
- `runtime/`: an OpenXR runtime from BasaltVR, its manifest, two checks and a shim for Steam's web helper
- `opencomposite/`: [OpenComposite](https://gitlab.com/znixian/OpenOVR), which runs OpenVR games on that runtime (`vrclient_x64.dll`), and `openvr_smoke.exe`, cranvr's OpenVR test program
- `SOURCE/opencomposite-source.tar.xz`: the source of that DLL (see Licenses)
- `LICENSES/` and `SOURCES.md`: the licenses and the sources of each part

The release names the SHA-256 of the archive in `cranvr-game-support-macos.tar.xz.sha256`. The cranvr app checks it before it unpacks the archive. The release holds the source of OpenComposite as a file of its own, `cranvr-opencomposite-source.tar.xz`.

## Requirements

- A Mac with Apple silicon and macOS 14 or later
- Rosetta 2: `softwareupdate --install-rosetta --agree-to-license`

## Licenses

OpenComposite is free software under the GNU GPL 3 (copyright of its authors, https://gitlab.com/znixian/OpenOVR). The archive carries its DLL as a separate program: a game loads it as its OpenVR runtime, and it calls the OpenXR runtime over the OpenXR interface. Its complete source is `cranvr-opencomposite-source.tar.xz` in each release and `SOURCE/opencomposite-source.tar.xz` in the archive: the commit `cff07db75c4823afe93ed7027b03d5f7bc86f164` of OpenOVR (branch `openxr`) with its libraries glm and the OpenXR SDK, cranvr's patches, the build script and the CMake toolchain file. The same commit is at https://gitlab.com/znixian/OpenOVR/-/tree/cff07db75c4823afe93ed7027b03d5f7bc86f164. The texts of the licenses of OpenComposite and of the parts that it contains (the OpenXR SDK loader, jsoncpp, glm, inih, Valve's OpenVR headers, debugbreak and the hand models of Oculus under CC BY 4.0) are in `LICENSES/`.

Wine is under the GNU LGPL 2.1 or later. The archive carries Wine 11.10 unchanged; its source is at https://gitlab.winehq.org/wine/wine/-/tags/wine-11.10. DXMT and BasaltVR are under the MIT license. The OpenXR SDK loader is under the Apache License 2.0. The texts are in `LICENSES/`.
