**macOS is currently not supported**. This should change in the future. Until then, this page provides an (unofficial) collection of information helping you to get Dino running. Problems are to be expected.

## Local Install

Install dependencies:
```
brew install adwaita-icon-theme glib glib-networking gpgme libgpg-error libgcrypt gtk+3 libgee libsoup sqlite cmake gettext ninja vala qrencode

# several of the libraries are misdetected by CMake on OS X
# but this just includes; so long as they are "brew link"ed in place
echo 'export CPATH="/usr/local/include:$CPATH"' >> ~/.bash_profile
echo 'export LDFLAGS="-L/usr/local/lib $LDFLAGS"' >> ~/.bash_profile

# gettext is "keg-only", so you need to do this to fully install it
brew link --force gettext
echo 'export PATH="/usr/local/opt/gettext/bin:$PATH"' >> ~/.bash_profile
echo 'export LDFLAGS="-L/usr/local/opt/gettext/lib"' >> ~/.bash_profile
echo 'export CPPFLAGS="-I/usr/local/opt/gettext/include"' >> ~/.bash_profile
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