# Dependencies
* C compiler
* CMake
* Emoji font (recommend)
* gettext
* GLib (≥ 2.38)
* glib-networking
* GTK (≥ 3.22)
* GPGME (For the OpenPGP plugin)
* libgee-0.8 (≥ 0.10)
* libsignal-protocol-c (≥ 2.3.2, for the OMEMO plugin)
* libgcrypt (For the OMEMO plugin)
* libgspell
* libqrencode3 (For the OMEMO plugin)
* libsoup (For the HTTP files plugin)
* ninja(-build) (recommend)
* SQLite3 (≥ 3.24)
* valac (≥ 0.34)

## libsignal-protocol-c
If build complains about missing or incompatible libsignal-protocol-c and it is not provided by your distribution, you can fetch and build it in tree by using `./configure --with-libsignal-in-tree`.

## Package names
Information might be outdated or incomplete.

### Ubuntu
```
sudo apt install cmake valac libgee-0.8-dev libsqlite3-dev libgtk-3-dev libnotify-dev libgpgme-dev libsoup2.4-dev libgcrypt20-dev libqrencode-dev gettext libsignal-protocol-c-dev libgspell-1-dev
```

### Fedora
```
sudo dnf install cmake vala libgee-devel gtk3-devel libgcrypt-devel qrencode-devel gdk-pixbuf2-devel libsoup-devel gpgme-devel libsignal-protocol-c-devel gspell-devel
```

### Arch Linux
```
sudo pacman -S cmake vala libgee gtk3 libgcrypt qrencode gdk-pixbuf2 glib-networking libsoup gpgme libsignal-protocol-c gspell
```