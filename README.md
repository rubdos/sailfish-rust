# The Rust Programming Language

This is [Sailfish OS] source code repository for [Rust]. It contains the
compiler, standard library, and documentation.

[Sailfish OS]: https://sailfishos.org
[Rust]: https://www.rust-lang.org

## Quick Start

Read ["Installation"] from [The Book].

["Installation"]: https://doc.rust-lang.org/book/ch01-01-installation.html
[The Book]: https://doc.rust-lang.org/book/index.html

## Compiling using the Mer Platform SDK

Building the RPM requires the [Platform SDK] or [OBS].
These instructions are for building with the Platform SDK,
so make sure to have it installed.

1. Enter the platform SDK, make sure to have at least the x86 and armv7hl targets installed.
2. Install the RPM dependencies `sudo zypper install ccache cmake gcc gcc-c++ gdb libffi-devel llvm-devel make ncurses-devel 'pkgconfig(libcurl)' 'pkgconfig(liblzma)' 'pkgconfig(openssl)' 'pkgconfig(zlib)' python3-base`
3. Install the cross compilers `sudo zypper install cross-armv7hl-gcc cross-armv7hl-binutils cross-armv7hl-as cross-armv7hl-glibc cross-armv7hl-glibc-devel cross-armv7hl-glibc-headers  cross-armv7hl-kernel-headers  cross-aarch64-gcc cross-aarch64-binutils cross-aarch64-as cross-aarch64-glibc cross-aarch64-glibc-devel cross-aarch64-glibc-headers cross-aarch64-kernel-headers`
4. Link up the sysroots for the cross systems.
   Replace `latest` with the target version that you want to use:
   1. `ln -s /srv/mer/targets/SailfishOS-latest-armv7hl armv7hl-meego-linux-gnueabi/sys-root`
   2. `ln -s /srv/mer/targets/SailfishOS-latest-aarch64 aarch64-meego-linux-gnu/sys-root` (if you also want to build the `aarch64` Rust)
5. Copy the sources to the rpm system: `cp * ~/rpmbuild/SOURCES/`
6. `rpmbuild -bb rust.spec`
7. Grab yourself some ☕️

[Platform SDK]: https://sailfishos.org/wiki/Platform_SDK
[OBS]: https://wiki.merproject.org/wiki/Community_OBS
