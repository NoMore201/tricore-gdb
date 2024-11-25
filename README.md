# Tricore GDB package

This folder contains the tricore GDB PKGBUILD for building the sofware under
MSYS2 framework (more info: https://www.msys2.org).

Grab the latest release from [Release section](https://github.com/NoMore201/tricore-gdb/releases).

## Note on PKGBUILD

The PKGBUILD and patches 0001, 0002 and 0005 are based on the
[gdb package in MINGW-packages repository](https://github.com/msys2/MINGW-packages/tree/cfc3558eafad71aab2befd581d66c9e5375375cb/mingw-w64-gdb).

Patch 0006 was created by re-applying all changes found in
[this repo](https://github.com/Gigallith/gdb-tricore) to latest 11.2 release of binutils-gdb

## Prerequisites

Recommended [environment](https://www.msys2.org/docs/environments/) to use is UCRT64,
but also MINGW32 and MINGW64 environments should work (may not be tested though).

For information on how to prepare the environment for building packages,
refer to the [official documentation](https://www.msys2.org/dev/new-package/#building-the-package)

Makepkg tool is sensitive to line ending characters in source file. It requires
unix LF characters, while git on windows configured with `core.autocrlf` could
checkout files with windows CRLF line endings. To avoid this issue either
set `core.autocrlf` to `false` or use the tool `dos2unix.exe` available in
UCRT64 shell to convert the line ending to unix style:

    > dos2unix tricore-gdb/PKGBUILD
    > dos2unix tricore-gdb/*.patch

## Building

    > MINGW_ARCH=ucrt64 makepkg-mingw -Cs

`-C` tells makepkg to do a clean build, `-s` is used to automatically download build
dependencies.

If you want to ignore PGP signature verification of the original author of the
MSYS2 package, append the `--skippgpcheck` flag to the makepkg command

## License

PKGBUILD and patch files taken from MSYS2 are subject to
[MSYS2 License](https://www.msys2.org/license/). Original script and patch
from this repository are subject to BSD 3-Clause License. See
[LICENSE](./LICENSE) for more information
