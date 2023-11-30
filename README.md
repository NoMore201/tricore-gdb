# Tricore GDB package

This folder contains the tricore GDB PKGBUILD for building the sofware under
MSYS2 framework (more info: https://www.msys2.org).

The PKGBUILD and patches 0001, 0002 and 0005 are based on the
[gdb package in MINGW-packages repository](https://github.com/msys2/MINGW-packages/tree/cfc3558eafad71aab2befd581d66c9e5375375cb/mingw-w64-gdb).

Patch 0006 was created by re-applying all changes found in
[this repo](https://github.com/Gigallith/gdb-tricore) to latest 11.2 release of binutils-gdb

## Prerequisites

Recommended [environment](https://www.msys2.org/docs/environments/) to use is UCRT64,
but also MINGW32 and MINGW64 environments should work (may not be tested though).

For information on how to prepare the environment for building packages,
refer to the [official documentation](https://www.msys2.org/dev/new-package/#building-the-package)

## Building

```sh
$ MINGW_ARCH=ucrt64 makepkg-mingw -Cs
```

`-C` tells makepkg to do a clean build, `-s` is used to automatically download build
dependencies.

If you want to ignore PGP signature verification of the original author of the
MSYS2 package, append the `--skippgpcheck` flag to the makepkg command
