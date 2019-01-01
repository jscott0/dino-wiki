**macOS is currently not supported**. This should change in the future. Until then, this page provides an (unofficial) collection of information via [homebrew](https://brew.sh/) helping to get Dino running. Problems are to be expected.

## system-wide installation 
Using homebrew formula by @denschub from [here](https://gist.github.com/denschub/2358c722d5d711022f99faac8f04c164):

```
brew tap denschub/dino https://gist.github.com/2358c722d5d711022f99faac8f04c164.git
brew install --HEAD dino
```

To use dino with support for OMEMO, HTTP-Upload, and OpenPGP you need to rename the plugin (PGP, OMEMO, ...) libraries in the `build/plugin` folder from .dylib to .so.

## local install

Install dependencies:
```
brew install adwaita-icon-theme glib glib-networking gpgme gtk+3 libgcrypt libgee libsoup sqlite cmake gettext ninja vala libqrencode3
```

Compile dino:
```
git clone https://github.com/dino/dino.git
cd dino
./configure
make
```
(Run `make install` with admin rights to do a systemwide installation).

Rename the plugin (PGP, OMEMO, ...) libraries from .dylib to .so:
```
cd build/plugins
mv http-files.dylib http-files.so
mv omemo.dylib omemo.so
mv openpgp.dylib openpgp.so
```

Run dino:
```
cd folder/where/dino/is/located
build/dino
```