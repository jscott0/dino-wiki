**macOS is currently not supported**. This should change in the future. Until then, this page provides an (unofficial) collection of information helping you to get Dino running. Problems are to be expected.

For virtualization of macOS purposes see [this](https://github.com/myspaghetti/macos-guest-virtualbox).

## Compiling with Homebrew
The following instructions expect you to use a Terminal emulator, for example the Terminal.app included with macOS. Open it and type in the commands as described.

1. If you don't have XCode tools installed, install them using
```sh
$ xcode-select --install
```
2. If you don't already have homebrew installed, install it using
```sh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
See https://brew.sh for updated installation instructions of homebrew.
3. Make sure all the required dependencies are installed by running
```sh
$ brew install adwaita-icon-theme glib glib-networking gpgme icu4c libgpg-error libgcrypt gtk+3 libsignal-protocol-c libgee libsoup sqlite cmake gettext ninja vala qrencode libxml2
```
4. Download the source code from the git in a directory of your choice (use `cd` to change the current working directory)
```sh
$ git clone https://github.com/dino/dino.git
$ cd dino
```
5. Configure and compile the dino in a brew shell
```sh
$ brew sh
$ ./configure
$ make
$ exit
```
6. Fix the filename of plugins
```sh
$ (cd build/plugins
   mv http-files.dylib http-files.so
   mv omemo.dylib omemo.so
   mv openpgp.dylib openpgp.so)
```

You are done. Start dino by typing `./build/dino`. If you want to update to the latest version, run `git pull` and redo steps 5 and 6.

TODO: Package dino in a bundle for nice installation.

## Old instructions (only for reference)

Install dependencies:
```
brew install adwaita-icon-theme glib glib-networking gpgme icu4c libgpg-error libgcrypt gtk+3 libsignal-protocol-c libgee libsoup sqlite cmake gettext ninja vala qrencode libxml2

# several of the libraries are misdetected by CMake on OS X
# but this just includes; so long as they are "brew link"ed in place
echo 'export CPATH="/usr/local/include:$CPATH"' >> ~/.bash_profile
echo 'export LDFLAGS="-L/usr/local/lib $LDFLAGS"' >> ~/.bash_profile

# gettext and icu4c are "keg-only", so you need to do this to fully install them
brew link --force gettext
echo 'export PATH="/usr/local/opt/gettext/bin:$PATH"' >> ~/.bash_profile
echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.bash_profile
echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.bash_profile
echo 'export LDFLAGS="-L/usr/local/opt/gettext/lib"' >> ~/.bash_profile
echo 'export LDFLAGS="-L/usr/local/opt/icu4c/lib"' >> ~/.bash_profile
echo 'export CPPFLAGS="-I/usr/local/opt/gettext/include"' >> ~/.bash_profile
echo 'export CPPFLAGS="-I/usr/local/opt/icu4c/include"' >> ~/.bash_profile
echo 'export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"' >> ~/.bash_profile
. ~/.bash_profile
```

Compile dino:
```
git clone https://github.com/dino/dino.git
cd dino
./configure
make
```

Rename the plugin (PGP, OMEMO, ...) libraries from .dylib to .so:
```
(cd build/plugins
mv http-files.dylib http-files.so
mv omemo.dylib omemo.so
mv openpgp.dylib openpgp.so)
```

Run dino:
```
./build/dino
```

Run `sudo make install` to do a systemwide installation.
