**macOS is currently not supported**. This should change in the future. Until then, this page provides an (unofficial) collection of information helping you to get Dino running. Problems are to be expected.

For virtualization of macOS purposes see [this](https://github.com/myspaghetti/macos-guest-virtualbox).

## Local Install

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