# libplist

*A small portable C library to handle Apple Property List files in binary, XML,
JSON, or OpenStep format.*

![](https://github.com/libimobiledevice/libplist/workflows/build/badge.svg)
![](https://github.com/libimobiledevice/libplist/workflows/CodeQL/badge.svg)

## Features

The project provides an interface to read and write plist files in binary,
XML, JSON, or OpenStep format alongside a command-line utility named `plistutil`.

Some key features are:

- **Formats:** Supports binary, XML, JSON, and OpenStep format
- **Utility:** Provides a `plistutil` utility for the command-line
- **Python:** Provides Cython based bindings for Python
- **Tested:** Uses fuzzing and data compliance tests
- **Efficient:** Lean library with performance and resources in mind

## Installation / Getting started

### Windows

First install ![MSYS2](https://www.msys2.org/).

Then open MSYS2 MINGW32 (or MSYS2 MINGW64 if your want to build for x64).

Install all required dependencies and build tools

```shell
# for x86
pacman -S mingw-w64-i686-toolchain 
pacman -S --needed base-devel msys2-devel
pacman -S git mingw-w64-i686-cython0 mingw-w64-i686-libzip
pacman -S make automake autoconf libtool pkgconf openssl openssl-devel
```

Then clone the actual project repository:
```shell
git clone https://github.com/liungkejin/libplist.git
cd libplist
```

Now you can build and install it:
```shell
./autogen.sh
make
make install
```

If you require a custom prefix or other option being passed to `./configure`
you can pass them directly to `./autogen.sh` like this:
```bash
./autogen.sh --prefix=/opt/local
make
make install
```

You can find the dll file in `%MSYS2 INSTALL PATH%\mingw32\bin`
If you want use this dll in Visual Studio C++ Project, you need use `pexports.exe`
to generate .lib file

```shell
pexports.exe -v libxxx.dll > libxxx.def
```

Then open `x86 Native Tools Command Prompt` or `x64 Native Tools Command Prompt`

run
```shell
lib /DEF:libxxx.def
```

Then you can use this libxxx.lib file in C++ project

```c++
#pragma comment(lib, "libxxx.lib")
```

### Debian / Ubuntu Linux

First install all required dependencies and build tools:
```shell
sudo apt-get install \
	build-essential \
	checkinstall \
	git \
	autoconf \
	automake \
	libtool-bin
```

If you want to optionally build the documentation or Python bindings use:
```shell
sudo apt-get install \
	doxygen \
	cython3
```

Then clone the actual project repository:
```shell
git clone https://github.com/libimobiledevice/libplist.git
cd libplist
```

Now you can build and install it:
```shell
./autogen.sh
make
sudo make install
```

## Usage

Then simply run:
```shell
plistutil -i foobar.plist -o output.plist
```
This converts the `foobar.plist` file to the opposite format, e.g. binary to
XML or vice versa, and outputs it to the `output.plist` file.

To convert to a specific format - and also to convert from JSON or OpenStep
format - use the `-f` command line switch:
```shell
plistutil -i input.plist -f json
```
This will convert input.plist, regardless of the input format, to JSON. The
code auto-detects the input format and parses it accordingly.

Please consult the usage information or manual page for a full documentation of
available command line options:
```shell
plistutil --help
man plistutil
```

## Contributing

We welcome contributions from anyone and are grateful for every pull request!

If you'd like to contribute, please fork the `master` branch, change, commit and
send a pull request for review. Once approved it can be merged into the main
code base.

If you plan to contribute larger changes or a major refactoring, please create a
ticket first to discuss the idea upfront to ensure less effort for everyone.

Please make sure your contribution adheres to:
* Try to follow the code style of the project
* Commit messages should describe the change well without being too short
* Try to split larger changes into individual commits of a common domain
* Use your real name and a valid email address for your commits

We are still working on the guidelines so bear with us!

## Links

* Homepage: https://libimobiledevice.org/
* Repository: https://git.libimobiledevice.org/libplist.git
* Repository (Mirror): https://github.com/libimobiledevice/libplist.git
* Issue Tracker: https://github.com/libimobiledevice/libplist/issues
* Mailing List: https://lists.libimobiledevice.org/mailman/listinfo/libimobiledevice-devel
* Twitter: https://twitter.com/libimobiledev

## License

This project is licensed under the [GNU Lesser General Public License v2.1](https://www.gnu.org/licenses/lgpl-2.1.en.html),
also included in the repository in the `COPYING` file.

## Credits

Apple, iPhone, iPad, iPod, iPod Touch, Apple TV, Apple Watch, Mac, iOS,
iPadOS, tvOS, watchOS, and macOS are trademarks of Apple Inc.

This project is an independent software library and has not been authorized,
sponsored, or otherwise approved by Apple Inc.

README Updated on: 2023-11-26
