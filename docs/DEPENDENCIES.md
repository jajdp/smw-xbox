# Dependencies

*(Español: [DEPENDENCIES.es.md](DEPENDENCIES.es.md))*

## The game project

| | |
|---|---|
| Repository | [snesrev/smw](https://github.com/snesrev/smw) |
| Commit | **`eae20c6`** — what the patch was generated against |
| License | MIT (`LICENSE.txt`; GitHub does not detect it because of the file name) |

## Your own ROM

| | |
|---|---|
| File | `Super Mario World (USA).sfc` |
| Size | 524,288 bytes |
| SHA-256 | `0838e531fe22c077528febe14cb3ff7c492f1f5fa8de354192bdff7137c27f5b` |

Nothing about the ROM is distributed here. The hash is a fingerprint, so you can tell whether your
dump is the one this was built and tested with.

## Build tools

| | What is needed | Why |
|---|---|---|
| Visual Studio 2022 | With the **C++ UWP workload** and the **v143** toolset | Here MSBuild compiles, packages *and* signs. This is the one port family where that workload is a real requirement |
| SDL2 | **2.26.3, source**, vendored in `third_party\SDL2\` and retargeted to v143 | The desktop binaries cannot run in an AppContainer: no WinRT video backend, and imports that are not there |
| Windows SDK | 10.0.26100 or similar | Only if you re-package with your own tiles (`makeappx`, `signtool`) |
| Python 3 | Any 3.8+ | `tools/apply_uwp.py`, standard library only; and the project's own asset extraction |
| An Xbox Series | In **Developer Mode**, with a user signed in | Installing a package with nobody signed in looks like a broken package |

## The console

`Microsoft.VCLibs.140.00` for x64 is installed alongside the package as a dependency; it is not
bundled inside it. It comes with the Windows SDK.
