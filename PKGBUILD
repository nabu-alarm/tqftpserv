# AUR Maintainer: Jami Kettunen <jami.kettunen@protonmail.com>

_pkgname="tqftpserv"
pkgname="$_pkgname"
pkgdesc="Trivial File Transfer Protocol server over AF_QIPCRTR"
pkgver=r44.533779c
pkgrel=1
arch=("aarch64")
url="https://github.com/andersson/$_pkgname"
license=("BSD-3-Clause")
groups=("qcom-icnss-wlan")
depends=("qrtr")
makedepends=("git" "make" "gcc" "meson")
provides=("$_pkgname")
source=("git+https://github.com/andersson/$_pkgname.git")
md5sums=("SKIP")

pkgver() {
  cd "$_pkgname"

  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$_pkgname"

  meson setup build -Dprefix=/usr
}

package() {
  cd "$_pkgname"

  meson compile -C build
  meson install -C build --destdir "$pkgdir/"
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$_pkgname/COPYING
}
