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

### Debian / Ubuntu
```
sudo apt install cmake valac libgee-0.8-dev libsqlite3-dev libgtk-3-dev libgpgme-dev libsoup2.4-dev libgcrypt20-dev libqrencode-dev libgspell-1-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libwebrtc-audio-processing-dev libsrtp2-dev libnice-dev glib-networking gstreamer1.0-plugins-good gstreamer1.0-gtk3
```

### Fedora
```
sudo dnf install cmake gcc-c++ gpgme-devel libnotify-devel libgcrypt-devel pkgconfig vala "pkgconfig(gee-0.8)" "pkgconfig(gio-2.0)" "pkgconfig(glib-2.0)" "pkgconfig(gthread-2.0)" "pkgconfig(gtk+-3.0)" "pkgconfig(libsoup-2.4)" "pkgconfig(sqlite3)" "pkgconfig(libqrencode)" "pkgconfig(gspell-1)" "pkgconfig(gstreamer-1.0)" "pkgconfig(gstreamer-app-1.0)" "pkgconfig(gstreamer-audio-1.0)" "pkgconfig(gstreamer-rtp-1.0)" "pkgconfig(gstreamer-video-1.0)" "pkgconfig(nice)" "pkgconfig(libsrtp2)" "pkgconfig(webrtc-audio-processing)"
```

### Arch Linux
```
sudo pacman -S cmake vala ninja glib2 glib-networking gtk3 gpgme libgee>=0.10 libgcrypt libsoup sqlite qrencode gspell gstreamer gst-plugins-base gst-plugins-good gst-plugin-gtk webrtc-audio-processing libnice libsrtp
```