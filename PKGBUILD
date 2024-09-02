# Maintainer:

pkgname=st-vcangel-git
_pkgname=st
pkgver=0.9.2.r1406.4c5603a
pkgrel=1
epoch=1
pkgdesc="Angel's simple (suckless) terminal with cool features and patches! "
url='https://github.com/VCAngel/st'
arch=('i686' 'x86_64')
license=('MIT')
options=('zipman')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
optdepends=('dmenu: feed urls to dmenu')
source=(git+https://github.com/VCAngel/st)
sha1sums=('SKIP')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

pkgver() {
  cd "${_pkgname}"
  printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
    "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd $srcdir/${_pkgname}
  # skip terminfo which conflicts with ncurses
  sed -i '/tic /d' Makefile
}

build() {
  cd "${_pkgname}"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "${_pkgname}"
  make PREFIX=/usr DESTDIR="${pkgdir}" install
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
  install -Dm644 Xdefaults "${pkgdir}/usr/share/doc/${pkgname}/Xdefaults.example"
}
