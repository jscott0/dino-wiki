# Dependency package names

### Debian / Ubuntu
```
sudo apt install cmake ninja-build valac gettext libgee-0.8-dev libsqlite3-dev libgtk-4-dev libadwaita-1-0 libgpgme-dev libsoup2.4-dev libgcrypt20-dev libqrencode-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libwebrtc-audio-processing-dev libsrtp2-dev libnice-dev glib-networking gstreamer1.0-plugins-good libsignal-protocol-c-dev
```

### Fedora
```
sudo dnf install cmake gcc-c++ gpgme-devel libnotify-devel libgcrypt-devel pkgconfig vala libsignal-protocol-c-devel "pkgconfig(gee-0.8)" "pkgconfig(gio-2.0)" "pkgconfig(glib-2.0)" "pkgconfig(gthread-2.0)" "pkgconfig(gtk+-3.0)" "pkgconfig(libsoup-2.4)" "pkgconfig(sqlite3)" "pkgconfig(libqrencode)" "pkgconfig(gstreamer-1.0)" "pkgconfig(gstreamer-app-1.0)" "pkgconfig(gstreamer-audio-1.0)" "pkgconfig(gstreamer-rtp-1.0)" "pkgconfig(gstreamer-video-1.0)" "pkgconfig(nice)" "pkgconfig(libsrtp2)" "pkgconfig(webrtc-audio-processing)"
```

### OpenSUSE Tumbleweed
```
sudo zypper install cmake gcc-c++ gpgme-devel libnotify-devel libgcrypt-devel pkgconfig vala "pkgconfig(gee-0.8)" "pkgconfig(gio-2.0)" "pkgconfig(glib-2.0)" "pkgconfig(gthread-2.0)" "pkgconfig(gtk+-3.0)" "pkgconfig(libsoup-2.4)" "pkgconfig(sqlite3)" "pkgconfig(libqrencode)" "pkgconfig(gstreamer-1.0)" "pkgconfig(gstreamer-app-1.0)" "pkgconfig(gstreamer-audio-1.0)" "pkgconfig(gstreamer-rtp-1.0)" "pkgconfig(gstreamer-video-1.0)" "pkgconfig(nice)" "pkgconfig(libsrtp2)" "pkgconfig(webrtc-audio-processing)" openssl-devel libsignal-protocol-c-devel
```

### Arch Linux
```
sudo pacman -S cmake vala ninja glib2 glib-networking gtk4 gpgme libgee>=0.10 libgcrypt libsoup sqlite qrencode gstreamer gst-plugins-base gst-plugins-good webrtc-audio-processing libnice libsrtp libsignal-protocol-c
```

# libsignal-protocol-c
If build complains about missing or incompatible libsignal-protocol-c and it is not provided by your distribution, you can fetch and build it in tree by using `./configure --with-libsignal-in-tree`.

# Dependencies

Basics
* C compiler
* CMake
* Emoji font (recommend)
* gettext
* GLib (≥ 2.38)
* GTK (≥ 4)
* libgee-0.8 (≥ 0.10)
* libqrencode3 (For the OMEMO plugin)
* ninja(-build) (recommend)
* SQLite3 (≥ 3.24)
* valac (≥ 0.34)

Encryption
* GPGME (For the OpenPGP plugin)
* libgcrypt (For the OMEMO plugin)
* libsignal-protocol-c (≥ 2.3.2, for the OMEMO plugin)
* libsrtp2 (For calls)

Connection establishment
* glib-networking
* libnice (≥ 0.1.15)
* libsoup (For the HTTP files plugin)

Audio/video processing
* GStreamer
* webrtc-audio-processing

***

### Basic instructions:
* `./configure`
* `make`
* `sudo make install`
* `sudo ldconfig`