**macOS is currently not supported**. This should change in the future. Until then, this page provides an (unofficial) collection of information via [homebrew](https://brew.sh/) helping to get Dino running. Problems are to be expected.

## System-wide Installation 
Using homebrew formula by @denschub from [here](https://gist.github.com/denschub/2358c722d5d711022f99faac8f04c164):

```
brew tap denschub/dino https://gist.github.com/2358c722d5d711022f99faac8f04c164.git
brew install --HEAD dino
```

To use dino with support for OMEMO, HTTP-Upload, and OpenPGP you need to rename the plugin (PGP, OMEMO, ...) libraries in the `build/plugin` folder from .dylib to .so.

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