# Sources of cranvr's game support

- Wine 11.10: Gcenx's macOS build, https://github.com/Gcenx/macOS_Wine_builds/releases/tag/11.10 (LGPL 2.1 or later; source at https://gitlab.winehq.org/wine/wine/-/tags/wine-11.10). Unchanged, apart from DXMT's DLLs.
- DXMT v0.80 (MIT), https://github.com/3Shain/dxmt, with BasaltVR's patches 0001 to 0004 and cranvr's patches 0005 to 0008. Tree commit d6f5da2230511d6318ecd994e41614afa9416fcc.
- BasaltVR (MIT), https://github.com/Stooovie/BasaltVR at 6116e59124ef0f11ba157571b6f44f901eb6ba59, with cranvr's runtime patches.
- The OpenXR SDK loader in the runtime's checks (Apache 2.0).

cranvr's DXMT patches add a limit on MSAA samples, an MSAA resolve without a sample store and an
optional skip of the Mac window's present. cranvr's runtime patches add the headset's refresh rate,
a view size per game and an optional limit of one slice per swapchain.
