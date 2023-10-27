# Tricore GDB package

This folder contains the tricore GDB PKGBUILD for building the sofware under
MSYS2 framework (more info: https://www.msys2.org).

The PKGBUILD and patches 0001, 0002 and 0005 are based on the [gdb package in MINGW-packages repository](https://github.com/msys2/MINGW-packages/tree/cfc3558eafad71aab2befd581d66c9e5375375cb/mingw-w64-gdb).

Patch 0006 was created by re-applying all changes found in [this repo](https://github.com/Gigallith/gdb-tricore)
to latest 11.2 release of binutils-gdb

## Prerequisites

To build this package, following things are needed:

- Working MSYS2 setup with "base-devel" packages installed
- Package `${MINGW_PACKAGE_PREFIX}-toolchain` installed

## Building

Recommended environment to use is UCRT64, but also MINGW32 and
MING64 environments should work (not tested though). Open up a UCRT64 shell,
cd to this directory and issue the following command

```sh
$ MINGW_ARCH=ucrt64 makepkg-mingw -Cs --skippgpcheck --nocheck
```