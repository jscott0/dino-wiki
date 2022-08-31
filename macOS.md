**macOS is currently not officially supported**. This should change in the future. Until then, this page provides the information you need to get Dino running. Problems are to be expected.

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
   $ brew install adwaita-icon-theme glib glib-networking gpgme icu4c libgpg-error libgcrypt gtk+3 gtk4 libsignal-protocol-c libgee libsoup libsoup@2 sqlite cmake gettext ninja vala qrencode libxml2 gspell gst-plugins-base srtp libnice
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
   $ zsh -e -x -c 'for plugin in build/plugins/*.dylib;
         do mv ${plugin} ${plugin%.dylib}.so;
       done'
   ```

You are done. Start dino by typing `./build/dino`. If you want to update to the latest version, run `git pull` and redo steps 5 and 6.

TODO: Package dino in a bundle for nice installation.

## Developer notes
Guides to run virtualized macOS:
- VirtualBox: https://github.com/myspaghetti/macos-guest-virtualbox
- KVM/QEMU/libvirt: https://github.com/foxlet/macOS-Simple-KVM