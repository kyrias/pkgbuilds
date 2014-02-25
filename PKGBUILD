# Maintainer: Bill Kolokithas <kolokithas.b@gmail.com>

pkgname=j4-dmenu-desktop-git
pkgver=git
pkgrel=1
pkgdesc="A rewrite of i3-dmenu-desktop, which is much faster"
arch=('i686' 'x86_64')
url="https://github.com/enkore/j4-dmenu-desktop"
license=('GPL3')
depends=('dmenu')
makedepends=('git' 'cmake')
provides=('j4-dmenu-desktop')
conflicts=('j4-dmenu-desktop')
source=("$pkgname::git://github.com/enkore/j4-dmenu-desktop")
md5sums=('SKIP')

pkgver() {
	cd $pkgname
	echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
	cd $pkgname
	cmake -DCMAKE_INSTALL_PREFIX=/usr -DNO_TESTS=1 .
	make
}

package() {
	cd $pkgname
	make DESTDIR=$pkgdir/ install
}
