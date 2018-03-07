**macOS is currently not supported**. This should change in the future. Until then, this page provides an (incomplete, unofficial) collection of information helping to get Dino running. Problems are to be expected.

- Rename the plugin (PGP, OMEMO, ...) libraries from .dylib to .so

Homebrew formula (by @denshub from [here](https://gist.github.com/denschub/2358c722d5d711022f99faac8f04c164)):
```rb
class Dino < Formula
  desc "Modern Jabber/XMPP Client using GTK+/Vala "
  homepage "https://dino.im"

  ## TODO: This is not really a version, but a dummy that's not going to work.
  # url "https://github.com/dino/dino/archive/0.0.tar.gz"
  # sha256 "a951b50559671ab30e74304ddc66c943405c8ad1bcbe4d77bef647a081fd0dbb"

  head do
    url "https://github.com/dino/dino.git"
  end

  depends_on "adwaita-icon-theme"
  depends_on "glib"
  depends_on "glib-networking"
  depends_on "gpgme"
  depends_on "gtk+3"
  depends_on "libgcrypt"
  depends_on "libgee"
  depends_on "libsoup"
  depends_on "sqlite"

  depends_on "cmake" => :build
  depends_on "gettext" => :build
  depends_on "ninja" => :build
  depends_on "vala" => :build

  def install
    mkdir "build" do
      system "cmake", "..", *std_cmake_args

      # We have to build with `-j1` or the build might fail. Currently,
      # dependencies in the upstream project seem to be built out of order,
      # so we can run into build failures...
      system "make", "install", "-j1"
    end
  end

  test do
    system "#{bin}/dino", "-h"
  end
end
```